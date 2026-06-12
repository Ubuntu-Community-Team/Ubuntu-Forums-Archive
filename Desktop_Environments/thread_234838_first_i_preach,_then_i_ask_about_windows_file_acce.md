---
title: "first i preach, then i ask about windows file access"
date: 2006-08-12
forum: Desktop Environments
---

### Post by thepoeticdragon on 2006-08-12
hey all. i am now a proud convert into Ubuntu from Windows XP, although i had to keep my XP partition solely for Adobe Indesign CS2. anyways, i did massive googling and started with suse linux. while i got used to it, i found it tough to get things just the way i wanted them. i then tried ubuntu dapper drake, which i ended up sticking to. i find it a very pretty distro that set things up easier for me to get used to. all the system tasks are easy to find and do (under the system tab). the third party applications i found here also made many things easier to do, like installing w32codecs and other things of the sort. i'm not really aiming to be the command-line heavy linux user, but more like gui-based. i just really wanted a new environment to work in, and with ubuntu it has become possible. :D 

anyway, i have ubuntu set up with windows xp dual boot, with the windows xp on a fat32 partition. linux, on the other hand, is on reiserfs. the only files i'll really have in windows that i want to access in linux are my media , which is found in the 'my documents' windows folder. however, as i go through the windows folders and files in the linux file browser, that particular folder is locked. i want to be able to move files, music or video, in and out of there, so here's my question: how do i unlock that folder for both read and write support?

---

### Post by orb9220 on 2006-08-12
Here is mine:

/dev/hda1       /home/orb/Drives/hda1/     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/hdd1       /home/orb/Drives/hdd1/     vfat    defaults,utf8,umask=007,gid=46 0       0

The first entry gives me read access to a ntfs partiton.
The second gives me read and write to my fat32 prtition.

I also have them mounted to directories I created in my home/Drives/ area so the drives wouldn't appear on the desktop.

Also if you just want to copy files then you must run gksudo nautilus in a term then you can copy files to your hearts content.

---

### Post by thepoeticdragon on 2006-08-12
ah i see... those entries would be in the fstab file, correct? i have them now in my particular fstab after editing, however the lock image is still on my 'my documents' windows folder. the gksudo worked like a charm, however, as all lock images in the windows mount no longer showed in the browser that was opened after command prompt.

while i don't really mind using the gksudo nautilus command, i'd like for the read and write access to be available through my broswer already... were the fstab entries supposed to do that?

thank you for your response and time, btw, orb9220.

---

