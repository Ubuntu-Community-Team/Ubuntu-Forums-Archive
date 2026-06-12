---
title: "Help Please 2 Unreal questions"
date: 2005-04-25
forum: Gaming &amp; Leisure
---

### Post by KezzerDrix on 2005-04-25
Hello,

1. I have installed Ut2k4 and am trying to do the patch on it.  How do I set up the unreal folder to give me permission to write to it?  /usr/local/games/UT2004

2. I have no sound, I have sound with everything but unreal 2k4 help please

---

### Post by jdodson on 2005-04-25
[QUOTE=KezzerDrix]Hello,

1. I have installed Ut2k4 and am trying to do the patch on it.  How do I set up the unreal folder to give me permission to write to it?  /usr/local/games/UT2004

2. I have no sound, I have sound with everything but unreal 2k4 help please[/QUOTE]

copy the files over as root or sudo.

---

### Post by KezzerDrix on 2005-04-25
Hello,

I want to give the folder write permissions.  For maps, addons, etc.  But I can't seem to log on as a root user.  I tried root and unbuntu, does this distro not really have a root user?  If not what is the command in a terminal to give that folder write permissions?


Thanks

---

### Post by woifi on 2005-04-25
1) ubuntuguide.org > If you are tired of typing "sudo" all the time, switch to root user by issuing "sudo -s -H" followed by user password

2) chown and chgrp are your friends

3) try to kill esd (by killall esd) - think you have sound then (I have this problem with ut99) ; I'm working for an more elegant solution...

hth

woifi

---

### Post by sc3252 on 2005-04-27
i hate to give you a bad way of fixing your problem but it is most likly the easy way, couldnt you do this.
"sudo nautilus --no-desktop --browser" and navigate to /usr/local/games/ and right click on the ut2004 folder and change permissions from root to usr or your name, also make sure that all the sub folders and files are under your permissions.

---

