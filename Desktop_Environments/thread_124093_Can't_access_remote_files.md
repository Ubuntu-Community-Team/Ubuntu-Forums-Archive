---
title: "Can't access remote files"
date: 2006-01-31
forum: Desktop Environments
---

### Post by el3ktro on 2006-01-31
I'm trying to share files between my desktop and my laptop. Since I have SSH running on both anyway and Gnome supports "mounting" remote dirs trough SSH I thought I'll try that. I can browse the remote directory just fine, but Gnome seems to have problems with filenames that contain blanks. When I click on such a file to open it, Gnome tells me that the file sftp://user@host:22:/document%20with%20blank.doc can't be opened. All blanks are substituted by a %20 and I can't access this file. I also tried sharing with Samba, but this causes the same error in Gnome. Any way around this?

Tom

---

### Post by el3ktro on 2006-01-31
I just figured out that I can with no problem copy the file to the local host, but I can't open them directly by clicking on it. Why does the "Connect to server" dialog does not offer to access NFS volumes btw?

Tom

---

### Post by el3ktro on 2006-02-02
I just figured out that the same applies for NFS. Also, there another stupid thing:

When I go to "Location->Network server" and connect to my laptop, I have an icon for this on my desktop and the network share also appears in the "Locations". In GEdit for example, when I click open I can choose between Home folder, file system, and the network share. But I can't choose the network share when I try to save a file in GEdit.

Damn I hoped Gnome would make this network thing better somehow. I'm trying for two years to find an easy way to access files on a remote computer, but neither KDE or Gnome offer this :-( I thought Linux was built for networks???


Tom

---

### Post by cwaldbieser on 2006-02-02
[QUOTE=el3ktro]I'm trying to share files between my desktop and my laptop. Since I have SSH running on both anyway and Gnome supports "mounting" remote dirs trough SSH I thought I'll try that. I can browse the remote directory just fine, but Gnome seems to have problems with filenames that contain blanks. When I click on such a file to open it, Gnome tells me that the file sftp://user@host:22:/document%20with%20blank.doc can't be opened. All blanks are substituted by a %20 and I can't access this file. I also tried sharing with Samba, but this causes the same error in Gnome. Any way around this?

Tom[/QUOTE]
Do you get the same problem if you ssh/sftp/scp from the command line?

---

### Post by el3ktro on 2006-02-02
I found out that this is due to lack of support for VFS in OOo. Damn what is openoffice.org2-gnome for then?? :-k

---

### Post by Herman on 2006-02-02
> Damn I hoped Gnome would make this network thing better somehow. I'm trying for two years to find an easy way to access files on a remote computer, but neither KDE or Gnome offer this :sad: I thought Linux was built for networks??? Hello, I'm not sure I exactly understand your particular problem or if I can help or not, but I use SSH all the time on my home network between several PCs, and never had a problem with it. I have a router with four desktops and a laptop, they all dual boot. 
Try reading [how mine is set up]("http://users.bigpond.net.au/hermanzone/p11.htm") and see if it has any info that will help you, maybe it will or maybe not, but I hope it might help. Best of luck with it, :-D (Herman)

---

### Post by tylluan on 2006-02-02
I have been trying to get a linux home network set up for ages with no success.  Never could make sense out of any of the tutorials or instructions on line.  Your instructions worked perfectly.

Thanks!

---

### Post by Herman on 2006-02-02
Thank you tylluan, it's always nice to get a little feedback, especially the positive kind.
Mr Shuttleworth and the team working to develop Ubuntu have given us excellent software, we just have to learn how to use it.  Ubuntu is great! :D (Herman)

---

### Post by el3ktro on 2006-02-03
[QUOTE=Herman]Hello, I'm not sure I exactly understand your particular problem or if I can help or not, but I use SSH all the time on my home network between several PCs, and never had a problem with it. I have a router with four desktops and a laptop, they all dual boot. 
Try reading [how mine is set up]("http://users.bigpond.net.au/hermanzone/p11.htm") and see if it has any info that will help you, maybe it will or maybe not, but I hope it might help. Best of luck with it, :-D (Herman)[/QUOTE]

Hello,
well thanks for your link, it actually shows exactly what I've done. The problem with this setup is that it doesn't work with OpenOffice. If I have the remote folder "mounted" like described in your tutorial, and when I browse the remote directory in Nautilus and when I click on an office file, I get an error that the file could not be opened, because OOo dosn't support this I suppose. Most standard Gnome apps work fine though, I can with no problem open pictures, music files & videos (gThumb, Rhythmbox, Totem) this way.

Another problem is that for example in GEdit: I open GEdit, choose "Open file" and select the remote directory in the "places" menu & open a remote file. This works fine. But when I try to SAVE a file, I can NOT select the remote directory. So I can read from it, but not write to it from certain apps like GEdit - because the remote direcotry doesn't even appear in the "places" menu. In Nautilus, I can read & write on the remote directory just as if it was local.

Is there any solution to this? This damn behaviour is the only thing that's keeping me away from a simple&easy home network that also my girlfriend can use ... :-(


Tom

---

### Post by carlosqueso on 2006-02-03
I don't know if this will work, because I haven't had problems, but can you create a symlink to the remote directory on your local machine and trick gedit into saving on the other machine?  Also for the OOo problems, I'd use abiword and gnumeric, they may work, and gnumeric has the statistics functions that OOo lacks.

---

