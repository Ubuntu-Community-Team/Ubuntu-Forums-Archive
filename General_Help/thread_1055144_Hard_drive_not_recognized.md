---
title: "Hard drive not recognized"
date: 2009-01-30
forum: General Help
---

### Post by lunarlightlord on 2009-01-30
Okay, I'm new to Ubuntu, but someone suggested using Ubuntu to recover files from a hard drive that wouldn't boot. I've followed the procedures to Try Ubuntu without any change to your computer, and the Ubuntu desktop is now showing, but the hard drive doesn't show up in the places menu. 
Are there any reasons why it's not showing up? It's a hard drive with Windows XP installed on it.

---

### Post by taurus on 2009-01-30
You need to mount it first before you can access it.  Open a terminal from the LiveCD and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

---

### Post by Irony on 2009-01-30
In terminal copy and paste;

```
sudo fdisk -l
```

Post the output here.

---

### Post by Irony on 2009-01-30
To copy and paste use the mouse to highlight the text to be copied, then middle click in the terminal.

---

### Post by lunarlightlord on 2009-01-30
> **Irony said:**
> In terminal copy and paste;

```
sudo fdisk -l
```

Post the output here.

There is no output. I entered the command and it just goes back to the command prompt
ubuntu@ubuntu:~$

---

### Post by dabl on 2009-01-30
That means the hard drive isn't even seen by your BIOS.  ???

Are you sure it has power?  You might have a dead hard drive -- Ubuntu won't help if that's the case.   :-?

---

### Post by lunarlightlord on 2009-01-30
> **dabl said:**
> That means the hard drive isn't even seen by your BIOS.  ???

Are you sure it has power?  You might have a dead hard drive -- Ubuntu won't help if that's the case.   :-?

It has power, and spins when I boot the computer. I think I screwed up though. I was going to access the files from the hard drive with a hard drive enclosure on another computer, so I removed the hard drive from the computer. But when I read I could use Ubuntu to access those files, I went to put the hard drive back in and dropped it from about a foot off of the ground. It wasn't spinning when it dropped, but I guess I busted it. Crap.

---

### Post by dabl on 2009-01-30
Try reconnecting the data cable to the drive, then go into BIOS and see what it says about a connected hard drive.  If you see it in BIOS, then try booting your Linux Live CD again and try again with ```
sudo fdisk -lu
```

But if there's no hard drive showing up in BIOS, then it isn't going to show up with Linux either.  :(

---

### Post by lunarlightlord on 2009-01-30
> **dabl said:**
> Try reconnecting the data cable to the drive, then go into BIOS and see what it says about a connected hard drive.

Thanks, I will try that.

---

### Post by lunarlightlord on 2009-01-30
Well, that didn't work. I'm going to try a few other things and post back later.

---

### Post by lunarlightlord on 2009-01-30
In BIOS, it says the primary master drive is an unknown device. Any suggestions?

---

### Post by lunarlightlord on 2009-01-30
> **lunarlightlord said:**
> In BIOS, it says the primary master drive is an unknown device. Any suggestions?

Also, when rebooting Ubuntu from the disc it is saying:
(initramfs) [    66.088017] ata1: SRST failed (errno=-16)

---

