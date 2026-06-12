---
title: "running files over a network"
date: 2005-04-27
forum: Desktop Environments
---

### Post by theonewhoismany on 2005-04-27
is it possible to run file over a network in ubuntu?

presently i have to copy the files locally in order to open them. and as you can imagine this is a somewhat tedious task especially over 802.11b.

thanks

---

### Post by ape on 2005-04-27
I may be misunderstanding your question, but in order to run the file across the network it still must be copied (in a way) in order to run on your machine.  When you execute the file across the network, the bits are copied over to load into your memory.

What type of file are you talking about and what size is it?

There are ways to run certain executables on the remote machine and have the display sent back to your machine.  Is this what you are wanting to do?

---

### Post by theonewhoismany on 2005-04-27
[QUOTE=ape]I may be misunderstanding your question, but in order to run the file across the network it still must be copied (in a way) in order to run on your machine.  When you execute the file across the network, the bits are copied over to load into your memory.

What type of file are you talking about and what size is it?

There are ways to run certain executables on the remote machine and have the display sent back to your machine.  Is this what you are wanting to do?[/QUOTE]

sorry, my english not so good.

i mean say for example i want to run an xvid file off one of my file servers. everytime i try to access the file it mplayer tells me that it can not find the file in question, I get the same problem in open office when i try and execute a .doc file for example across the not work.

it says:

error loading document
file:///home/user/smb://server/folder/document.doc
does not exist

yet the file does exist i can open it if i copy it across and have it on the local machines hard drive then open it but it makes life harder and consumes time

---

### Post by ape on 2005-04-27
Hmm. I see what you mean.  If I connect through Nautilus to the SMB share, I can see the file, copy it, but not use the associated application by clicking on the icon.

If I mount the share using the command 'sudo mount -t smbfs -o username=xxxx,password=xxxx //server/share /mountpoint',  then I can access it through the filesystem and successfully open the file.  This may be a workaround for you for now.  

There definitely seems to be something with Nautilus and SMB file associations.

Just did some more tests using Nautius and with files like .doc and .xls and the issue here seems to be how the file location is being passed into OpenOffice.  .pdf files just don't want to open up at all.  On the other hand, clicking on .jpg and .bmp files opens them okay as well as .html files and .txt files are opened with the appropriate program.

The acutal mounting of the smb file system using the mount command seems to be the best way to go in this situation.

By the way, your English is fine!

---

### Post by vermeersch on 2005-04-27
got the same problem in thread:

[http://ubuntuforums.org/showthread.php?t=28451](http://ubuntuforums.org/showthread.php?t=28451)

I installed kde and tried with Konqueror: could not open .doc, but pdf and even .xls went fine!
In nautilus, neither of these files opens 
So the prob is not limited to nautilus/gnome : Konqueror KDE gives similar results 

Is this a bug? How come it was not detected during test period? Seems a very important issue to me and a reason to switch to other distro.

---

### Post by vermeersch on 2005-04-28
???

---

### Post by nocturn on 2005-04-28
The cause is easy.  Gnome has VFS (virtual file system) to access files on any supported protocol (such as smb:// ssh://).  KDE has IOslaves for this.

All apps that support the VFS or the IOslaves can access whatever nautilus and konq can.  But some apps (like OO, mplayer, xmms) do not use that middle layer.  As such, they do not see the files (and do not recognize paths like smb://server/mp3.mp3).

---

### Post by vermeersch on 2005-04-30
If this is  the reason, then why does OO see and open files on other network-PC through gnome/nautilus in mandrake and not in Ubuntu?

---

### Post by vermeersch on 2005-05-01
???

---

### Post by kjkrum on 2005-09-07
Same problem here... running Warty and trying to access shares on a NT domain.

Five months later and it's still broken.  This certainly doesn't make Ubuntu look good at the office.

---

