---
title: "Broken Fluxbox"
date: 2011-03-29
forum: Desktop Environments
---

### Post by mlerota on 2011-03-29
Latest version of Fluxbox 1.1.1 is broken. It works but focusing windows and capture of a keyboard doesn't work right. (when you are coming from another workspace) It's frustrating when you want to type something but window or terminal doesn't capture your first input. I installed the new version from source and there is no problem. For all of you that like fluxbox you can do it like this. 

First become root and remove your old fluxbox 
apt-get remove fluxbox

Download new 1.3.1 version from source in /usr/local/src

cd /usr/local/src
tar xzvf fluxbox-1.3.1.tar.gz

cd fluxbox-1.3.1

Maybe you miss some libs
apt-get install libimlib2-dev libxpm-dev libxft-dev libxrender-dev
./configure  --enable-xpm --enable-imlib2 --enable-xft --enable-xrender

make 
make install

I don't know why you need this:

ln -s /usr/local/bin/fluxbox /usr/bin/fluxbox

But it doesn't work without this soft link. 

Then in your gdm setup directory create this file: 
/usr/share/xsessions/fbox.desktop

And put this: 

[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox 1.3.1
Comment=This session logs you into FBox
Terminal=false
Exec=/usr/local/bin/startfluxbox
# no icon yet, only the top three are currently used
Icon=
Type=Application

[X-Window Manager]
SessionManaged=true

That's it.

---

