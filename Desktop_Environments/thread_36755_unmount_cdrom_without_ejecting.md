---
title: "unmount cdrom without ejecting?"
date: 2005-05-24
forum: Desktop Environments
---

### Post by dbloom on 2005-05-24
how do you unmount the cdrom without ejecting the cd?  i'd like to create an iso image of an audio cd, but every time i try to unmount it, the drive locks up on me.  

any thoughts?

thanks.

---

### Post by shakin on 2005-05-24
```

$ sudo umount /media/cdrom

```

---

### Post by JonahRowley on 2005-05-24
Since audio cds are not mounted, I'm not sure I understand the question.  What exactly are you trying to do?

If a process is still using a file on a mounted CD, the unmount will fail.  To see if there are any processes using files on your CD, look at the **fuser** and **lsof** commands.

---

### Post by dbloom on 2005-05-24
thanks for your replies.  i was trying to create an iso image of an audio cd so i can burn it later when i pick up some cdr's.  

i was following the thread [here](http://www.ubuntuforums.org/showthread.php?t=6509). it does mention selecting the "unmount" option from the shell, which i can't find -- i presume i'm looking in the wrong place.

shakin, i tried 'sudo umount', but that's how i end up locking the cdrom.

JonahRowley, since the audio cd icon appeared (on the desktop) when the cd was inserted, i assumed it was mounted.  i will check out those commands you mentioned tonight when i get home.   

thx.

---

### Post by JonahRowley on 2005-05-24
Come to think of it, I did have this same problem.  The file alteration monitor (gamin?) wouldn't let go of my (not audio, data) cdrom.  I had to killall gamas to get it back.

---

### Post by Takis on 2005-05-24
[QUOTE=dbloom] since the audio cd icon appeared (on the desktop) when the cd was inserted, i assumed it was mounted.  i will check out those commands you mentioned tonight when i get home.[/QUOTE]

When the icon appeared, did it have that little green triangle on it? The triangle designates that the device represented is mounted. It's very obvious and you'll recognise it for what it is straight away. If it's not there, though (which is highly likely because you can't mount an audio cd) then you're trying to umount something that isn't mounted, and it might be what's making things go funny. Have a look for that green triangle. 

Actually, I just managed to find pics on Google.
Unmounted:
[IMG]http://www.skolelinux.org/images/skoleknoppix/icons/cdrom_unmount.png[/IMG]
Mounted:
[IMG]http://www.abuledu.org/IMG/png/cdrom_mount.png[/IMG]

---

### Post by dbloom on 2005-05-24
There's no green arrow and when i try umount i get an error that the drive isn't mounted, which is what you guys have been telling me...

so i tried this:  
```
dd if=/dev/audio of=cd.iso
``` 

'/dev/cdrom' and '/media/cdrom' didn't seem to work for me.  well, after 2.5 hours and only 52MB copied so i gave up.  is there another way to create an image of an audio cd that i can burn later?  

thanks.

---

### Post by Takis on 2005-05-24
Is it an IDE cdrom (most tend to be)?
What happens if you try ```
dd if=/dev/hdc of=cd.iso
```

?

---

### Post by dbloom on 2005-05-24
it is /dev/hdc, but this is the message i get:

```
dd: reading `/dev/hdc': Input/output error
0+0 records in
0+0 records out
0 bytes transferred in 0.004478 seconds (0 bytes/sec)
```

---

### Post by JonahRowley on 2005-05-24
No, **/dev/audio** is your sound card, you don't want that.  If you want to extract the audio, I don't think Linux has a device for that.  I remember FreeBSD had devices for each audio track, from which you could extract the raw pcm data.  Look at tools like **cdparanoia** for that.

And no, you don't "mount" audio cds.  You only mount data cds.  That's why you can't mount it.  Be careful though, some cds are mixed, meaning that have both audio and data tracks.  Those can (and may be automatically) mounted.

---

### Post by RastaMahata on 2005-05-24
[QUOTE=dbloom]how do you unmount the cdrom without ejecting the cd?  i'd like to create an iso image of an audio cd, but every time i try to unmount it, the drive locks up on me.  

any thoughts?

thanks.[/QUOTE]
 why dont you get greaveman (sudo apt-get graveman)?
Then you can "copy a cd" into an image :P

---

### Post by dbloom on 2005-05-24
thanks for the suggestion.  i installed it, but couldn't get it to "see" the audio files on the disc. 

i'll try again tomorrow -- it's getting late.

thx again though.

............

well, i tried again.  same issue.  in fact, it doesn't seem to acknowledge that an audio cd is even in the drive yet i can play the cd in every audio player i have installed (which is about 4, i think... kind of excessive...).  trying "duplicate cd" doesn't work either -- i can't find files on the cd, which i suppose makes sense because i can't mount it...  

this seems like such a simple task -- the easy thing to do is just buy some cdr's, but i really want to accomplish this first.  i just can't give up...

---

### Post by dbloom on 2005-05-25
JonahRowley, i somehow missed your post last night.  thx.  

i wonder, would it be possible to extract data into FLAC files with SoundJuicer and then burning them to a disc later using GnomeBaker?  it seems GB can create audio cd's from files, but i don't know whether FLAC files are possible...  or maybe there's another "lossless" format i could use with SJ..?

thx.

---

### Post by pappo on 2005-05-25
For what you want to do, which I think was to save away an audio cd, and then put it on CDR's later, you could do this:

1.  Install ripperx using synaptic.  It is in Ubuntu universe.  It will rip all the audio tracks off your audio cd to a directory of your choosing.

2.  Later, use k3b (also available using synaptic), and create an audio cdr from the directory of files you saved with ripperx.

Good luck

---

