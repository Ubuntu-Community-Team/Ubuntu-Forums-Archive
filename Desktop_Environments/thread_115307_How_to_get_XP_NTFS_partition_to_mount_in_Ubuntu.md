---
title: "How to get XP NTFS partition to mount in Ubuntu?"
date: 2006-01-10
forum: Desktop Environments
---

### Post by myke on 2006-01-10
Howdy.  Everything going good.   Everyone's helped out well so far especially with my wifi issues and network manager and gtkwifi are both good solutions.  My new question is the above.  How do I get my XP partition to mount and show up in Ubuntu?  It never has since my original installation.  I'd like to move some files over from the XP drive without having to boot XP up and burn them to cd first.  It would be a lot easier to do have each partition to recognize the other but even booting in XP doesn't see a recognition of the Linux partition.  How do I fix this?

Oh ... one other separate thing real quick.  I've noticed than when I want to access folders in the drive many of the are root access only as that is who the owner is.  Being able to access the /usr/share folder as my primary login would be most helpful.  Is there anyway to chmod the entire share folder and everything in it to being owned by the primary login user instead of root?  The only way I've figured out how to do it so far is one folder at a time which is very tedious.

---

### Post by bagel on 2006-01-10
Sorry-Double Posted. Please delete.

---

### Post by bagel on 2006-01-10
Hello there;

This [link]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions") deals with mounting WinXP partitions in Ubuntu. 

```
chmod -R
``` tells chmod to process the directory recursivly. So all subdirecotires and files in them also get chmodded.

Ciao, bagel

---

### Post by bikeman on 2006-01-10
Hi, welcome to Ubuntu!  I am a relative newbie also, but have had real good results with the unofficial ubuntu guide at [http://ubuntuguide.squarecows.com/doku.php]("http://ubuntuguide.squarecows.com/doku.php")

This is from that guide:
For the NTFS question, first list your partition tables so you know where the NTFS partition is:
Type(in the terminal):  sudo fdisk -l
note the location for the next step

How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?
e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) Local mount folder: /media/windows

Type(in the terminal):

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

This opens the fstab file in the text editor.
Append the following line at the end of file:

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Save the edited file, don't change the name.

The NTFS drive should be mounted (read-only in Linux) when you re-boot, and you can copy files to your Linux drive.

Windows does not recognize Linus partitions.  If you want to have files in a place where both OS's can read and write, create a FAT partition and put your files there.  Both OS's can read and write to FAT.

As for the second part, rather than changing the permission (which decreases security), there is a way that you can browse the file system as root.  I'll refer you to the unofficial guide above for instructions. ;) 

Daniel

---

### Post by cassiuss on 2006-01-10
Thanks bikeman - this worked perfectly for me. Quick and easy solution!

---

### Post by myke on 2006-01-10
Thanks to both of you ... Bagel & Bikeman.  Both the wiki and the ubuntuguide were quite helpful.  I used the wiki instructions and got the xp partition mounted in like 30 seconds.  I think the ubuntuguide site will be very helpful for lots of stuff.

---

