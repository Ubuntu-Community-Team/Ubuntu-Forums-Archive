---
title: "How to stop X?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by ZijWePro on 2006-06-04
Hey, I'm quite new to Linux and stuff.
I'm just trying to install my nVidia drivers for Linux but it says that I need to shut down X (Which is GNOME I guess...). How must I do this?
Many thanks in advance... Again... :) 
Jeroen van Zijp
edit: By the way, I also have another problem: I still have a NTFS partition in my PC but I can't open it to play MP3's from it in example. When opening the drive it says:
Can't mount the selected drive.
Error: /dev/hdb1 isn't a removable drive.
Error: Couldn't run pmount.
How do I solve this also? Because all my mp3's and movies are on the drive and I don't wanna format it to ext3 i.e.... Many thanks again :D

---

### Post by tseliot on 2006-06-04
[QUOTE=ZijWePro]Hey, I'm quite new to Linux and stuff.
I'm just trying to install my nVidia drivers for Linux but it says that I need to shut down X (Which is GNOME I guess...). How must I do this?[/QUOTE]
Try my guide:
[http://ubuntuforums.org/showthread.php?t=139264]("http://ubuntuforums.org/showthread.php?t=139264")

---

### Post by ZijWePro on 2006-06-04
I guess it worked, after rebooting, before the log-on screen it gave me the nVidia logo...

---

### Post by tseliot on 2006-06-04
[QUOTE=ZijWePro]I guess it worked, after rebooting, before the log-on screen it gave me the nVidia logo...[/QUOTE]
Yes, it did. Congratulations :)

---

### Post by shrift on 2006-06-04
Just for future reference, it is an easy command: ```
sudo /etc/init.d/gdm stop
```
And to start it again:```
sudo /etc/init.d/gdm start
```

---

### Post by ZijWePro on 2006-06-04
Ok thanks all, but I still have the mounting problem...
Can anyone of you help me to let it mount each time I start up and so I can access the NTFS partition? I already edited the /etc/fstab file but it first said only root can mount the partition. So then I added my account to the root group and rebooted... Now the mountpoint is there but when I try to access it, it says I don't have the rights to open the "directory". ](*,)  I really hope I can stay using that NTFS partition because all my beloved music is on it...
Many thanks in advance!

---

### Post by shrift on 2006-06-04
What command are you using to try and mount it? Also, what directory are you trying to mount it to?

---

### Post by ZijWePro on 2006-06-04
I'm trying to mount it with the following command:
mount /dev/hdb1
I defined the directory/mountpoint as /datahd
This is what my /etc/fstab looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /datahd         ntfs    defaults        0       1
```

I hope this is right...

---

### Post by shrift on 2006-06-04
Okay, make your ntfs line look like this:
```
/dev/hdb1       /datahd         ntfs    user,umask=000        0       0
```

That should do it. Let me know.

---

### Post by shrift on 2006-06-04
One more thing, you should add your user to the root group. That is unsafe, and unecessary. Try my fix, and remove your user from the root group.

---

### Post by tseliot on 2006-06-04
[QUOTE=ZijWePro]I'm trying to mount it with the following command:
mount /dev/hdb1
I defined the directory/mountpoint as /datahd
This is what my /etc/fstab looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /datahd         ntfs    defaults        0       1
```

I hope this is right...[/QUOTE]
Read this guide, it's very easy (look for the part "Make partitions automatically available"):
[http://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html]("http://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html")

---

### Post by ZijWePro on 2006-06-04
Hehe it makes sense now! I can read from the HD and it works all perfect!
Many thanks to all of you guys who helped me out with my problems! If I ever get another problem with Ubuntu, I will return here because your support is great! :D
Jeroen van Zijp

---

### Post by shrift on 2006-06-04
Good. Out of curiousity, what did your fstab line look like at the end?

---

### Post by shamrock_uk on 2006-06-04
You may want to remove yourself from the root group afterwards by the way. 

Loosely speaking, X is the graphical base to your system - its what lets you see a graphical desktop. Gnome or KDE are then a collection of further applications to make it pretty and functional, but it's perfectly possible to only run X on its own. 

It's a little different from Windows where it all seems to be integrated together, but much more flexible. 

Another little tip - if ever you get an application freeze the screen (very unlikely, I know...) then you can do Ctrl + Alt + Backspace to kill only X. That way you can be back at a login prompt without you having to restart the whole computer.

---

### Post by ZijWePro on 2006-06-04
@Shrift: Erhm, I made the line like you suggested...
@shamrock_uk: I already removed my account from the root usergroup like Shrift said. Anyway, thanks for your other tips!

---

### Post by shrift on 2006-06-04
Cool. : ) Just wanted to make sure that worked like I expected it to.

---

### Post by ZijWePro on 2006-06-05
Hmmm, I'm just noticing I don't have write access to the NTFS drive :(
I can read everything from it but I can't write to it like i just say...
Can anyone help me with this one?
Sorry that I said yesterday I had write access to it, but it seems not now...

---

### Post by shrift on 2006-06-05
Make certain that you are read/write permission to the folder that you are mounting the drive to. First you should unmount the drive, check the permissions, then remount it and try then.

---

### Post by ZijWePro on 2006-06-05
Sorry, I'm a bit new to Linux so how do I check the permissions?
Edit:
I now also tried the things tseliot said in his how-to but it doesn't make sense... :(
I think it's the filesystem itself which doesn't allow writing to it. If I go to / and look to the pictogram from /datahd I see a pencil and a forbidden-sign right-above the icon, which means I can't write to it I guess...
By the way, I also tried the directory /media/windows to mount it too but got the same problem there...

---

### Post by shrift on 2006-06-05
browse to the folder in nautilus, right click on it, and click "properties" then click the "permissions" tab. Make sure you have are allowed to write to the folder, if your not then you need to make it so you can. If you don't own the folder then you will have to change your permissions to the folder in the commandline.

Let me know.

---

### Post by xtacocorex on 2006-06-05
NTFS write support does not work. 

There are ways to get around it, but it isn't worth it because you can only edit files that are already created and you can't increase their file size.

The best way for compatibilty is to have a separate fat32 partition since those are both read/write in Windows and Linux. 

There are also drivers for Windows that allow you to see ext2/3 partitions: [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by shrift on 2006-06-05
Oh, heh, yeah. I forgot about that. Sorry. You won't be able to write to your NTFS without some, probably, painful work. And it's not very stable.

---

### Post by ZijWePro on 2006-06-05
Hmm, that's a big pitty :(
So I have to live with it...

---

### Post by shrift on 2006-06-05
Unfortunately yes, however you can write to fat32 filesystems. If you need to share some files between OSs, that is a good way.

---

