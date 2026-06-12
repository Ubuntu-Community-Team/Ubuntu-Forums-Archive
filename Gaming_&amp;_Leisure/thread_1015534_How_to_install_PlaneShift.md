---
title: "How to install PlaneShift"
date: 2008-12-18
forum: Gaming &amp; Leisure
---

### Post by BigBig5 on 2008-12-18
:confused:I been trying many ways to install PlaneShift, but none work
This is what happens in Terminal:confused:
> trekkie@DBTLINUX:~$ mkdir ~/.Games
trekkie@DBTLINUX:~$ cd ~/Desktop
trekkie@DBTLINUX:~/Desktop$ chmod +X PlaneShift-v0.4.03-x86.bin
trekkie@DBTLINUX:~/Desktop$ sudo ./PlaneShift-v0.4.03-x86.bin
[sudo] password for trekkie: 
Segmentation fault
trekkie@DBTLINUX:~/Desktop$ 

---

### Post by giantoz on 2008-12-19
oops. sorry, i posted for the wrong game...

maybe try this:

[http://ubuntuforums.org/showthread.php?t=421457](http://ubuntuforums.org/showthread.php?t=421457)

---

### Post by Extol11 on 2009-01-09
I installed it and everything went fine except the last part. I used this guide. 
[http://gaming.gwos.org/doku.php/guides:64bit:planeshift]("http://gaming.gwos.org/doku.php/guides:64bit:planeshift") it's the 64 bit version as you can see. 

The last part for doing the menus with alacarte didn't work. I typed what it said in there and it didn't work. The thing is the installer is "PlaneShift-v0.4.03-x64.bin" and the version in that guide is "PlaneShift-v0.4.01-x64.bin" (notice the number difference). I think the commands could have changed a bit. Everything in the installer went perfect. The only problem is that the menus for starting the game in the application applications menu don't seem to work. Maybe the commands should be different or maybe, just maybe, there's a new patch in the site [http://www.planeshift.it/download.html]("http://www.planeshift.it/download.html")which seems to be necessary and since the guide is outdated, it left out. Can anyone help me?

---

### Post by Extol11 on 2009-01-10
Nobody knows? Nobody else has tried to run this game or has the game running already?

---

### Post by regor210 on 2009-01-12
Assuming you have your 3D driver installed.&#65279;

Download Planeshift linux (64 bit): or Linux (32 bit): Into your home folder. you can find it here.
 [http://www.planeshift.it/download.html](http://www.planeshift.it/download.html)
 
open a Terminal: In Ubuntu goto Applications>Accessories>Terminal
 
Set your permissions: type this command into the terminal minus the $. Note make sure the name is the same as you downloaded. 

$ sudo chmod a+x PlaneShift-v0.4.03-x64.bin
 
Start the installer: type this command into the terminal minus the $.Note make sure the name is the same as you downloaded. 
$ ./PlaneShift-v0.4.03-x64.bin
 
Accept this license? select yes.

When asked for Installation Directory, I think it best to place it in your home folder. Not /opt. so I use /home/regor210/ . If your not sure of the name of your home folder, in Ubuntu goto Places>Home Folder. so you would use /home/your name/
 
when asked for System wide install? select No
 
when asked What Window Manager are you using? If your using Ubuntu select Gnome.
 
when asked Install menu Icons? select yes.
 
when asked create desktop shortcuts? select yes.
 
when asked Set Permissions? say No 

I just used this guide and it worked fine.
Hope this helped

---

### Post by landshrk on 2009-02-13
Okay. Followed the directions here, and this is what I got:

bash: ./PlaneShift-v0.4.03-x64.bin: cannot execute binary file

Any ideas as to what's going on?

---

### Post by Perfect Storm on 2009-02-13
Try **sh PlaneShift-v0.4.03-x64.bin** instead.

---

### Post by waxyfresh on 2009-02-13
Im having a similar problem:

david@IceWeasel:~$ cd /home/david/Desktop/
david@IceWeasel:~/Desktop$ sh PlaneShift-v0.4.03-x64.bin
sh: Can't open PlaneShift-v0.4.03-x64.bin
david@IceWeasel:~/Desktop$ ./configure PlaneShift-v0.4.03-x64.bin
bash: ./configure: No such file or directory
david@IceWeasel:~/Desktop$ ./PlaneShift-v0.4.03-x64.bin
bash: ./PlaneShift-v0.4.03-x64.bin: No such file or directory
david@IceWeasel:~/Desktop$ ./configure PlaneShift-v0.4.03-x64.bin
bash: ./configure: No such file or directory
david@IceWeasel:~/Desktop$ sh PlaneShift-v0.4.03-x64.bin
sh: Can't open PlaneShift-v0.4.03-x64.bin
david@IceWeasel:~/Desktop$ sudo sh PlaneShift-v0.4.03-x64.bin
[sudo] password for david: 
sh: Can't open PlaneShift-v0.4.03-x64.bin
david@IceWeasel:~/Desktop$

---

### Post by Perfect Storm on 2009-02-13
Try:

```
cd ~/Desktop
chmod +x PlaneShift-v0.4.03-x64.bin
./PlaneShift-v0.4.03-x64.bin
```

---

### Post by Henrikzhura on 2009-03-12
Try this:

mkdir ~/.Games
cd ~/Desktop
chmod +x PlaneShift_CBV0.3.020-x86.bin
sudo ./PlaneShift_CBV0.3.020-x86.bin

---

### Post by Nempis on 2009-03-26
None of all these things seem to work with me neither. I could make it executable but after that it just says it can't execute it or it says syntax error.

---

### Post by deLeewit on 2009-12-05
> **regor210 said:**
> Assuming you have your 3D driver installed.&#65279;

Download Planeshift linux (64 bit): or Linux (32 bit): Into your home folder. you can find it here.
 [http://www.planeshift.it/download.html](http://www.planeshift.it/download.html)
 
open a Terminal: In Ubuntu goto Applications>Accessories>Terminal
 
Set your permissions: type this command into the terminal minus the $. Note make sure the name is the same as you downloaded. 

$ sudo chmod a+x PlaneShift-v0.4.03-x64.bin
 
Start the installer: type this command into the terminal minus the $.Note make sure the name is the same as you downloaded. 
$ ./PlaneShift-v0.4.03-x64.bin
 
Accept this license? select yes.

When asked for Installation Directory, I think it best to place it in your home folder. Not /opt. so I use /home/regor210/ . If your not sure of the name of your home folder, in Ubuntu goto Places>Home Folder. so you would use /home/your name/
 
when asked for System wide install? select No
 
when asked What Window Manager are you using? If your using Ubuntu select Gnome.
 
when asked Install menu Icons? select yes.
 
when asked create desktop shortcuts? select yes.
 
when asked Set Permissions? say No 

I just used this guide and it worked fine.
Hope this helped


I used this guide and it works under Ubuntu 9.10 64-bit. After these instructions, I just went 'Places->Home Folder->Plane Shift->psclient', to run it.
Don't use (right-click) properties on the desktop icon to change the 'execute as file', it doesn't work. Don't think it hurts, but it didn't work for me.

---

### Post by love2learn on 2010-01-27
yeah, no go for me either:

l2l@l2l-laptop:~/Games$ ls
PlaneShift-v0.5.1-x86.bin
l2l@l2l-laptop:~/Games$ sudo chmod a+x PlaneShift-v0.5.1-x86.bin 
[sudo] password for l2l: 
l2l@l2l-laptop:~/Games$ ./PlaneShift-v0.4.03-x64.bin
bash: ./PlaneShift-v0.4.03-x64.bin: No such file or directory
l2l@l2l-laptop:~/Games$ ./PlaneShift-v0.5.1-x86.bin 
Segmentation fault
l2l@l2l-laptop:~/Games$ sh PlaneShift-v0.5.1-x86.bin 
PlaneShift-v0.5.1-x86.bin: 1: Syntax error: "(" unexpected
l2l@l2l-laptop:~/Games$ ./configure PlaneShift-v0.5.1-x86.bin 
bash: ./configure: No such file or directory
l2l@l2l-laptop:~/Games$ sudo ./PlaneShift-v0.5.1-x86.bin 
Segmentation fault
l2l@l2l-laptop:~/Games$ 


This is my first attempt at installing but I will come back with answers as this was the top google choice for my search.

---

### Post by love2learn on 2010-01-27
That was a little easier than I thought it would be. It was a bad download. Here is what worked for me.

l2l@l2l-laptop:~/Games$ ls
old plane  PlaneShift-v0.5.1-x86(2).bin
l2l@l2l-laptop:~/Games$ chmod a+x PlaneShift-v0.5.1-x86\(2\).bin
l2l@l2l-laptop:~/Games$ ./PlaneShift-v0.5.1-x86\(2\).bin 

Cheers

---

