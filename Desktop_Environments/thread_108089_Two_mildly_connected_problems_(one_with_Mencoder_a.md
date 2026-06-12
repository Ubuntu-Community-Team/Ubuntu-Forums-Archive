---
title: "Two mildly connected problems (one with Mencoder and the other with an installation)"
date: 2005-12-25
forum: Desktop Environments
---

### Post by tmckellar on 2005-12-25
Currently I've got two mildly connected problems in Breezy.

To start I'm having a problem with Mencoder. I've been getting into stop motion animation lately. I'm really wanting to get into it a bit more seriously. I'm using a program actually called Stopmotion to sequence all my photos which is downloadable from the Ubuntu repositories. [http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/](http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/) The problem I'm having is with the video export option using Mencoder. I have Mencoder k6 and k7 installed. Here is the options it has for the Mencoder codec.

mencoder mf://$IMAGEPATH/*.jpg -mf w=1600:h=1200:fps=20:type=jpg -ovc lavc -lavcopts vcodec=mpeg1video -oac copy -o $VIDEOFILE

If anybody can give me some help or insight to why it might not be working or how to get another encoder (eg. ffmpeg) working it would be greatly appreciated.


Now onto problem number two. At the moment I can't use any form of Apt because of a installation problem I'm having with a piece of software named Myrtille. [http://lamenagerie.com/boite/soft/myrtille/](http://lamenagerie.com/boite/soft/myrtille/) It is another program designed to edit and create stop motion animations. It gave me an error when it first installed but I can't remember precisely what it is. Here is the errors I get when I try to reinstall the package.

(Reading database ... 285717 files and directories currently installed.)
Preparing to replace myrtille 0.3k (using .../Desktop/myrtille_0.3k_all.deb) ...Unpacking replacement myrtille ...
/var/lib/dpkg/info/myrtille.postrm: line 3: /usr/bin/update-menus: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /usr/bin/update-menus: No such file or directory
dpkg: error processing /home/tmckellar/Desktop/myrtille_0.3k_all.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /usr/bin/update-menus: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /home/tmckellar/Desktop/myrtille_0.3k_all.deb

Here is the error I get when I try to remove the Myrtille package.

tmckellar@ubuntu:~$ sudo dpkg -r myrtille dpkg: error processing myrtille (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 myrtille

Basically I can't get anything from the repositories unstil I can get this package removed. I've tried using the force remove options with dpkg but absolutely nothing has worked so far. Once again I really appreciate any help anyone can give me. Thanks.

Tye

---

### Post by bjoernen on 2006-01-13
Mencoder is kind of tricky to use in some circumstances. On the other side it is nice when it works :-) To those of you having trouble with video export in stopmotion, I suggest you to try the following command (inside stopmotion):

mencoder -ovc lavc -lavcopts vcodec=msmpeg4v2:vpass=1:$opt -mf type=jpg:fps=8 -o $VIDEOFILE mf://$IMAGEPATH/*.jpg

This is a default option in the latest release (0.3.3) which is available on ubuntu soon. Go to the projects website and grab the latest release if you can't wait for it :-) [http://stopmotion.bjoernen.com](http://stopmotion.bjoernen.com)

---

### Post by bjoernen on 2006-01-13
Another option, using ffmpeg:

ffmpeg -r 10 -b 1800 -i $IMAGEPATH/%06d.jpg $VIDEOFILE

---

### Post by mangasurfer on 2006-08-20
hi to get ride of myrtille. frist you need to install the menu package

menu_2.1.24_i386.deb

then myrtille will install and package manager will be functional again.

hope this helps

---

