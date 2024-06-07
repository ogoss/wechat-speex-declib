#### 安装 speex

```
cd /usr/local/src
wget http://downloads.us.xiph.org/releases/speex/speex-1.2.0.tar.gz
tar xzvf speex-1.2.0.tar.gz
cd speex-1.2.0
./configure --enable-static --prefix=/usr/local
make
sudo make install
```

#### 安装 X264
```
cd /usr/local/src
git clone --depth 1 http://git.videolan.org/git/x264.git
cd x264
./configure --enable-static --prefix=/usr/local
make
sudo make install
```
设置PKG_CONFIG_PATH,确保 pkg-config 能够找到 x264 库：
```
export PKG_CONFIG_PATH="/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH"
```


#### 安装 libmp3
```
cd /usr/local/src
git clone --depth 1 https://github.com/lame-project/lame.git
cd lame
./configure --enable-static --prefix=/usr/local
make
sudo make install
```


#### 安装ffmpeg
```
cd /usr/local/src
git clone --depth 1 https://git.ffmpeg.org/ffmpeg.git ffmpeg
cd ffmpeg
PKG_CONFIG_PATH="/usr/local/lib/pkgconfig" ./configure --enable-gpl --enable-nonfree --enable-libmp3lame --enable-libx264 --enable-libspeex
make
sudo make install
```


#### 安装 wechat-speex-declib
```
git clone --depth 1 https://github.com/ogoss/wechat-speex-declib.git
cd wechat-speex-declib && make && cp ./bin/speex_decode /usr/local/bin/speex2wav
speex2wav test.speex test.wav
```
