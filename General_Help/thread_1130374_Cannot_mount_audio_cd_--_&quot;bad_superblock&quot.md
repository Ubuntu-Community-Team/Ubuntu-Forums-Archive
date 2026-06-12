---
title: "Cannot mount audio cd -- &quot;bad superblock&quot;"
date: 2009-04-19
forum: General Help
---

### Post by oleander on 2009-04-19
I put in an audio cd last night to listen to it but it wouldn't play. At first I thought it might be the audio player but it wasn't. When trying to mount the cd, I get this output:

```
oleander@xubuntu:~$ sudo mount /dev/scd0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

After "dmesg | tail" I get this:
```
oleander@xubuntu:~$ dmesg | tail
[ 2183.868811] end_request: I/O error, dev sr0, sector 1091912
[ 2183.872189] end_request: I/O error, dev sr0, sector 1093152
[ 2183.875641] end_request: I/O error, dev sr0, sector 1091904
[ 2183.880430] end_request: I/O error, dev sr0, sector 1248
[ 2183.883818] end_request: I/O error, dev sr0, sector 2496
[ 2183.887127] end_request: I/O error, dev sr0, sector 1248
[ 2183.890566] end_request: I/O error, dev sr0, sector 2496
[ 2183.890886] UDF-fs: No partition found (1)
[ 2183.961843] end_request: I/O error, dev sr0, sector 64
[ 2183.962175] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```

I know there have been other posts about this and I have checked them -- but my fstab file doesn't have codepage references in it that the other users had problems with. Here is the fstab line:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,rw 0       0

```

I'm not experienced enough to see how to solve the problem. Any suggestions would be very much appreciated. Thanks ahead of time. :D

~Oleander

---

### Post by oleander on 2009-04-20
Does anyone have any ideas, or should I just file a bug report?

---

### Post by zman58 on 2009-04-21
Can you mount ANY audio CDs and listen to them?
Can you mount a data CD and access it?
Is it possible that the audio CD you are mounting is scratched, greasy, or dirty?

If the Audio CD was burned on another CD RW, then it may not be "reliably" readable on the CD reader you are using. I have seen this problem before with newer media on older readers.

Anyway, I would first suspect the media. Get another media to confirm.

If you can, try substituting another CD reader temporarily to verify that the problem is not the reader. Of course if you have a laptop that won't be so easy to do.

---

### Post by oleander on 2009-04-21
I tried another audio cd and got a strange result...after doing
```
sudo mount /dev/scd0
```
I opened /media/cdrom to find AUTORUN.INF and SETUP.EXE -- it was an audio cd?? Maybe that was DRM software? The cd was "Beautiful Garbage" from the band "Garbage." I tried a CD-R that I burned myself (using Ubuntu) and got this
```
sudo mount /dev/scd0
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The audio cd that I burned had some scratches but the initial audio cd that I had tried was spotless -- not one single scratch or visible dust on it. Neither of the audio cds that I got the "bad superblock" error with were CD-RW because one I burned myself (it clearly says CD-R) and the other I bought with a bunch of language cds and a book (companies usually don't package CD-RWs because of playback issues).

I do have the cd/dvd decryption packages installed, so I doubt that it's encrypted and it can't be the drive because on my other partition, I have Windows Vista and I got the same audio cds to work with Vista. Oh, and I don't remember having any trouble with data cds.

Strange, huh?

~Oleander

---

### Post by raptor2552 on 2009-04-21
Adding the utf8 character set to your cdrom may help

change your fstab entry:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,rw 0       0

to:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,rw,utf8 0       0

It may be were the codepage fault is coming from

---

### Post by oleander on 2009-04-22
Thanks for the suggestion, I tried it, but got this:
```
sudo mount /dev/scd0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

At this point, ](*,) I'm thinking that it must be some sort of bug. I'll have to submit a bug report.

P.S. - Raptor2552, the bird that you're using as your avatar is really amazing! 

Thanks for all your help, everyone. :)

---

### Post by mc4man on 2009-04-22
That 'error' message is correct, actually it's indicating that media has been recognized on the drive.

You cannot mount an audio cd, media is not mounted, only the filesystem on it is and audio cd's don't contain one.

Audio cd's are accessed at a location, for hardy onward it would be ~/.gvfs/cdda mount on scd[COLOR="Red"]x[/COLOR] (0 in your case

That's not to say you may not have a problem elsewhere, put an audio cd in, navigate to the above location and see if the contents are visible

---

### Post by oleander on 2009-04-23
Mc4man, thanks for your reply. After doing some research on gvfs, I found out a lot about Linux that I never knew. I have had no formal instruction on Linux nor have I ever used audio cds with my computer so I never knew how differently Linux treats them (as compared to Windows). 

It seems that the problem I encountered was not the cd or the drive but the very fact that I was trying to mount it. I had also assumed that the multimedia programs I had already installed would play audio cds but Rhythmbox didn't seem to register the cd. After installing "goobox" I could play the cd just fine.

Thanks again everyone! :D
Oleander

...off to mark the thread as [SOLVED]

---

