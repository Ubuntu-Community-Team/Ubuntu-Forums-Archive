---
title: "Playing Media Over the Network"
date: 2006-01-05
forum: Desktop Environments
---

### Post by cs378 on 2006-01-05
I have a Desktop running WinXP and laptop running Ubuntu Breezy 5.10

There is a shared folder in the desktop which contain a *.avi video file. I want to play that file over the network on my laptop, how would I do that on Ubuntu?

New to linux....

I have tried the vlc player which plays all media, but it won't play over files over the network. so can someone tell me a tip that will allow me to do that.

Thx u

Ubuntu is great <-- first Linux that worked on my laptop :KS

---

### Post by superm1 on 2006-01-05
Well for a temporary solution to copy the movie over goto Places-> Connect to Network Server.  If you fill in the information for your file share, it will temporarily make a folder icon on your desktop.  You can open the share out and copy stuff out.  Unfortunately, you can't actually access it directly from *most* apps.  

If you want a more perm.  solution, you can create a mount point in /mnt or /media & mount the windows share there.  You will be able to directly access the movie files from any of your apps, totem, xine, mplayer, vlc. etc.

---

### Post by cs378 on 2006-01-05
Thx for replying

I don't want to copy over the file because of limited available space i have on my laptop

As you said, I can mount the shared folder to media

how would i do that??

sudo mount smb://<ComputerName> /media/myDesktop

won't work

thx again

---

### Post by superm1 on 2006-01-05
Sorry, you'll have to install smbfs.  I forget that Ubuntu creates a seperate package for it.

```
sudo apt-get install smbfs
```

Your mount command should work after that.  Also, you don't need the smb://.
Instead do it like you would access a share in windows, or at least how I remember it to be, it's been some time:  //computername/sharename

You might rather just put it in your fstab, so that you don't need all the mount information every time.  

See this post for more info. [http://ubuntuforums.org/showpost.php?p=231417&postcount=3](http://ubuntuforums.org/showpost.php?p=231417&postcount=3)

You said this was for a laptop.  If you add the flags "user" & "noauto" you can set it so you can just go to Computer in gnome and double click it to mount it.  When you are done, you can right click and hit unmount volume.  You will probably need to log out and back in for this to take effect however.  I think gnome re-reads the fstab to populate "computer" on login.

---

### Post by cs378 on 2006-01-05
THANKS sooo much

works great

---

