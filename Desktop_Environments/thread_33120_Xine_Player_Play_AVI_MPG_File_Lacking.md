---
title: "Xine Player Play AVI/ MPG File Lacking"
date: 2005-05-09
forum: Desktop Environments
---

### Post by yccheok on 2005-05-09
Hi,

I am using Ubuntu Warty. I am facing a problem which my xine player play AVI movie or MPG movie lacking. Tat's mean after a few frames it played, it will stop for a seconds, then played, then continue...... :( At the end of the day, I will get an error message. 

**ur system seems too busy, the amoung of dropped frames is too high.**

Please note that, during the time i play video, no other resource hungry applications is running. I am using pentium 2.4GHZ with 512 RAM.

I had install the following packages

[CENTER]gstreamer0.8-plugins - 0.8.5-1ubuntu3 (warty)
w32codecs - 1:20050412-0.0 (stable)
xine-ui - 0.99.1-1 (warty)[/CENTER]

I first guess maybe is my xine-ui problem. I want to give a try on mplayer but it seem i have problem install it through synaptic with my current sources.list file.

Any suggestions? Am I missing any packages, or I get them from wrong repositories, or I should use mplayer......


Here are the sources.list file which I am using:

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports main universe

---

### Post by defkewl on 2005-05-09
I suggest you using some other media player like vlc. It worked for me :)

---

### Post by gil-galad on 2005-05-09
Have you tried totem-xine?

---

### Post by yccheok on 2005-05-13
i try the steps in [http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt) to install Mplayer. Sounds cool! I able to rebuild Mplayer with additional codec embedded into it. Now that solve my AVI MPG file lacking problem.

---

