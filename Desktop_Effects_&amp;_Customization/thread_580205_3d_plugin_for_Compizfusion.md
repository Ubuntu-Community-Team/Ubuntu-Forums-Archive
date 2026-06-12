---
title: "3d plugin for Compiz/fusion"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by masai489 on 2007-10-18
Hello out  there. I'm new to configuring this great effect for Ubuntu but I'm trying to load the 3d effect and so far I have a tar file. I've tried to run make and get this...

iam@Section-1:~/Desktop/3d$ make
[: 1: ==: unexpected operator
-e compiling : 3d.c -> build/lib3d.loPackage x11 was not found in the pkg-config search path.
Perhaps you should add the directory containing `x11.pc'
to the PKG_CONFIG_PATH environment variable
No package 'x11' found
Package compiz was not found in the pkg-config search path.
Perhaps you should add the directory containing `compiz.pc'
to the PKG_CONFIG_PATH environment variable
No package 'compiz' found
/bin/sh: libtool: not found
make: *** [build/lib3d.lo] Error 127

I'm kind of unsure, is the error due to where I extracted the file and if so...what is the suggested extraction point so when I run the make file it'll be happy? I've searched for this and have come across so much helpful info but nothing really that I can find that'll help. I appreciate any advice. :guitar:

---

### Post by Vorian on 2007-10-18
You need to install build the dependencies for 3d to work properly.

---

### Post by masai489 on 2007-10-18
Ok, can you please tell me how that's done or direct me to a link expressing how this  is done? Thanks.

---

### Post by Amaranth on 2007-10-18
The 3d plugin is not compatible with the version of compiz we have in gutsy.

---

### Post by masai489 on 2007-10-18
Amaranth, thanks for the info on that. Is there any effect we can get or will this be a feature available soon? Thanks again for saving me the time.

---

### Post by Seti on 2007-10-21
"The 3d plugin is not compatible with the version of compiz we have in gutsy."

Bummer!

---

### Post by ArielTM on 2007-10-22
Hi
The current snapshot of the 3d plugin doesn't work with the cf version in gutsy
but old snapshots are

try my script
[http://ubuntuforums.org/showthread.php?t=585491](http://ubuntuforums.org/showthread.php?t=585491)

---

### Post by cedenburn on 2007-11-02
This works great Thanks

---

### Post by nikoPSK on 2007-11-02
thats too bad... well you have any idea when a compiz fusion 0.6.0. will be released?:popcorn:

---

### Post by nickweedon on 2008-01-10
It is still possible to run the 3d plugin with the gusty version of compiz-fusion. To do so however, you will need to download the last snapshot of the 3d plugin source before work was started upon migrating the plugin to the new compiz core (as after that point, it will no longer compile under gusty). To build the 3D plugin under gusty (using the standard gusty repository version of compiz-fusion) you must perform the following steps:

- cd /usr/local/src
- mkdir compiz
- cd compiz
- Download the version of the 3D plugin that will work with gusty's compiz-fusion by visiting "http://gitweb.compiz-fusion.org/?p=fusion/plugins/3d;a=shortlog" and download the source code snapshot taken on 2007-08-29 ("Initialize variable"). After doing so, move it to /usr/local/src and rename it to 3dplugin.tar.gz
- tar -xzvf 3dplugin.tar.gz
- sudo apt-get install compiz-bcop compiz-dev git git-core
- cd 3d
- make
- make install

restart compiz (compiz --replace &) and then you should see that the 3D plugin is now available.

---

