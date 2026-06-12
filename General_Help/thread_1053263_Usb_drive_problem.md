---
title: "Usb drive problem"
date: 2009-01-28
forum: General Help
---

### Post by qrees on 2009-01-28
I have Ubuntu  8.04

When I insert pendrive it shows up as /media/sdb1 (after a few minutes, but lets call it "a feature", i can live without a PC for a few minutes). When I remove it this is what I get in /var/log/messages:

```
[ 6429.350686] usb 2-6: USB disconnect, address 12
[ 6429.351909] lost page write due to I/O error on sdb1
```
Doesn't look like a feature...

But now when I reconnect the pendrive it shows up as /dev/sdc1 and I can't access it. Ok, ok, I can write mount vfat /dev/sdc1.... but we have year 2009, there has to be an easier way...

---

### Post by cubeist on 2009-01-28
How are you removing it? If you just yank it out without first ejecting it, then you are likely interrupting a data stream causing the I/O message.  Also, the computer thinks that /dev/sdb is still in use, so it assigns the next available dev/sdc.

If you are ejecting the device properly, then we have another problem completely.

---

### Post by ajgreeny on 2009-01-28
Do you unmount the drive before you remove it?  It sounds rather as if you simply pulled it out while it was still mounted, which could account for the change of dev name, and the error message.

---

### Post by qrees on 2009-01-28
> **ajgreeny said:**
> Do you unmount the drive before you remove it?  It sounds rather as if you simply pulled it out while it was still mounted, which could account for the change of dev name, and the error message.
I didn't mount it, but I have to unmount it? And no, no data transfer was in progress, all transfer have finished.

And If it shows up as sdc1 why I can't open it? I have to manually create folders, call mount etc? Ubuntu doesn't recognize that there is new drive and doesn't show it?

---

### Post by ajgreeny on 2009-01-28
USB drives normally automount, so always MUST be unmounted before removing.

---

### Post by qrees on 2009-01-28
> **ajgreeny said:**
> USB drives normally automount, so always MUST be unmounted before removing.

But this still doesn't solve mounting problem. When I insert the drive nothing happens.

We have year 2009 and I still have to mount and unmount everything manually from the console?

---

### Post by Gizenshya on 2009-01-28
I've had some similar problems and issues.

I use "Disk Mounter" (2.22.2) and it works wonders.  Its a tray add-on btw, which makes it very easy to use.  You see the drives (as icons/buttons) that are connected (whether mounted or not) and you can choose to mount, unmount, or open drive from the drive's button. :)

Just right-click on the tray (at the top of the screen) and click "add to panel."  If its not listed, get it from the synaptic installer and then add it to the panel.

---

### Post by qrees on 2009-01-28
> **Gizenshya said:**
> I've had some similar problems and issues.

I use "Disk Mounter" (2.22.2) and it works wonders.  Its a tray add-on btw, which makes it very easy to use.  You see the drives (as icons/buttons) that are connected (whether mounted or not) and you can choose to mount, unmount, or open drive from the drive's button. :)

Just right-click on the tray (at the top of the screen) and click "add to panel."  If its not listed, get it from the synaptic installer and then add it to the panel.

Wonderful, thanks. It's working. it's not fully automatic, but works.

---

### Post by cubeist on 2009-01-28
> **qrees said:**
> I have Ubuntu  8.04

When I insert pendrive it shows up as /media/sdb1

In your own words, your drives DO mount the first time... they just don't mount after you have pulled them out incorrectly.

So all you have to do is properly unmount your drives and your mount/unmount problems will disappear.  If you are using Nautilus, there is a handy little eject icon next to the drive in the side pane... pressing this unmounts the drive.  Or, in the file menu, select "unmount volume". Very easy.

Also, you should know this is not unique to linux, you have to umount drives properly in windows and mac, or face possible data loss.

cheers

---

### Post by qrees on 2009-01-28
> **cubeist said:**
> In your own words, your drives DO mount the first time... they just don't mount after you have pulled them out incorrectly.

So all you have to do is properly unmount your drives and your mount/unmount problems will disappear.  If you are using Nautilus, there is a handy little eject icon next to the drive in the side pane... pressing this unmounts the drive.  Or, in the file menu, select "unmount volume". Very easy.

Also, you should know this is not unique to linux, you have to umount drives properly in windows and mac, or face possible data loss.

cheers
Well... it mounted for the first time, but only after I've added it to /etc/fstab as sdb1. It works with Disk Mounter sdc1.

But it should be seen in gnome as sdc1, I don't think that gnome has got some allergy to "c" letter.

---

### Post by ajgreeny on 2009-01-28
You have not actually told us if you have tried doing this to get your USB drive automounting again, as it apparently did the first time you plugged it in.

I am amazed how many people, who with knowledge of windows only, just pull out usb drives with no thought about what may be going on and then wonder why things have not copied properly, or written to disk cleanly.

---

### Post by qrees on 2009-02-02
> **ajgreeny said:**
> You have not actually told us if you have tried doing this to get your USB drive automounting again, as it apparently did the first time you plugged it in.

I am amazed how many people, who with knowledge of windows only, just pull out usb drives with no thought about what may be going on and then wonder why things have not copied properly, or written to disk cleanly.
What knowing windows has to do here? You are Linux Torvalds or sth?

I the other hand I think you should learn how to read. Who said something about copying? Who said something about writing to disk?

Now I have reinstalled the system (I used to have 8.04, now I have 8.10), and guess what? It's working. I can insert the usb drive and it automounted. I can pull it out and it's unmounted. No playing with console. This may be a shock for you, so sit down, breath for a while or sth:
It now works exacly the same like in Windows. (I don't like comparing Linux to Windows, but you forced me)

---

### Post by ajgreeny on 2009-02-02
I am sorry if I upset you but you misunderstood my point, which was simply that you MUST ALWAYS unmount a usb drive before removing it and many people do not do this and risk corruption of data by not doing so.  That was a general point and not aimed specifically at you.  However, I repeat my comment, make sure you unmount the drive before removing it, whether in windows or linux.

See also what cubeist said; it is not just me telling you:-
> So all you have to do is properly unmount your drives and your mount/unmount problems will disappear. If you are using Nautilus, there is a handy little eject icon next to the drive in the side pane... pressing this unmounts the drive. Or, in the file menu, select "unmount volume". Very easy.

Also, you should know this is not unique to linux, you have to umount drives properly in windows and mac, or face possible data loss.

cheers 	

---

### Post by qrees on 2009-02-02
> **ajgreeny said:**
> I am sorry if I upset you but you misunderstood my point, which was simply that you MUST ALWAYS unmount a usb drive before removing it and many people do not do this and risk corruption of data by not doing so.  That was a general point and not aimed specifically at you.  However, I repeat my comment, make sure you unmount the drive before removing it, whether in windows or linux.

See also what cubeist said; it is not just me telling you:-

Yes, I can see your point, and I'm sorry. I know I have to (or I should) unmount every drive before removing it. The point is, it didn't work the way it should have, but now it works so case closed ;)

And about these "stupid" windows users, it's not really about beeing windows user or linux user, it's just about how much you know about computers and the way they work.

---

