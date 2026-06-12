---
title: "UDF DVD mount error"
date: 2006-06-12
forum: Desktop Environments
---

### Post by sopo_dan on 2006-06-12
I have lots of DVD's burned in Windows using Nero, as DVD UDF
When i insert one of those and 2xclick on the drive icon under "Computer" i get this message:
```
mount: block device /dev/hda is write-protected, mounting read-only 
mount: wrong fs type, bad option, bad superblock on /dev/hda, 
       missing codepage or other error 
       in some cases useful info is found in syslog - try 
       dmesg | tail  or so
``` 
But if i do "sudo mount -t udf /dev/hda /media/cdrom0" it works just fine
My /etc/fstab entry looks like this (default):
```
/dev/hda        /media/cdrom0       udf,iso9660 user,noauto     0       0
``` 
I don't get it. UDF is specified there too. Shouldn't dynamic mounting also work for UDF disks?

---

### Post by sopo_dan on 2006-06-13
Nobody able to help here? Please

---

### Post by Fatjoint on 2006-06-13
[QUOTE=sopo_dan]I have lots of DVD's burned in Windows using Nero, as DVD UDF
When i insert one of those and 2xclick on the drive icon under "Computer" i get this message:
```
mount: block device /dev/hda is write-protected, mounting read-only 
mount: wrong fs type, bad option, bad superblock on /dev/hda, 
       missing codepage or other error 
       in some cases useful info is found in syslog - try 
       dmesg | tail  or so
``` 
But if i do "sudo mount -t udf /dev/hda /media/cdrom0" it works just fine
My /etc/fstab entry looks like this (default):
```
/dev/hda        /media/cdrom0       udf,iso9660 user,noauto     0       0
``` 
I don't get it. UDF is specified there too. Shouldn't automounting work?
[/QUOTE]


Aren't you specifying in your fstab as to NOT automount?

[edit] sorry - no, that's not it - i'm being stupid.  The noauto argument is just stating that you won't mount it at boot time.

It is interesting to note in the example under **man mount** that the argument is explicitly comma seperated.  This is directly quoted from it:

> 

(iii)  Normally,  only  the superuser can mount file systems.  However,
       when fstab contains the user option on a line, anybody  can  mount  the
       corresponding system.

       Thus, given a line
              /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide
       any user can mount the iso9660 file system found on his CDROM using the
       command
              mount /dev/cdrom
       or
              mount /cd



Is this a bug?  I noted the same thing in my fstab and I'm having CDROM issues also...

---

### Post by sopo_dan on 2006-06-13
The thing is (and i forgot to specify this) this issue only occurs with UDF disks for me. ISO9660 ones work just as they should - insert the disk & it gets automounted.

---

### Post by sopo_dan on 2006-06-16
I'm sorry to bring this up again, but i can't believe that none of you "enlightened minds" around here can make a suggestion on the issue.
Maybe this helps: I tried removing "ISO9660" from the line in /etc/fstab and with that done UDF disks work fine, but on the other hand I have to manually mount ISO ones... so the problem still isn't solved. 
Why won't both work, if ISO as well as UDF is stated in fstab? :(

---

### Post by scxtt on 2006-06-16
what about lines like this:```

/dev/hda        /media/cdrom0       udf     user,noauto     0       0
/dev/hda        /media/cdrom0       iso9660 user,noauto     0       0

note: both in /etc/fstab @ the same time
```disclaimer: i have no idea if that will make a difference, even work, or just piss ubuntu off ...

---

### Post by sopo_dan on 2006-06-16
Just tried that. It won't do anything bad, but it doesn't work either. 
If I put the line with UDF first, only UDF disks will dynamically mount/umount. If I put the ISO9660 line first only those will.

---

### Post by sopo_dan on 2006-06-16
LOL, this is freaky!
I've done some more reading through the man page for mount, but haven't gotten any smarter out of it, so I thought I'd try "experimenting"
So, as i stated in the original post, my /etc/fstab line used to read:
```
 /dev/hda        /media/cdrom0       udf,iso9660 user,noauto     0       0
``` I changed it to:
```
 /dev/hda        /media/cdrom0       iso9660,udf user,noauto     0       0
``` and now both fs types work fine (pop in the disk and it gets mounted)

