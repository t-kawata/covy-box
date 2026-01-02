# OpenAudio env
```
cd /usr/local
git clone https://github.com/fishaudio/fish-speech.git
cd fish-speech
cat <<EOF > .env
BACKEND=cuda             # または cpu
COMPILE=1                # コンパイル最適化を有効化
GRADIO_PORT=7861         # WebUIのポート
API_PORT=8081            # APIサーバーのポート
UV_VERSION=0.8.15        # UVパッケージマネージャーのバージョン
EOF
chown -R 1000:1000 ./references
chown -R 1000:1000 ./checkpoints

hf auth login --token hf_???????????????????????????????????
hf download fishaudio/openaudio-s1-mini --local-dir checkpoints/openaudio-s1-mini

# CUDAでWebUIを起動
docker compose --profile webui up

# APIサーバーを起動
docker compose --profile server up
```
