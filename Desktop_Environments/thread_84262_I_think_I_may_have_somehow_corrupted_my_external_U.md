---
title: "I think I may have somehow corrupted my external USB drive"
date: 2005-10-30
forum: Desktop Environments
---

### Post by aysiu on 2005-10-30
Ordinarily, I'd think there was actually something wrong with gnome-volume-manager or some kind of weird Gnome bug, but here's the situation:

My wife's iPod--works fine. I plug it in. It mounts and appears on the desktop. I right-click and select "unmount volume," and it unmounts and disappears from the desktop.

My Sandisk MP3 Player--also works fine. I plug it in. It mounts and appears on the desktop. I right-click and select "unmount volume," and it unmounts and disappears from the desktop.

Okay. The problem? My Lacie external hard drive in the past few days (i.e., it never did this before in the last six months I've been using Ubuntu), instead of unmounting cleanly when I select "unmount volume," gives me this error message:

```
Unable to eject media

eject: unable to eject, last error: Invalid argument
``` If you want to see how it actually looks, take a look at the screenshot I attached.

As I said before, I'd ordinarily think it was some kind of bug except that for two other external USB devices, it works just fine, *and* I haven't had these problems with the Lacie one in the last six months either (so I don't think it's a hardware compatibility issue).

Any ideas what could be wrong? And if it is some kind of corruption (maybe unknowingly I didn't do a clean unmount before?), how can I uncorrupt it?

Note: it does unmount cleanly if I run ```
sudo eject /media/LACIE
``` from the terminal.

---

### Post by NewbieNik on 2005-10-30
I asume it mounts OK? and data is readable?

---

### Post by aysiu on 2005-10-30
[QUOTE=NewbieNik]I asume it mounts OK? and data is readable?[/QUOTE] Thanks for responding. Yeah, it mounts just fine. All the data is intact. I can read/write to it. I can copy files to and from it. It works just fine. It's only the unmounting that doesn't work.

It can eject with the sudo command but gives me the error if I try to unmount it as a user.

---

### Post by NewbieNik on 2005-10-30
Don't think its your hardware.....Looks like a permission error, but where is a little harder. 
Not sure if I cn help, but can throw some sticks in the air and see where they land.
Whats the /dev name of LACIE? Is it using the same dev as the other devices?
Have you accessed and umounted LACIE as a different user besides you and sudo?
Have you given it a good kick? (Sorry, had to throw that one in)

---

### Post by aysiu on 2005-10-30
[QUOTE=NewbieNik]Don't think its your hardware.....Looks like a permission error, but where is a little harder. 
Not sure if I cn help, but can throw some sticks in the air and see where they land.
Whats the /dev name of LACIE? Is it using the same dev as the other devices?[/quote] Thanks for walking me through this detective work. I've never had a problem like this before. Unfortunately, the results are not very enlightening:

iPod: /dev/sde2
Sandisk: /dev/sdf1
Lacie: /dev/sdf1

> 
Have you accessed and umounted LACIE as a different user besides you and sudo?
Have you given it a good kick? (Sorry, had to throw that one in) I'm about to try using a different user. The good kick may come if I can't figure this out.

**Edit**: Okay. I just logged out and logged back in as another user--same problem.

Damn.

It doesn't look easily solvable. Any other ideas?

---

### Post by NewbieNik on 2005-10-30
[QUOTE=aysiu]Thanks for walking me through this detective work. I've never had a problem like this before. Unfortunately, the results are not very enlightening:

iPod: /dev/sde2
Sandisk: /dev/sdf1
Lacie: /dev/sdf1

 I'm about to try using a different user. The good kick may come if I can't figure this out.[/QUOTE]

dagnammit!!! the fact the LACIE and sandisk are the same has just ruined my devious and evil plan of permissions on the /dev
I'm afraid to admit thatI am beyond my swimming depth on this one. I will dutifully scour sites to see if I can turn anything up, but I don't know myself, sorry and good luck!

---

### Post by gw90se on 2005-10-30
I am going to watch this thread. I am having the same error message pop up when I unmount my external hard drive.

---

### Post by aysiu on 2005-10-30
It's okay. Thanks for your help. I think I may just ```
sudo eject /media/LACIE
``` for a while. I just use it once a week to back up my files. If there was a quick fix that would have been nice, but oh well...

---

### Post by aysiu on 2005-10-30
[QUOTE=gw90se]I am going to watch this thread. I am having the same error message pop up when I unmount my external hard drive.[/QUOTE] Oh, you are? Hm. Maybe we *should* file a bug report on this...

What brand is your external hard drive? What filesystem does it use? Mine is a Lacie, and it's FAT32.

---

### Post by NewbieNik on 2005-10-30
PS got a great piece of wood for smacking broken devices about, you can borrow it if all else fails

---

### Post by aysiu on 2005-10-30
[QUOTE=NewbieNik]PS got a great piece of wood for smacking broken devices about, you can borrow it if all else fails[/QUOTE] I appreciate the offer. *sudo eject /media/LACIE* will probably do for now.

---

### Post by gw90se on 2005-10-30
I am not sure of the brand. It is a very generic one that I was given. (The case that is, I had the maxtor hard drive.) I beleive it came from Tiger Direct.

I am curious why it feels it has to eject it? Floppys unmount fine. CD's eject fine. Does it see it as a CD type drive?

---

### Post by aysiu on 2005-10-30
No idea.

---

### Post by Samuel on 2005-10-30
i have been having similar problems, my flash drive and iPod are both sda1 and between them i get different problems, sometimes the flash drive wont mount and i cannot unmount my iPod as user, can you boot ubuntu fine with the drives plugged in? 

My box wont boot while the flash drive is in, i get something like,
Starting Enterprise Volume Manager and it stays like that for about 5 minutes.

in the usplash when hot-plugging is starting it doesn't say OK, everything else does....
My iPod became corrupt and needed reformatting yesterday :( 
Seems like allot of strange problems going on with USB recently.
One post suggested it was due to the kernel upgrade from the updater and said he fixed his usb problems by downgrading the kernel, I'm not sure how to do this though.

---

### Post by gw90se on 2005-10-30
yeah, I can boot with the ext hard drive plugged in. No difference to it.

---

### Post by aysiu on 2005-10-31
The mystery continues...

In KDE, the graphical (user) unmount works just fine for that device.

---

### Post by Nomad64 on 2005-10-31
[QUOTE=aysiu]It's okay. Thanks for your help. I think I may just ```
sudo eject /media/LACIE
``` for a while. I just use it once a week to back up my files.[/QUOTE]
I don't have any idea as to why this is happening...it could be a bug. You said that it didn't start happening until a few days ago? Have you updated anything on your system or made any other major changes between the last time it worked fine, and the first time it didn't?

Just noticed that your sandisk drive and this External HDD both mount in /dev/sdf1, but you use the other location (/media/LACIE/) to umount it? Double check the permissions of both folders. That would be my shot-in-the-dark.

To streamline the process, you could just make a custom application launcher with the command: "sudo eject /media/LACIE" and place it on your panel or desktop (be sure to select "Run in Terminal").

Although, the fact that you can mount it, and read/write from it makes me believe that the HDD itself is just fine.

---

### Post by gw90se on 2005-10-31
Ah, a hint to check out. If I use the command sudo to eject it, it works fine. If I don't sudo, I get the message. So, it has to be a permissions problems

```
gw90se@ubuntu:~$ sudo eject /media/USB_BACKUP
Password:
gw90se@ubuntu:~$ eject /media/USB_BACKUP
eject: unable to eject, last error: Invalid argument
gw90se@ubuntu:~$

```

---

### Post by GeneralZod on 2005-10-31
[QUOTE=aysiu]
```
Unable to eject media

eject: unable to eject, last error: Invalid argument
``` 
[/QUOTE]

I'd bet 20p that this is a bug and nothing to do with your hard-drive, especially as the command-line call works.  I'm betting that the Eject command issued by GNOME is giving the wrong /dev/<blah> entry.  Another vote for "File a bug report!" here :)

---

### Post by aysiu on 2005-10-31
Bug report filed.

It's now [bug report #18718](https://bugzilla.ubuntu.com/show_bug.cgi?id=18718)

---

### Post by Nomad64 on 2005-11-01
It would seem that we aren't alone...[https://bugzilla.ubuntu.com/show_bug.cgi?id=5049](https://bugzilla.ubuntu.com/show_bug.cgi?id=5049).

Also notice that there are *several* bug reports of this...so it shall be added to the pile of "unsolved mysteries" for now. :)

---

### Post by gw90se on 2005-11-16
Interesting twist. I set my system up to auto mount for writing to the fat32. Then when I unmounted, I didn't get the eject error.


Oops, spoke too soon. It evidently was still writing and the error message showed up. Back to the drawing board.

---