Now I'm glad it works, but I sure would like to understand why? The man page says when mount command is issued and more than one fs type is specified they are probed for in the specified order. So why when UDF is first, exactly UDF disks are the ones which won't mount, but when it is last both work? This shouldn't even matter for the given scenario, as UDF disks can't mount as ISO, and vice-versa. They shouldn't interfere with each other.
Anyway, thanks **scxtt**, it was your suggestion that made me try out different cominations.

---

### Post by scxtt on 2006-06-16
maybe it only likes alphabetical order :p ... that is strange, i've not done any experimenting w/ UDF, so i haven't spent time w/ it ...

glad to hear it works tho ...

---

### Post by hangfire on 2006-06-18
[QUOTE=scxtt]maybe it only likes alphabetical order :p ... that is strange, i've not done any experimenting w/ UDF, so i haven't spent time w/ it ...

glad to hear it works tho ...[/QUOTE]

I have the same problem, however the manual mount doesn't work, nor does changing the order in /etc/fstab.

The  DVD-ROM is my Kubuntu 6.06 install ISO, burned with Nero 5.5.

[B]$ sudo mount -t udf /dev/hdc /media/cdrom0
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

and from dmesg:

[B][4307261.071000] hdc: packet command error: status=0x51 { DriveReady SeekComplet
e Error }
[4307261.071000] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[4307261.071000] ide: failed opcode was: unknown
[4307261.072000] cdrom: failed setting lba address space
[4307262.230000] UDF-fs: No VRS found


[/B]
Edit- I just checked the checksum on my Kubuntu DVD 6.06 install ISO image, that's OK, and I reburned on another brand disk, minus instead of plus, at 2.4x instead of 4x, same problem. Funny thing, I installed Dapper from this disk, however I did have to go to text mode, it locked up on "Loading Kernel" in graphics mode.

---

### Post by scxtt on 2006-06-18
did you do a google search on "UDF-fs: No VRS found"? -- i saw a suggestion that said to remove the entry for your DVD-ROM in /etc/fstab and try mounting it manually ...

---

### Post by vr6stress on 2006-06-19
[QUOTE=sopo_dan]LOL, this is freaky!
I've done some more reading through the man page for mount, but haven't gotten any smarter out of it, so I thought I'd try "experimenting"
So, as i stated in the original post, my /etc/fstab line used to read:
```
 /dev/hda        /media/cdrom0       udf,iso9660 user,noauto     0       0
``` I changed it to:
```
 /dev/hda        /media/cdrom0       iso9660,udf user,noauto     0       0
``` and now both fs types work fine (pop in the disk and it gets mounted)
[/QUOTE]

WOW! i had this same exact problem - i think it showed up after i installed a kernel that enabled my core duo...

but i changed my fstab to match yours - ie putting iso9660 before udf and once i logged back in - there's the dvd sitting on my desktop...and it loads up just fine...

man - did anyone let anyone know that maybe there's a bug in there and that udf has to go second?

thanks for the tip though - made my lunch hour...hahaha

---

### Post by hangfire on 2006-06-20
[QUOTE=scxtt]did you do a google search on "UDF-fs: No VRS found"? -- i saw a suggestion that said to remove the entry for your DVD-ROM in /etc/fstab and try mounting it manually ...[/QUOTE]

Yes, thanks, I tried that, no effect, even after a reboot. dmesg errors are exactly the same.

HF

---

### Post by BungaMan on 2006-06-20
did you try the novrs option?

