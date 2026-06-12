---
title: "How do I open .dmg on linux?"
date: 2009-05-11
forum: General Help
---

### Post by Fzang on 2009-05-11
Yes, .dmg can be opened on linux despite what smart people may say :)

I tried following this guide

[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

And I wrote

```
joh@Johs-Zepto:~$ sudo mount -t hfs -o loop'/home/joh/Desktop/Alumin Fortis.dmg' /macdisk

```

And terminal gave me

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

What's wrong?

---

### Post by coffeecat on 2009-05-11
> **Fzang said:**
> ```
joh@Johs-Zepto:~$ sudo mount -t hfs -o loop'/home/joh/Desktop/Alumin Fortis.dmg' /macdisk

```....


What's wrong?

You need a space between the word loop and the ' that follows. Another way of dealing with the space in your 'Alumin Fortis.dmg' filename without using single quotes would be to escape the space with a backslash, thus:

```
sudo mount -t hfs -o loop /home/joh/Desktop/Alumin\ Fortis.dmg /macdisk
```

---

### Post by Fzang on 2009-05-11
Now I get

```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

What is this madness?? I read that linux could easily mount a disk image this way?

---

### Post by coffeecat on 2009-05-11
That's interesting - I get the same as you with a variety of .dmg files, using both "-t hfs" and "-t hfsplus". Googling brings up a number of howtos with essentially the same instructions, so I  think the issue is with the .dmg images, not the mount command, because I found this:

[http://www.linux4all.net/mounting_apple_dmg_images_on_linux](http://www.linux4all.net/mounting_apple_dmg_images_on_linux)

If the issue is the compression of the .dmg image, then that dmg2img utility might be the answer, although I haven't tried it myself.

Have you got access to a Mac. It might be easier to mount the .dmg in a Mac. I'll try it myself later from a Mac terminal and see what happens. You've intrigued me. :wink:

---

### Post by Fzang on 2009-05-11
Nope, I don't have access to a mac as such... or well, a couple in my class has a mac but I can't go around asking them to open my random .dmgs all the time :p

---

### Post by AusIV4 on 2009-05-11
I believe .dmg files can only be opened under Linux if they are not compressed or encrypted. I'm not sure how you can identify a compressed dmg though.

[Edit]
cofeecat's link already covered this (and how to decompress). Sorry about that.

---

### Post by komealy on 2009-09-18
> **coffeecat said:**
> You need a space between the word loop and the ' that follows. Another way of dealing with the space in your 'Alumin Fortis.dmg' filename without using single quotes would be to escape the space with a backslash, thus:

```
sudo mount -t hfs -o loop /home/joh/Desktop/Alumin\ Fortis.dmg /macdisk
```

An easier, well, more user friendly way to do this is to get AcetoneISO from getdeb.net and it has a convert MacOS Image option in the conversion menu that allows you to extract the dmg file to a folder.  You still can't do much with the contents though, unless they are just wallpapers or something generic.

---

### Post by bulletxt on 2009-09-19
> **komealy said:**
> An easier, well, more user friendly way to do this is to get AcetoneISO from getdeb.net and it has a convert MacOS Image option in the conversion menu that allows you to extract the dmg file to a folder.  You still can't do much with the contents though, unless they are just wallpapers or something generic.

+1 to that

---

### Post by SqRt7744 on 2010-01-19
A few of the dmg files I have downloaded have proven to be bz2 compressed, for example the ogre sdk for mac. This was easily solved: I extracted it with archive manager, then mounted it from the terminal (it was of type hfsplus)

 1. Extract with archive mounter or bunzip2 (you might want to rename the dmg to have the extension bz2 to not confuse yourself. You could also now give the extracted file the extension .hfs_image (or .dmg) for clarity.
 2. mount archive as follows:
```

 sudo mount -t hfsplus -o loop XXXXX.hfs_image /mnt

```

TADA!

---

### Post by cthlhu1987 on 2010-05-02
I dunno what to do. I have tried all the methods mentioned here in the thread and nothing worked. I tried to mount the image (with the "hfs" and the "hfsplus"-option, but it gave me the error-msg posted by Fzang), I tried acetoneiso (I gave me the "Process Error Code: 255" and the error-msg "*file name and location deleted*:The file format is invalid or unsupported."). Universal Extractor via Wine didn't even recognize the file ;(. Any other programm converted the dmg into an 1000MB big (trying converting it into bin with dmgextractor also didn't work :(), invalid file ;( ;(
But there is a happy end, 7-zip ([via Wine]("http://www.7-zip.org/download.html")) managed to open the dmg file and extract some stuff (It showed some partitions in the dmg file, I picked the biggest one with the nonsense-size of 1 GB and it was the right one).

---

### Post by afrodeity on 2010-08-11
Isn't there a tool to accomplish this, first thing in the morning, when your eyes can't focus on a terminal, and all you want to do is unpack a dmg file to look at a few icons without bothering with bash?

---

### Post by afrodeity on 2010-08-11
If I file the dmg,

it says :data

so its not hfs, what do I do?

---

### Post by keronas on 2010-10-08
you can convert the dmg file  with the dmg2img . it is available for the repository 
and then mout 
sudo mount -t hfsplus -o loop coveted.img /path

---

### Post by markh789 on 2010-10-08
> **keronas said:**
> you can convert the dmg file  with the dmg2img . it is available for the repository 
and then mout 
sudo mount -t hfsplus -o loop coveted.img /path

That's exactly it. I've been mounting a few DMG files lately. But heres how I do it:

For example:

ExampleFile.dmg
dmg2img ExampleFile.dmg
sudo mkdir /media/ExampleFile
sudo mount -t hfsplus -o loop ExampleFile.img /media/ExampleFile

When your done just use
sudo umount /media/ExampleFile/

Make sure that /media/ExampleFile is the same as the the DMG/IMG name "ExampleFile.dmg"

So if it was AnotherExample.dmg you would make /media/AnotherExample

---

### Post by PCNetSpec on 2011-02-25
Your problem may lie in the fact that you've got a hybrid disk image and you don't know where the HFS+ (or HFSX) partition starts... you'll need to convert the DMG to an IMG then do a hex dump of the IMG and search for the (known) volume header, then subtract 1024 bytes to find the partition start... and use this as an offset for your loop device.

Instructions here:
[http://linuxforums.org.uk/linux-tips-tricks/use-linux-to-install-osx-from-a-dmg-extracted-to-a-partition-without-a-mac-dvd/msg5792/#msg5792](http://linuxforums.org.uk/linux-tips-tricks/use-linux-to-install-osx-from-a-dmg-extracted-to-a-partition-without-a-mac-dvd/msg5792/#msg5792)

---

### Post by afrodeity on 2011-02-26
Thanks, I solved the problem, but now can't remember exactly how. :(

---

### Post by PCNetSpec on 2011-02-26
:) .. How many times have I done that before...

---

### Post by tarek89 on 2011-11-13
Okay i had the same problem while trying to install itunes 10.5 .dmg version i converted it with dmg2img and i have the img file. when i moount the img file it says 
```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

although i tried mounting with hfs and hfsplus

---

### Post by PCNetSpec on 2011-11-14
Got a link to the .dmg ?

---

