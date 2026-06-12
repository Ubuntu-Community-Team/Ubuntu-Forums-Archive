---
title: "With or without dmg2iso"
date: 2006-02-24
forum: Desktop Environments
---

### Post by Luke771 on 2006-02-24
Hi
I downloaded a .dmg file because no .iso image was available, but now I can't convert it to .iso. I'm not intrested in burning the .dmg image itself, all I want is to convert it to .iso and mount it. Mounting the .dmg without converting anything would do just as fine, as long as it works; I tried ```
 mount -o loop -t hfsplus filename.dmg /mountingpoint 
``` 

And got the output:> mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

On the she same page where I found the line to mount .dmg images under Linux ( [http://www.mode-x.com/wiki/index.php/Linux:_Tips_&_Tricks](http://www.mode-x.com/wiki/index.php/Linux:_Tips_&_Tricks) ) reads> Ensure that the following are set in your kernel config:

 CONFIG_HFS_FS=m
 CONFIG_HFSPLUS_FS=m


But I don't know how to do that.
Actually, I dont even know if mounting .dmg images can be done under Ubuntu in the first place, and I have read only one article about that being possible, so far.

An intresting Google result, coming up quite often actually, was that renaming your filename.dmg to filename.iso will do the trick; that would be enough to change your .dmg file a perfectly "mountable" .iso image, I was skeptic from the start about this one but I tried anyway. Didnt work of course. 

I downloaded an application called dmg2iso but I dont know how to use it: I tried the line I found on the download site ```
dmg2iso.pl filename.dmg filename.iso
```

Which gave me the output "command not found"; dmg2iso.pl is in the root directory, I tried both adding "sudo" before the line and logging in as root: neither one worked.

The problem could be that I only downloaded the file dmg2iso.pl to root directory whithout doing anything else with that file before trying to run the commands. Perl base is installed. I've been trying to google this for hours but I'm not getting much, hope is getting thinner, so I'm posting this hoping that someone will read it and try to help me.
Thanks to all the "helpers"

---

### Post by taurus on 2006-02-24
Try

chmod 755 dmg2iso.pl
./dmg2iso.pl filename.dmg filename.iso

---

### Post by Luke771 on 2006-02-25
Output:
> bash: /usr/local/bin/dmg2iso.pl: /usr/local/bin/perl^M: bad interpreter: No such file or directory


---

### Post by taurus on 2006-02-25
See where perl is on your system (or if you even have it).  Apparently, that file thinks perl is in /usr/loca/bin but I think perl is in /usr/bin.  Run this command to find out for sure and then edit your /usr/local/bin/dmg2iso.pl for the correct path to perl,

whereis perl

---

### Post by Luke771 on 2006-02-26
Thanks.
I think I did it some way, but I had to ...cheat :-D

First I tried something very similar to the last suggestion, i.e. I checked if I actually had perl installed, then I tried moving both the file to be converted and the script itself to the directory shown in the error output, but that didn't do the trick.
My google searches showed a number of Windows user running dmg2iso without any problems, so I downloaded the windows version to the directory where the file to be converted is stored, and used the command line[code]wine dmg2iso.exe filename.dmg filename.iso[code]
and it looks good so far; it's not done yet but it's working

---

### Post by ed_agamemnon on 2006-03-09
I'm trying the same thing as you and am stuck with a .dmg I can't convert. 

I wanted to take a look inside the new Mac OS X native installer for Starcraft and see if it was *nix enough to be converted for Linux (chances are that's it's not...)

The Perl method won't work for me because I'm missing a ton of modules and I honestly can't be bothered to faf about for hours downloading them from CPAN.

The Wine idea was a great one, so:

```
~/Desktop$ wine dmg2iso.exe StarCraft_OS_X_Installer.dmg StarInst.iso
dmg2iso v0.2c by vu1tur (vu1tur@gmx.de)

reading property list...ok
found 4 partitions
decompressing:
partition 0...ok
partition 1...ok
partition 2...ok
partition 3...ok

conversion successful

```

Looks good... but the resulting .ISO won't open (either under Nautilus or Archive Manager). Interestingly enough, the .dmg is 9.3MB and the created .iso is 12.2MB. Anyway. Can't really make any more progress: stuck.

If anyone can help that'd be great (the Mac OS X Starcraft installed can be downloaded from [here]("http://www.blizzard.com/support/?id=msc0411p")

Interestingly the output from the 'file' command on the .dmg is...

```
StarCraft_OS_X_Installer.dmg: VAX COFF executable not stripped - version 376

```

... and on the new .iso is:

```
StarInst.iso: Apple Partition data block size: 512, first type: Apple_partition_map, name: Apple, number of blocks: 63, second type: Apple_HFS, name: disk image, number of blocks: 24984,

```

-weird that it ends in a ',' [comma] too.

---

### Post by Larrxi on 2007-09-09
After converting the dmg image to an iso you have to run the following command:
mount -o loop -t hfsplus  StarInst.iso /media/cdrom

Atleast it works for me.

---

### Post by zmjjmz on 2007-09-18
I tried using the .exe version of dmg2iso, but whenever i run it, i get this
```
reading property list...ok
found 4 partitions
decompressing:
partition0...ok
partition1...ERROR: Inflation failed
```
It happened with all the .dmgs I tried...

---

### Post by el.motar on 2007-10-29
I run across this post as I was having some difficulties with the dmg file format.
Was getting all the usual problems with the perl path.
My solution was to download the java version from the [http://vu1tur.eu.org/tools/](http://vu1tur.eu.org/tools/).
Just follow the java link.


[http://hem.bredband.net/catacombae/index2.html](http://hem.bredband.net/catacombae/index2.html)

I got the dmgextrator zip, unzip it and run the dmgx.sh image.dmg image.iso.

Worked really well.

Hope its of some help.

ATB

---

### Post by Tech^CF on 2007-10-31
The JAVA version el.motar linked to worked great. Seems like the perl script wasn't too happy with very large (6.5GB+) or newer DMG files. JAVA version ran great and had a nice GUI.

Thanks!

---