Actually I have the same problem that it cannot mount as UDF.  Switching the parameters in fstab does not work and manually mounting doesn't work either.  Manual mounting does work if I specify ISO9660 as file system.  But then of course I'm only able to see the ISO9660 content which contains an autorun.inf and a UDF driver for windows.  So yes the CD exists out of 2 file systems.  Google results in nothing but links to manpages of mount :(

Anyone an idea how to mount cd's with more than one file system?

---

### Post by hangfire on 2006-06-20
[QUOTE=BungaMan]did you try the novrs option?[/QUOTE]

Tried it, to no avail, but....

[QUOTE=BungaMan]Manual mounting does work if I specify ISO9660 as file system.  But then of course I'm only able to see the ISO9660 content which contains an autorun.inf and a UDF driver for windows.[/QUOTE]

Curiously, this works for me, and I see the entire contents of the system. I strongly suspect it depends on the way the DVD was burned, in my case a stock Nero 5.5 without updates.

Now, I can run Synaptic and get all the packages I couldn't ask for during the text install, and not have to wait for the net download. Woohoo!

HF

---

### Post by sopo_dan on 2006-06-20
@vr6stress: glad it helped... this drove me nuts for days 

@hangfire: the ubuntu/kubuntu disks aren't UDF, they are ISO images, that's why they won't mount with "-t UDF" option

---

### Post by sopo_dan on 2006-06-22
well i have filed this at lauchpad. it is bug [#50640]("https://launchpad.net/distros/ubuntu/+source/util-linux/+bug/50640")[URL="https://launchpad.net/distros/ubuntu/+source/util-linux/+bug/50640"]
[/URL]

---

### Post by kung_pow on 2008-02-22
I'm new to Ubuntu and have only used a tiny amount of unix/linux. I just installed version 7.10 and am also having problems with udf. Switching the order of iso9660 and udf does not work, or just using auto or does using udf only in the fstab. 

Here's the fstab.

```
/dev/hda        /media/cdrom0  udf,iso9660 user,noauto,exec 0       0
```

Here's the message after trying to mount:

mount: block device /dev/hda is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And here's the dmesg:

[ 4665.980000] UDF-fs: No VRS found
[ 4758.216000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4758.252000] ISO 9660 Extensions: RRIP_1991A
[ 4858.648000] UDF-fs: No partition found (1)
[ 4958.128000] atkbd.c: Unknown key pressed (translated set 2, code 0xb3 on isa0060/serio0).
[ 4958.128000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[ 4958.208000] atkbd.c: Unknown key released (translated set 2, code 0xb3 on isa0060/serio0).
[ 4958.208000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[ 5091.676000] UDF-fs: No partition found (1)
[ 7616.052000] UDF-fs: No partition found (1)

Have I said to much? This forum is great. Thank you.

---

### Post by dangermouse28 on 2008-03-14
Kung_pow - try using a cd/dvd lens cleaner.

Was having similar probs with my laptop (bought off ebay and well used) and a cleaner sorted it out.

It's worth a try!

---

### Post by diabolustheslayer on 2008-04-18
Hi, i'm having problems with the same thing, but as i'm a total ignorant in linux i don't even know if i copied the codes in the right place, i had hard time finding out what the "terminal" was. I can't open the CD's and DVD's i recorded with windows, the thing is that i can perfectly open dvd movies and other cd's i recorded with ubuntu, and i can perfectly record new dvd's, so i guess is not a hardware problem. Please tell me what did i do wrong according to the text below. is it 'cos i totally erased windows when i installed ubuntu? thanks.


diabolus@MOTORHEAD:~$ sudo mount -t udf /dev/hda /media/cdrom0
[sudo] password for diabolus:
mount: special device /dev/hda does not exist
diabolus@MOTORHEAD:~$ /dev/hda        /media/cdrom0       udf,iso9660 user,noauto     0       0
bash: /dev/hda: No such file or directory
diabolus@MOTORHEAD:~$ mount /dev/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

diabolus@MOTORHEAD:~$ mount /cd
mount: can't find /cd in /etc/fstab or /etc/mtab
diabolus@MOTORHEAD:~$ /dev/hda        /media/cdrom0       udf,iso9660 user,noauto     0       0
bash: /dev/hda: No such file or directory
diabolus@MOTORHEAD:~$ /dev/hda        /media/cdrom0       iso9660,udf user,noauto     0       0
bash: /dev/hda: No such file or directory

---

### Post by diabolustheslayer on 2008-04-18
If the problem is that i erased windows and that's why it won't open windows cd's; how can i install windows from ubuntu? I'm really sorry if my questions seem stupid to you, i just wanna learn and i don't really know what to look for.

---

