---
title: "Don't show smbmount-Mounts on Desktop"
date: 2009-05-08
forum: Desktop Environments
---

### Post by Broco on 2009-05-08
Hi there guys,

I just wanted to know if it's possible to prevent Ubuntu from showing folders mounted by smbmount on the Desktop.
I mount them via ```
smbmount //*SERVER-IP*/Folder /home/broco/.sambamounts/Folder -o user=broco,iocharset=utf8
```
which means that they are neither in /media nor in /etc/fstab.

I thought Ubuntu just shows mounts in /media on the Desktop but I seem to be wrong.
The option "volumes_visible" (gconf-editor) should stay enabled because I still want to see plugged-in USB-Sticks, Bluetooth devices, etc. I just want to hide the Samba-Mounts.

Any Suggestions?

Greetings 
Broco

Edit: I'll never be perfect in English....

---

### Post by DJJo on 2009-05-08
I think it is normal with smb.

you can make a jumper.
[LEFT]second mouse on the desktop and make jumper.
or starter i dont the richt translation for it.


[/LEFT]

---

### Post by Broco on 2009-05-15
I don't want it to be normal.
When not using smbmount, OpenOffice.org will ask you for your password everytime you want to open a file. That's really annoying.
So I decided to use smbmount but I don't want the Mounts to appear on the Desktop.
Isn't there anything possible (maybe with HAL)?

Greets
Broco

---

### Post by satiricon_ on 2009-08-09
I have a similar problem, but I dont want any mount icon in my desktop. I have unchecked volumes_visible in /apps/nautilus/desktop but the icon is still there =(

I used the comand...

sudo smbmount //192.168.1.103/E /home/david/temp-SE/ -o user=guest pass=""

I am doing some thing wrong? my ubuntu is 9.04

help please?

---

### Post by TheNessus on 2009-08-09
I hate that too, but got no solution.

Instead, I minimized the size of the icons and replaced them with transparent .png's, so that I got only text icons. It combines nicely on the desktop with conky. But still, if there's a way to not show the mounts on the desktop it would be awesome.

---

### Post by satiricon_ on 2009-08-09
My mistake =S

I was using "sudo gconf-editor" to uncheck the mount-in-desktop option and so I was configuring the root desktop.

To hidde the mounts from your desktop yo must in command line write

gconf-editor

without sudo.. and then in apps->nautilus->desktop uncheck volumes_visible option
:)

---

### Post by lostinswitz on 2009-10-16
[satiricon_]("http://ubuntuforums.org/member.php?u=890559") - Thanks

I was annoyed by this as well.  Your solution worked great.

---

### Post by theZoid on 2009-10-17
> **lostinswitz said:**
> [satiricon_]("http://ubuntuforums.org/member.php?u=890559") - Thanks

I was annoyed by this as well.  Your solution worked great.

I just stopped everything in gconf, and added the volume mounter applet to the panel

---

### Post by goltoof on 2010-08-05
I also want to fix this, but I'm not finding anything to uncheck. "volumes_visible" is not an option I see in gconf-editor anywhere.

Is there another way I can prevent mounts from showing on my desktop?

---

