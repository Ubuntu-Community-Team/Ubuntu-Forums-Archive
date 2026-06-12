---
title: "Clock Screensaver"
date: 2013-04-25
forum: Desktop Environments
---

### Post by ibjsb4 on 2013-04-25
Looking for a screensaver thats an analog clock that will fill the entire monitor so it can be seen from anywhere in the room.  Shouldn't make a difference, but its going on an Xubuntu 12o4 box that currently has no screensaver setup.  Thanks

---

### Post by ibjsb4 on 2013-04-28
bump

---

### Post by stinkeye on 2013-04-28
This was done in 13.04 but should also work in 12.04 and 12.10

I successfully compiled xscreensaver with a patch to include an analogue clock fom this page...
_[http://www.d8.dion.ne.jp/~pt2k/software/xscreensaver-clock/index_e.html](http://www.d8.dion.ne.jp/~pt2k/software/xscreensaver-clock/index_e.html)_

Installed packages for building...
```
sudo apt-get install build-essential gcc libgtk2.0-dev checkinstall
```

Downloaded the latest xscreensaver source code.
Direct link ----> _[http://www.jwz.org/xscreensaver/xscreensaver-5.21.tar.gz](http://www.jwz.org/xscreensaver/xscreensaver-5.21.tar.gz)_

Dowloaded the clock patch... xs-clock-patch-1.0.0-for-xscreensaver-**5.15**.diff.gz from 
_[http://www.d8.dion.ne.jp/~pt2k/software/xscreensaver-clock/index_e.html](http://www.d8.dion.ne.jp/~pt2k/software/xscreensaver-clock/index_e.html)_


Placed both downloads in the created directory **~/src**

Then followed the directions on the above page for installing in Ubuntu 12.04 with a couple of [COLOR="#FF0000"]changes[/COLOR] for the directory I used to compile in, the source version and used **checkinstall** instead of **make install**.
eg
```
sudo apt-get remove gnome-screensaver
sudo apt-get install libglade2-dev libxt-dev
[COLOR="#FF0000"]cd ~/src[/COLOR]
tar xzf xscreensaver-5.2[COLOR="#FF0000"]1[/COLOR].tar.gz
cd xscreensaver-5.2[COLOR="#FF0000"]1[/COLOR]
zcat ../xs-clock-patch-1.0.0-for-xscreensaver-5.15.diff.gz | patch -p1
./configure --prefix=/usr
make
sudo [COLOR="#FF0000"]checkinstall[/COLOR]
sudo ln -s /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```

In the unity dash enter **screensaver** or in terminal run **xscreensaver-demo** to configure.
By default the clock wanders, but you can fix the clock in the settings button.

In startup applications, for the Screensaver entry, replace the command **gnome-screensaver** with **xscreensaver -nosplash**

---

### Post by ibjsb4 on 2013-04-28
Thanks stinkeye.

I had no idea it was going to be this complex.  Ill try it in a vm later.  I wonder if this can be transfered to a thumb drive after the build.  Be nice just to be able to go to this persons house and download it and be on my way.

---

### Post by stinkeye on 2013-04-28
> **ibjsb4 said:**
> Thanks stinkeye.

I had no idea it was going to be this complex.  Ill try it in a vm later.  I wonder if this can be transfered to a thumb drive after the build.  Be nice just to be able to go to this persons house and download it and be on my way.
The checkinstall command creates a deb file in the  ~/src/xscreensaver-5.21 directory.
eg I have **/home/glen/src/xscreensaver-5.21/xscreensaver_5.21-1_amd64.deb** after installation.
So I imagine you could use that deb to install on the same release and architecture.

The deb I created in 13.04 also works in my 12.10 install. Used gdebi to install and it just gave a warning about a different version in the repos.
I know very little about this sort of stuff though.
It surprised me when adding the patch and building, it actually worked let alone using that deb to install in 12.10 :o

---

