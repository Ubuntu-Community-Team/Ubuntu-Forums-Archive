---
title: "Help installing UT2004"
date: 2006-02-12
forum: Gaming &amp; Leisure
---

### Post by darcstarr on 2006-02-12
I'm having trouble installing UT2004. I used wine to run the setup.exe file under the install cd#1 and it was going well until it asked me to put cd#2 in. When I inserted cd#2 and clicked on the box asking me to switch to cd#2 kept popping up even though that cd was already in the drive.

---

### Post by Harleen on 2006-02-12
Forget wine and install the native version. There is an install script on one of the CDs (the first?). Copy it somewhere on your hard disc and run it.

---

### Post by MetalMusicAddict on 2006-02-12
Its on the last CD. Should be a **.sh** So the command will be something *like*:
**sudo sh /media/cdrom/ut2004.sh**

---

### Post by darcstarr on 2006-02-12
Well that all worked up to the point where it asks me to mount Unreal Tournament Disk 2 CDROM. When I insert it and click OK the box asking me to insert the Disk 2 CDROM keeps popping up. How do I solve this problem?

---

### Post by darcstarr on 2006-02-12
There is no .sh file in the last cdrom its actually in the first cdrom.

---

### Post by darcstarr on 2006-02-12
There is an attachment below which shows the install screen im currently at.

---

### Post by Harleen on 2006-02-12
I only have the DVD version, so I can only guess what you have to do when installing from CD.
If you could change CDs you could obviously unmount the first CD - good. Is the second CD mounted automatically when you insert it? You can check that by typing "mount" in a terminal. There should be some entry for /media/cdrom. If not, you can mount the CD by hand by typing "mount /media/cdrom".
Maybe you can mount the CD also using an icon on your Desktop. It''s possible in KDE, so maybe GNOME offers something similar.

---

### Post by MetalMusicAddict on 2006-02-12
[QUOTE=darcstarr]There is no .sh file in the last cdrom its actually in the first cdrom.[/QUOTE]
Weird. Mine is on the last. I now have it on a DVD though. I figured out how to build a DVD from the CDs.

---

### Post by darcstarr on 2006-02-12
[QUOTE=Harleen]I only have the DVD version, so I can only guess what you have to do when installing from CD.
If you could change CDs you could obviously unmount the first CD - good. Is the second CD mounted automatically when you insert it? You can check that by typing "mount" in a terminal. There should be some entry for /media/cdrom. If not, you can mount the CD by hand by typing "mount /media/cdrom".
Maybe you can mount the CD also using an icon on your Desktop. It''s possible in KDE, so maybe GNOME offers something similar.[/QUOTE]

Ya, the second CD is mounted autmatically. But I still cannot get past the step to install on Disk 2.

---

### Post by siorai on 2006-02-12
You actually should copy the installer onto your harddrive, it doesn't matter where, just on the desktop is fine, and run it from there.

---

### Post by Harleen on 2006-02-12
On your screenshot you have executed the install script from /media/cdrom. I'd assume, that you wouldn't be able to eject the CD 1 in that case, but you could...
If you have mounted CD2, the install should continue. I still guess, that you haven't mounted it correctly. Can you cd into the /media/cdrom directory and check, if you really have mounted the second CD?

---

### Post by darcstarr on 2006-02-12
[QUOTE=Harleen]On your screenshot you have executed the install script from /media/cdrom. I'd assume, that you wouldn't be able to eject the CD 1 in that case, but you could...
If you have mounted CD2, the install should continue. I still guess, that you haven't mounted it correctly. Can you cd into the /media/cdrom directory and check, if you really have mounted the second CD?[/QUOTE]

> darcstarr@darcstarr:~$ cd /media/cdrom
darcstarr@darcstarr:/media/cdrom$ ls
ls: ???????: Input/output error
ls: ???????????????????????????????????????????????????????????????????????????????????????????: Input/output error
darcstarr@darcstarr:/media/cdrom$

Thats what I got. I'm assuming that the input/output error suggests that you're on to something with the mounting issue. Now the thing I need to know is how to fix this problem.

---

### Post by Harleen on 2006-02-12
That doesn't look too good.
Do what siorai has suggested: Copy the installer on you hard disk and run it from there. Because you won't be able to unmount the CD if you still access the directory you have to do this.
Then you should be able to unmount the CD1 and mount CD2 when the installer asks for it.
Maybe this guide can help you: [http://www.linuxelectrons.com/article.php/20040419200456201](http://www.linuxelectrons.com/article.php/20040419200456201)

---

### Post by Sp@z on 2006-02-12
[QUOTE=Harleen]That doesn't look too good.
Do what siorai has suggested: Copy the installer on you hard disk and run it from there. Because you won't be able to unmount the CD if you still access the directory you have to do this.
Then you should be able to unmount the CD1 and mount CD2 when the installer asks for it.
Maybe this guide can help you: [http://www.linuxelectrons.com/article.php/20040419200456201](http://www.linuxelectrons.com/article.php/20040419200456201)[/QUOTE]
he/she is right I had the same issue. I copied the installed from the disk to my hard drive and it worked like a charm after that...it is a mounting unmounting issue.

---

### Post by darcstarr on 2006-02-12
Ya ...I'm having a problem with the mounting/unmounting step in the sense that I don't know how to do it.

---

### Post by Harleen on 2006-02-12
On the command line you mount a cd by typing "sudo mount /media/cdrom"
To unmount it type "sudo umount /media/cdrom"

This is assuming that no automount daemon is doing nasty things behind our back. Under KDE CDs are mounted only with user interaction. If GNOME handles this different, that could cause a problem.

---

### Post by Sp@z on 2006-02-12
When you insert a disk does an icon appear onyour desktop? It should have the name of the disk. I simply right clicked mine and selcted "eject" and it worked without a hitch. If it doesnt' show up go to "applications"  "system tools" "configuration editor" the that will open a window and them select  "apps" "nautilais" "desktop" then check the "Volumes visible" box and you should see all the volumes after that. If there is no CD in the drive though, you won't see anything till there is. 

This is assuming your terrified of the terminal window like I am LMAO, but copy and paste his commands for ease though!

---

### Post by darcstarr on 2006-02-12
Ya! It finally worked! Ok I got it installed. Thanks everyone for all your help.:)

---

### Post by handy on 2006-02-12
The Linux install file was on the first CD on my UT2k4 set.  I copied it to the desktop & ran it from there.

I would just have to eject each CD using the RMB menu / eject & put the next one in, select OK or whatever on the requester & continue.

You can also run the linux setup in the terminal... No harm in trying...

---

### Post by handy on 2006-02-12
A lot can happen while I'm typing! :KS 

Good news! :mrgreen:

---

