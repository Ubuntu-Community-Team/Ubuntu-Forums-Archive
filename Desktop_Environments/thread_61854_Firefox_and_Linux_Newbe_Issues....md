---
title: "Firefox and Linux Newbe Issues..."
date: 2005-09-02
forum: Desktop Environments
---

### Post by mark2 on 2005-09-02
Firefox says... Fatal Error [-618]: Couldn't open xpistub library.

That and I was wondering if someone could tell me how to get gnome how to mount NTFS drives?

Also, i cant do the sudo apt-get thingy to install KDE... it says its missing or something random like that.

Specs:

P4 1.7Ghz
512MB Ram
(for ubuntu) 2.5Gb hdd (yea i know its tiny)
40GB hdd for XP
SiS 650 Chipset/Video (YEA i know... stupid crappy intergrated video)

---

### Post by KingBahamut on 2005-09-02
I hit your post in tips and tricks with the below bit. 

> For kde

apt-get install kubuntu-desktop

Mounting NTFS drives
add the below line to fstab in /etc

where hd1 equals the parition your mounting
and /media/windows is your mount point.
/dev/hdx1 /media/windows ntfs nls=utf8,umask=0222 0 0

---

### Post by mark2 on 2005-09-02
[QUOTE=KingBahamut]I hit your post in tips and tricks with the below bit.[/QUOTE]

Ok thanks (I think havent tried it yet. hehe)

Also, does anyone have any clues as to how to get the back & forward buttons on a MS IntelliMouse Explorer to work?

---

### Post by mark2 on 2005-09-02
[QUOTE=mark2]Ok thanks (I think havent tried it yet. hehe)

Also, does anyone have any clues as to how to get the back & forward buttons on a MS IntelliMouse Explorer to work?[/QUOTE]
 Ummm, looking at the fstab thingy, i'm a tad confused/not-getting where i edit/add the windows partition bit in.

---

### Post by EnderTheThird on 2005-09-02
> Also, does anyone have any clues as to how to get the back & forward buttons on a MS IntelliMouse Explorer to work?

To get my MS Intellimouse working, all I had to do was  edit my xorg.conf file.  Type this in a terminal:
```
sudo gedit /etc/X11/xorg.conf
```

Scroll down until you see the entry for your mouse, just do a search for mouse if you want.  Across from "protocol", you'll probably see an entry saying "ImPS/2".  Change that to "ExplorerPS/2".  Then just restart X by hitting Ctrl+Alt+Backspace and log back in.  If your back/forward buttons still don't work in Firefox, then go here and follow the guide (you already did the first part about editing the xorg.conf though):  [http://ubuntuforums.org/showthread.php?t=28374&highlight=back+forward+mouse+buttons](http://ubuntuforums.org/showthread.php?t=28374&highlight=back+forward+mouse+buttons)

He goes into more detail, but I only had to do the first part to get mine to work.

>  Ummm, looking at the fstab thingy, i'm a tad confused/not-getting where i edit/add the windows partition bit in.

Go here:  [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Just make sure you do the command:
```
sudo fdisk -l
```
to figure out which harddrive is your Windows drive.  Then just adjust any of the "/dev/hda1" entries accordingly with what that command shows for your Windows drive.

---

### Post by mlomker on 2005-09-02
[QUOTE=mark2]Ummm, looking at the fstab thingy, i'm a tad confused/not-getting where i edit/add the windows partition bit in.[/QUOTE]

Generally at the end of the file.   :razz: 

If you post the output of **fdisk -l** then someone can tell you what to add.  I should warn you that NTFS drives are read-only under linux.  There's some fancy stuff (recompiling the kernel) to make it read/write but it's not reliable.

You'll need to be more specific about the apt-get error.  Open a command prompt, type **su** and reenter your password (this logs you in as root so you can install stuff), then type **apt-get install kdesktop**.  It worked for me...I'm running Kubuntu and love it.

---

### Post by mark2 on 2005-09-02
[QUOTE=mlomker]Generally at the end of the file.   :razz: 

If you post the output of **fdisk -l** then someone can tell you what to add.  I should warn you that NTFS drives are read-only under linux.  There's some fancy stuff (recompiling the kernel) to make it read/write but it's not reliable.

You'll need to be more specific about the apt-get error.  Open a command prompt, type **su** and reenter your password (this logs you in as root so you can install stuff), then type **apt-get install kdesktop**.  It worked for me...I'm running Kubuntu and love it.[/QUOTE]


Um, i just tried the su thingy in the terminal and put in the password, and it says su: Authentication failure


And i can run other stuff in root fine...

---

### Post by mark2 on 2005-09-02
[QUOTE=mark2]Um, i just tried the su thingy in the terminal and put in the password, and it says su: Authentication failure


And i can run other stuff in root fine...[/QUOTE]
 Ok, now i get This error message...

root@linmark1:/home/mark # apt-get install kdesktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kdesktop

---

### Post by mark2 on 2005-09-02
[QUOTE=mark2]Ok, now i get This error message...

root@linmark1:/home/mark # apt-get install kdesktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kdesktop[/QUOTE]
 And i still cant mount my damn NTFS Hdd...

---

### Post by KingBahamut on 2005-09-02
not kdesktop 

apt-get install kubuntu-desktop 

be sure you have all the respositories as well from 
[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by mark2 on 2005-09-02
[QUOTE=KingBahamut]not kdesktop 

apt-get install kubuntu-desktop 

be sure you have all the respositories as well from 
[http://ubuntuguide.org](http://ubuntuguide.org)[/QUOTE]

Well, when i tried to get it to do what it says on [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) it spits out this error at me:

cp: cannot stat `/etc/apt/sources.let': No such file or directory

---

### Post by mark2 on 2005-09-02
[QUOTE=mark2]Well, when i tried to get it to do what it says on [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) it spits out this error at me:

cp: cannot stat `/etc/apt/sources.let': No such file or directory[/QUOTE]
 Yay i got it to go finally. HEHE... silly me, i prolly did something wrong and didnt notice it. Stupid dyslexia for u..

---

