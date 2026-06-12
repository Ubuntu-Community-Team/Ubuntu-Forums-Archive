---
title: "Cant delete an mp3. says read only permission"
date: 2009-02-10
forum: General Help
---

### Post by SteveNorman on 2009-02-10
Heres the story as complete as I can tell it. A friend sent me an mp3 file of a song we recorded on protools, via his mac. I downloaded it to my asus one (150 HD version). I listened to it, then let the laptop sit. after I tried to wake it up the system crashed. I could not boot the laptop into ubuntu. I dual boot this with XP which booted and ran as fine as it normally does. I just tried to boot into ubuntu after it sat for awhile and was able to reboot into my graphical desktop (GNOME), but it is running poorly. I tried to move the file into the trash but got an error message. I tried to open a terminal but could not. I am now in my cntrl alt f1 virtual terminal session, and cannot sudo rm -rf the damn file either. It say

```
rm: cannot remove `God Of Man mix9.mp3': Read-only file system
```

I have tried ```
chmod 777 God Of Man mix9.mp3
```

and  get 
```
chmod: changing permissions of `God Of Man mix9.mp3': Read-only file system
```

I had thought the sudo rm -rf was the nuke of the linux world....Can anyone tell me what I am doing wrong?

BTW I am assuming its the mp3 which is causing the problem, after I get rid of it I  can trouble shoot something else

---

### Post by SteveNorman on 2009-02-11
I am now wondering if my root is corrupted somehow, I cant open anything requiring a password....lil help?

---

### Post by Xiangxianni on 2009-02-11
> **SteveNorman said:**
> Heres the story as complete as I can tell it. A friend sent me an mp3 file of a song we recorded on protools, via his mac. I downloaded it to my asus one (150 HD version). I listened to it, then let the laptop sit. after I tried to wake it up the system crashed. I could not boot the laptop into ubuntu. I dual boot this with XP which booted and ran as fine as it normally does. I just tried to boot into ubuntu after it sat for awhile and was able to reboot into my graphical desktop (GNOME), but it is running poorly. I tried to move the file into the trash but got an error message. I tried to open a terminal but could not. I am now in my cntrl alt f1 virtual terminal session, and cannot sudo rm -rf the damn file either. It say

```
rm: cannot remove `God Of Man mix9.mp3': Read-only file system
```

I have tried ```
chmod 777 God Of Man mix9.mp3
```

and  get 
```
chmod: changing permissions of `God Of Man mix9.mp3': Read-only file system
```

I had thought the sudo rm -rf was the nuke of the linux world....Can anyone tell me what I am doing wrong?

BTW I am assuming its the mp3 which is causing the problem, after I get rid of it I  can trouble shoot something else


Maybe your file system crashed,try to fsck it and try again.

---

### Post by SteveNorman on 2009-02-11
booting into recovery does that automatically in 8.10 right? This acer is without a cd drive....

---

### Post by ozanamn on 2009-02-11
Have you tried deleting it thru Nautilus yet?

---

### Post by SteveNorman on 2009-02-11
I havnt been able to open anything yet. no terminals or synaptic etc. so far the menu drop downs open, but no apps run, including the terminal. I have to use a virtual terminal with cntrl alt f1, and when using that earlier I couldnt access synaptic. I may be able to get nautilus,,I will try and reboot into ubuntu in a bit after I research somemore.

right now I get he desktop and menus,,but thats about it.

---

### Post by howefield on 2009-02-11
You could try booting up with the live cd and deleting the file from there, but sounds more severe than the damage a bad mp3 could cause.

---

### Post by SteveNorman on 2009-02-11
yeah Im gonna try and free disk space first then go from there. the mp3 was the last thing I used which made me decide to get rid of it first.Im on a little acer one with no drive, so im at a loss, guess I can go to another box and make a bootable usb.

---

### Post by 3rdalbum on 2009-02-11
Almost nothing will run on a read-only filesystem. You need to boot up a live CD/live USB and run "fsck" on your disk.

---

### Post by SteveNorman on 2009-02-11
I am in my Ubuntu partition now, and everything seems to be working. What I did:

running 8.10 which has a built in fsck in recovery mode:
-booted computer
-in grub hit esc
-choose recovery mode
-auto fsck runs and fails, message stated I had duplicate (multiply claimed) blocks in use, stated that I was in a read only file system, and am in a recovery mode. The message stated I should run fsck manually without options
- it gave me a root prompt in which I entered fsck
-fsck ran and I answered all options yes
-after the prompt returned I hit cntrl-D and the sytem rebooted normally


So the rumoured built in fsck in recovery mode is real. I did not have to use a bootable cd or usb to fix this. Good job Developer!

Thanks all who helped, are the thanks tags gone now in this forum? Also how do you mark things as solved now didnt see it in thread tools....

---

