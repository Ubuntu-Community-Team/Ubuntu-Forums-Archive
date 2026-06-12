---
title: "Can't mount Windows"
date: 2009-04-14
forum: General Help
---

### Post by rfLarke on 2009-04-14
Hey guys, I apologize if this it the wrong forum.

Basically, I was in Ubuntu, fishing through the files on my Windows partition, and accidentally mis-clicked and moved some files around and broke something. So I tried using system restore since I didn't know what files I moved (My laptop's trackpad is a little wonky, I didn't even see what happened), and it all did it's thing... But now I can't boot Windows, it just gets as far as "welcome", then freezes.

Anyways, that's aside the point, here's the deal: I have means of restoring windows, but I need to retrieve some important files before I do so. Unfortunately, I cannot do so due to being unable to shut down windows short of killing the power, which of course means it's not unmounting properly, meaning I can't access the files from Windows OR Ubuntu.

Basically, I'm going to be really bummed if I can't get those files off of Windows before I restore it, so... Help.

(ps, I'm using a single hard drive with a Windows and Ubuntu partition.)

---

### Post by theozzlives on 2009-04-14
You should be able to access your Windows partition through Ubuntu, If you can't use the live CD to access your Windows partition.

---

### Post by rfLarke on 2009-04-14
I'm afraid I've tried both the LiveCD and my regular install and both return "Unable to mount the volume"

---

### Post by Alekz_ on 2009-04-14
Can you post us which command you're using to mount the Win partition? And what message appear after the command execution...

Like:
mount -t ntfs /dev/sda1 /mnt/win

[]'s

Alekz_

---

### Post by rfLarke on 2009-04-14
Oh, hah. I wasn't actually using a terminal (Not as used to it, been using Windows for over a decade), I was just clicking the volume from the "places" menu.

Anyways, tried that, it didn't do anything, but it gave me an option to force it, which did the trick, now I'm able to boot windows again.

Wow I feel silly, how simple that was. Thanks guys!

---

