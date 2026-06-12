---
title: "Restoring ubuntu panel &quot;deleted&quot; my desktop files!"
date: 2010-05-19
forum: Desktop Environments
---

### Post by RasmusEriksson on 2010-05-19
After restoring my panel using these commands:

owner@owner-desktop:~$ gconftool-2 –shutdown
owner@owner-desktop:~$ rm -rf ~/.gconf/apps/panel
owner@owner-desktop:~$ pkill gnome-panel

my files on the desktop, in my home directory went missing. Also looking at my harddrive it seems like it has completely wiped out my content.

I had some important files on my desktop and I am wondering if there is any way to get them back? It doesn't reasonable that all my files were deleted during a panel restore, maybe they are hiding under a rock somewhere ;(.

Oh and the system I am running it on is: Ubuntu 10.04

---

### Post by emilywind on 2010-05-19
> **RasmusEriksson said:**
> After restoring my panel using these commands:

owner@owner-desktop:~$ gconftool-2 –shutdown
owner@owner-desktop:~$ rm -rf ~/.gconf/apps/panel
owner@owner-desktop:~$ pkill gnome-panel

my files on the desktop, in my home directory went missing. Also looking at my harddrive it seems like it has completely wiped out my content.

I had some important files on my desktop and I am wondering if there is any way to get them back? It doesn't reasonable that all my files were deleted during a panel restore, maybe they are hiding under a rock somewhere ;(.

Oh and the system I am running it on is: Ubuntu 10.04
You did not accidentally put a space between the ~/ and .gconf/apps/panel, did you? As in...

```
owner@owner-desktop:~$ rm -rf ~/ .gconf/apps/pane
```

If so, that would have been telling it to delete your home directory along with .gconf/apps/panel. If not, I am unsure what is wrong but perhaps it is just a GUI issue. Could you post the output of `ls ~/`?

---

### Post by RasmusEriksson on 2010-05-19
I might have accidentally used an additional space, I dont know ;)

But what I do know, is that in my home directory there is one file from my previous settings that is still there.  

Post of ls ~/:
ansökning.odt  Dokument   Hämtningar  Musik    Skrivbord
Bilder           Downloads  Mallar      Publikt  Video

---

### Post by emilywind on 2010-05-19
If there was a space involved, you likely deleted everything in your home directory. If you had OpenOffice opened at the time and saved that file after running those commands then that would be why it survived. If that is the case, there is not much I can help you with at this point, because if you put a space there then you deleted your home directory and the files it contained. You can try finding a file recovery program, but I am not sure how possible it is to restore deleted files on an ext4 file system.

Outside of that, I recommend that you to be extremely careful when using the terminal in the future, *especially* when running a command like `rm -rf` on a folder. The f in the -rf means force, which means it will just listen to you and not ask any questions. Also, keep in mind that non-escaped spaces often mean multiple arguments, and are not the same as having no space in the command. When it comes to deleting things, you could always use nautilus (the file browser) which is visual and harder to mess up in. Unfortunately though, giving commands for the terminal is a lot easier to put into a tutorial since it is text-based and extremely powerful, so you will likely run into them a lot.

Anyway, be careful what you run in the command line without knowing what it does, and make certain you follow every command exactly how it is if you do. If you have to do so, copy and paste the commands you are told to run into the command line and hope the people who made them did not mess up. haha

This should help you acquire a decent idea of how the command line works: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Just for the sake of the possibility you did not kill your home directory, could you post the output of `cat /etc/fstab`? Cheers. :)

---

### Post by RasmusEriksson on 2010-05-20
First of all I would like to thank you for the information. Most of the stuff I had backed up on a external hard drive so it was not the most horrible thing that could happen.

Here is a post of what you asked for ;):

rasmus@raawr-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=995e91f5-bcf5-44af-948b-c87b4e686870 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=91f280e1-9a52-41ce-9240-9d07425578e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
rasmus@raawr-laptop:~$ 




And once again thank you for all the information you gave me. I will be more careful in the future ;)

---

### Post by emilywind on 2010-05-20
Seems you do not have a separate /home partition, so disregard the fstab thing. As for the information, you are welcome. I came into this thread to help, so I am glad to hear that I did. Cheers. :)

---

