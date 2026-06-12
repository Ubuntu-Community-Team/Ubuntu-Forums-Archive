---
title: "Can't eject CDs except for on desktop"
date: 2005-05-22
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-22
Annoyance: I can't eject CDs using the button on my CD-rom drive.

Problem: I'm installing UT2k4 and it wants CD 2. It won't let me eject from desktop and well, I can't eject it manually. No UT2k4 makes me cry.

Solution:?

---

### Post by ola on 2005-05-22
It probably doesn't work becuase the CD is mounted.. Is there any chanse that you have a CD icon on your desctop you might be able to unmount the CD before removing it?

---

### Post by Curlydave on 2005-05-22
That's where it says its busy and refuses to eject.

---

### Post by kvidell on 2005-05-22
[QUOTE=Curlydave]That's where it says its busy and refuses to eject.[/QUOTE]
 You could always be mean to it:```
sudo eject
```That should force it open.

---

### Post by Curlydave on 2005-05-22
I think I need to be a little meaner than that: 

umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/dev/hdc' failed

---

### Post by kvidell on 2005-05-22
[QUOTE=Curlydave]I think I need to be a little meaner than that: 

umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/dev/hdc' failed[/QUOTE]
 sudo umount -f /dev/hdc && sudo eject
?

---

### Post by Curlydave on 2005-05-22
"sudo: unmount: command not found"

---

### Post by f.prisson on 2005-05-22
```
umount
``` not ```
unmount
```

---

### Post by kvidell on 2005-05-22
[QUOTE=f.prisson]```
umount
``` not ```
unmount
```[/QUOTE]
 Typo :-P Please read the first time I posted ;) I said it right that time.

Thank you though! *corrects*
- Kev

---

### Post by kvidell on 2005-05-22
[QUOTE=f.prisson]```
umount
``` not ```
unmount
```[/QUOTE]Gyeh! Typo, sorry Dave!
- Kev

---

### Post by Curlydave on 2005-05-22
Oh, woops! (btw, I really appreciate the help on this one!)

> umount2: Device or resource busy
umount: /media/cdrom0: device is busy
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
 is the newest issue.

---

### Post by brickbat on 2005-05-22
er...are you sure you did umount with the -f switch?

---

### Post by Takis on 2005-05-22
The -f switch doesn't actually help - all the more so in this case, because the dude's reading from a CD which is already mounted read-only. (umount f doesn't actually do an unmount, it just sets the read-only flag).

---

### Post by kvidell on 2005-05-22
[QUOTE=brickbat]er...are you sure you did umount with the -f switch?[/QUOTE]
 Well, as my friend here just demonstrated on some of his linux boxes in the datacentre over at cisco; umount -f is just a nice idea, doesn't always work :-\ (works like fire on Solaris boxes though x.x)
Hm... New approach is necessary then.

---

### Post by Curlydave on 2005-05-22
It works when not in the middle of a UT2k4 install... Not when I need it though. :(

---

### Post by neighborlee on 2005-05-22
[QUOTE=Curlydave]It works when not in the middle of a UT2k4 install... Not when I need it though. :([/QUOTE]
----------------
did you start install from the /media/cdrom Direcotry?..if so it wont eject prob...try by running it from somewhere else...you've uncovered one of those little gripes I have with ubuntu that isn't shared by likes of mandrake, suse, knoppix, linspire, xandros or others albeit I hear ( can't verify) that this is being remedied by breezy or the one after that .. ?

good luck
nl

---

### Post by reset_button on 2005-05-23
Yea, it seems like they tried to do a good thing by automatically detecting when a CD is inserted and mounting it, but didn't do such a hot job with it.

---

### Post by sapo on 2005-05-23
haha this is a Ut2k4 DUMB problem

Just copy the script install.sh or whatever its called to another folder... and then run it

Think about it...

You are running the install.sh from the cd... how can you umount the cd if you are using the script?

I dont know what the ut2k4 programmers where thinking when the made it  ](*,)

---

### Post by Takis on 2005-05-23
[QUOTE=sapo]You are running the install.sh from the cd... how can you umount the cd if you are using the script?[/QUOTE]

Hahahaha that's hilarious! Good old Epic.

I haven't tried it out yet, but you might want to have a go at downloading the installer from [the loki dudes](http://www.liflg.org/?catid=6&gameid=17).

---

### Post by Takis on 2005-05-23
[QUOTE=sapo]You are running the install.sh from the cd... how can you umount the cd if you are using the script?[/QUOTE]
Hahahaha that's hilarious! Good old Epic.
Are you sure, though? How is it (AFAIK) noone's really come across this before?

---

### Post by brickbat on 2005-05-25
If its true, that must be the most stupid thing I have heard this year! :roll:

---

### Post by sapo on 2005-05-25
[QUOTE=brickbat]If its true, that must be the most stupid thing I have heard this year! :roll:[/QUOTE]

Believe me.. its TRUE  ](*,)

---

### Post by Curlydave on 2005-05-25
That's it! Thank you very much, I got it installed now. :)

I'm not going to blame epic on this one; I can't even think of any other games that came with a linux client on the CD. How would epic fix this? Perhaps include in the script something that copies it to my desktop and runs it? I think the intention is for you to copy the file onto your HD.

---

### Post by crun on 2005-05-25
Apart from copying the script to your HD you can also run the script like this:

```
sh /media/crom/install.sh
```

then you can still unmount the cdrom and insert a new one during the install process

---

