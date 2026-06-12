---
title: "Completely Erase Hard Disk"
date: 2009-03-05
forum: General Help
---

### Post by notesetter on 2009-03-05
Hello,

I'm looking for a reliable open-source utility (maybe a live CD?) that will completely and destructively erase all the contents of a hard disk (Arthur Andersen style).

In case you're wondering, I'm collecting donated computers and refurbishing them with memory, upgraded peripherals and xubuntu. The computers are to go to low-income families with school-age children my the community who don't already have access to a computer. Naturally, I want to assure potential donors that their old data will be completely destroyed.

Does gparted do this when it formats a disk?

A brief description of the program can be found at [http://www.notesettersinc.com/Community.html]("http://www.notesettersinc.com/Community.html") The site is still under construction.

The program's own website is under construction and is not yet up.

Thanks,

David

---

### Post by Rabid Moth on 2009-03-05
Dariks Boot and Nuke does an excellent job. It has several different styles of writing to the hard drive.

---

### Post by anjilslaire on 2009-03-05
from your live cd:

```

dd if=/dev/zero of=/dev/hda

```

This will destroy all data on the hard drive.

---

### Post by Krupski on 2009-03-05
> **notesetter said:**
> In case you're wondering, I'm collecting donated computers and refurbishing them with memory, upgraded peripherals and xubuntu. The computers are to go to low-income families with school-age children my the community who don't already have access to a computer. Naturally, I want to assure potential donors that their old data will be completely destroyed.


You can use "DD" to write zeros to the drive. It's a slow process though... plan on about 1/2 hour for a 250 GB hard drive.

If you want to use "dd", here's how:

```

[COLOR="Red"][B]
## WARNING! THIS CODE ERASES HARD DRIVES!
## DO NOT CUT-N-PASTE, THEN USE THIS CODE UNLESS
## YOU COMPLETELY UNDERSTAND WHAT IT DOES!
[/B][/COLOR]

    dd if=/dev/zero of=/dev/sdb bs=32K


```

The above example assumes that the drive you wish to erase is "/dev/sdb". You will have to connect the drive you wish to erase to the computer, determine it's device name, then put the PROPER name into the command shown above.

Hope this helps.

-- Roger

---

### Post by Krupski on 2009-03-05
> **anjilslaire said:**
> from your live cd:

```

dd if=/dev/zero of=/dev/hda

```

This will destroy all data on the hard drive.

Oops... sorry didn't see your post.

---

### Post by notesetter on 2009-03-05
> You can use "DD" to write zeros to the drive. It's a slow process though... plan on about 1/2 hour for a 250 GB hard drive.


Can/should I use this method with a Live CD on whichever computer I'm working on? Can I use an Ubuntu Live CD or is this for gparted? Either?

Thanks for the help,

Dave

---

### Post by boof1988 on 2009-03-05
I have used both "dd" and [Darik's Boot and Nuke (DBAN)](http://www.dban.org/download).  I prefer DBAN because it "feels" more automated and has more of a GUI "feel".  Also DBAN is on it's own "LiveCD" that you boot up and then the CD can be removed while DBAN does it's thing.

Maybe try both and see which you like more.

---

### Post by Therion on 2009-03-05
> **boof1988 said:**
> 

I have used both "dd" and [Darik's Boot and Nuke (DBAN)](http://www.dban.org/download).

+1 For DBAN.  Not that other methods won't work.

---

### Post by James- on 2009-03-05
> **anjilslaire said:**
> from your live cd:

```

dd if=/dev/zero of=/dev/hda

```

This will destroy all data on the hard drive.

if you really want to wipe data...aka NOT RECOVERABLE...AKA stuff you don't want other people finding ^.-

Use these 2 commands:

```

dd if=/dev/urandom of=/dev/hda
dd if=/dev/zero of=/dev/hda

```

---

### Post by Herman on 2009-03-05
I like the reply by az in post #5 of the following thread:  [safely erase a hard disk with zeros]("http://ubuntuforums.org/showthread.php?t=606846&highlight=badblocks")- Ubuntu Web Forums.

In the above-linked thread, Az said:> A more useful method would be to use badblocks.  Why not put the work to good use and look for bad blocks at the same time as you are overwriting your data.
```
sudo badblocks /dev/sda -w -s -p 5
```[COLOR=Red]**WARNING, the above code will completely destroy all of the data on your hard drive - only use it if you really intend to erase all of your data!**[/COLOR]

---

### Post by Krupski on 2009-03-05
> **Herman said:**
> [COLOR=Red]**WARNING, the above code will completely destroy all of the data on your hard drive - only use it if you really intend to erase all of your data!**[/COLOR]

Excellent! I think it should be a "policy" here that any commands or code which have the potential to damage data or erase someone's system should have a big, bright red warning attached to it.

-- Roger

---

### Post by HermanAB on 2009-03-05
All disk drives have a secure erase utility built into the drive controller.  All you need to do is activate it:

$ sudo hdparm --security-erase-set-pass whatever /dev/sda
$ sudo hdparm --security-erase-enhanced whatever /dev/sda

The drive will then erase itself.

This is the best way to non-destructively erase a drive.

Cheers,

Herman

---

