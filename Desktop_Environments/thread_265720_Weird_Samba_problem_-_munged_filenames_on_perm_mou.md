---
title: "Weird Samba problem - munged filenames on perm mounted Samba share"
date: 2006-09-26
forum: Desktop Environments
---

### Post by dwasifar on 2006-09-26
Some background: I have been running Ubuntu for a while as a combination file server and desktop.  I decided to split the server functions out to a separate machine.  I moved the storage drive into the new machine, set up Samba shares like the ones I had on the original machine, and the Windows boxes on the network work fine.  However, I now need to connect to those shares from the K/Ubuntu desktop as well, and I have run into a weird problem.  Filenames that look fine from the Windows boxes, and from within Konqueror if you connect to them manually, come across wrong if the Samba share is mounted permanently in /etc/fstab.

Here is /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.0.25/mp3  /remote/mp3  smbfs  iocharset=utf8,codepage=unicode,unicode,dmask=777,fmask=777  0  0
//192.168.0.25/misc /remote/misc  smbfs  iocharset=utf8,codepage=unicode,unicode,dmask=777,fmask=777  0  0

You can see that the mount points are within the /remote folder.  If I go to smb://192.168.0.25/mp3 through Konqueror, everything looks normal.  But if I go to /remote/mp3 and look at the same files, some of the filenames are not right.  Most are fine, but a few are not.  For instance, in a certain directory containing nine mp3s, I have one file which shows up with the extension .mp:x33 instead of .mp3.  Looking at that directory through smb://192.168.0.25/mp3 shows me the file with the correct extension.  It shows up fine in Windows too.  It's just a problem when mounting the Samba share to a permanent mount point within /etc/fstab.  I added the charset and unicode options to the fstab entries to try to fix the problem, but that didn't help.

I set up the permanent mount points to give Amarok someplace to use for its home directory.  Obviously Amarok can't deal with this problem and errors out when it tries to scan the collection.  

The server is a plain-jane Ubuntu install.  The client (desktop) where I'm having the problems started life as an Ubuntu install, over which I later installed Kubuntu desktop, if that makes a difference.

(Note: if you're seeing a smiley in that extension name above, it shouldn't be there, obviously.  The characters in that extension are . m p : x 3 3)

---

### Post by dwasifar on 2006-09-26
More information:

1) It is the same in Gnome as it is in KDE.

2) I reinstalled Samba from the repositories, no help there.

3) I swapped in a HD from a different K/Ubuntu installation I was fooling around with over the weekend.  (This is one of the things I love about Linux over Windows - you can swap a drive into different hardware and stand a chance of it actually working, which it did.)  With a few tweaks to fstab, it mounted the shares without the problem. 

So there's definitely something weird with the Samba setup on the original desktop's configuration.  Can't imagine what.

---

