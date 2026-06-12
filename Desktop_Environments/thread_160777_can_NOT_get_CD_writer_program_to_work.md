---
title: "can NOT get CD writer program to work"
date: 2006-04-15
forum: Desktop Environments
---

### Post by wpshooter on 2006-04-15
Apparently the concept of these CD writer programs used in Ubuntu is foreign to me.

I have been trying I don't know how long to understand how these programs are supposed to function.  I just can NOT get it.

Maybe this is because I am used to using the Drag-to-Disc function of Roxio Easy Creator software in Windows.  This function of this software package makes it possible for a CD-RW to be treated just as if it were any other drive on the system, i.e. you can use the windows copy and paste functions to move files, etc. to/from another drive to the CD-RW and you can do this without having to blank or erase the CD-RW after every new copy process.  You can in a similar vain use the drag and drop function of windows to just click on a file, etc. and move it over to/copy to the CD-RW, and again you can do this as many times as you like just as if the CD-RW was another hard drive.  In effect, I am NOT interested in BURNING CD image files, I want the CD to function as another hard drive.

It does not appear to me that these CD writer programs I have been trying in Ubuntu have this capability.  

What good is a CD-writing process if I have to erase the CD ever time I decide I want to write/add something else to it ?

Can someone give me some DETAILED instructions on how to accomplish what I am needing to do (if it is possible) in these CD-writer programs that are available for Ubuntu.  I have tried KDE3 and GnomeBaker.

Thanks.

---

### Post by cilynx on 2006-04-15
If you're using stock Ubuntu with Gnome, when you put in a blank CD, it should tell you and open up a folder that it call "CD/DVD files to be burned" or something like that.  If it doesn't open up the folder automagically, it should at least put an icon on your desktop of a blank CDR.  Click on this and it'll bring up the same folder.  You can drag and drop files there and press the burn button in the upper right corner to burn them from there.  In all honesty, it's very similar to the built in burning function of WinXP.  That's the closest I know of to what you're asking for.

---

### Post by wpshooter on 2006-04-15
When I do what you describe, and the next time I try to copy some more files to the CD it comes back with an error saying that I can not write to the CD because it is read-only.  And what it is wanting me to do is to ERASE everything that I just copied to the CD before it will allow me to write to it AGAIN.

When I go in to look at the permissions of the CD rom drive the write boxes are NOT checked, but when I try to check them this is what I get:

**Couldn't change the permissions of "cdrom0" because it is on a read-only disk**

I know for a fact that this drive is capable of writing to CD-RW's (because I do it in Windows using Roxio all of the time - it is a Plextor 40/12/40A model drive) and I know that the CD that I have in the drive IS a CD-RW.

Is there anyone out there that has used the DRAG-TO-DISC function of Roxio's Easy CD Creator program that knows what I am talking about (please see my original post) ???

Thanks.

---

### Post by cilynx on 2006-04-16
I think you're looking for multisession mode.  I'm drawing at straws here (never felt a need for cdrw when I have USB stick), but have you tried gcombust?  There's a package in the universe repository.

[http://www.abo.fi/~jmunsin/gcombust/]("http://www.abo.fi/~jmunsin/gcombust/")

---

### Post by 146lily on 2006-04-16
**[COLOR="Red"]K3b is the best![/COLOR]**

Ex-windows users will love k3b, its like nero but better! It will run fine under gnome only it will take time to download due to to needing kde files. After downloading check configuration for helper programs like vcdimager and then download the missing ones. Then use k3b setup to ensure the correct permissions.

---

### Post by wpshooter on 2006-04-17
[QUOTE=146lily]**[COLOR="Red"]K3b is the best![/COLOR]**

Ex-windows users will love k3b, its like nero but better! It will run fine under gnome only it will take time to download due to to needing kde files. After downloading check configuration for helper programs like vcdimager and then download the missing ones. Then use k3b setup to ensure the correct permissions.[/QUOTE]

Well I think I finally figured out how to use the K3b program.

But I must say it is a VERY slow file copying process when compared to Roxio's DRAG-TO-DISC function of their Easy CD Creator program.

Then one more question.  When I place the CD that has been written to by the K3B program back into the machine, I get a popup menu from the CD writing program which is apparently written into the Ubuntu system by default, something called CD/DVD Creator.  Since I am going to use the K3B program, do I need this CD/DVD Creator program and should it and can it be UNINSTALLED ?  And if so, how do I uninstall it ?  I don't see it listed in the listing of programs that are checked as having been installed.

Thanks.

---

### Post by cilynx on 2006-04-17
The CD/DVD Creator is built into Nautilus (the shell / file manager for Gnome).  You can't uninstall it, but you can disable it under System->Preferences->Removable Drives and Media

---

### Post by wpshooter on 2006-04-17
Thanks, I will see if I can find it when I get home.

---

