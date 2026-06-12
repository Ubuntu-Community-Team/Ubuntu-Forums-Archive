---
title: "Thunar vs. Nautilus"
date: 2010-12-29
forum: Desktop Environments
---

### Post by BlueInkAlchemist on 2010-12-29
Greetings, all:

I'd really prefer to use Nautilus as my default file manager in Xubuntu rather than Thunar.  I followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=720449") to make this change but Thunar continues to manage my files when the system boots.  

Thinking that perhaps Xubuntu was opting for the 'Thunar' program file rather than the 'thunar' script I'd written, I tried renaming the file of the program to '_Thunar'.  The system didn't like that one bit, throwing errors about not connecting to the trash service and not opening the GUI's file system icon by default.  I sudo'd back into Nautilus and changed the file name back.

So where do I go from here?  I'm running Xfce 4.6.1 currently, if that makes a difference.

Thank you in advance!

---

### Post by Jose Catre-Vandis on 2010-12-29
Why not install just plain old Ubuntu?

Anyway, what is it about thunar that's the problem? I find it much more flexible and adaptable than nautilus, and it doesn't "get in the way" as much. Only a few GUI issues on right click and paste here and there, but learn a new way (not how it is in Windows)

---

### Post by BlueInkAlchemist on 2010-12-29
> **Jose Catre-Vandis said:**
> Why not install just plain old Ubuntu?

Anyway, what is it about thunar that's the problem? I find it much more flexible and adaptable than nautilus, and it doesn't "get in the way" as much. Only a few GUI issues on right click and paste here and there, but learn a new way (not how it is in Windows)

Whenever I plug in a flash drive, Thunar will let me into it but won't allow me to unmount it.  It throws the error:

```
Unable to unmount "CAKE":

The volume "CAKE" was probably mounted manually on the command line
```

while Nautilus ejects it just fine.  Also, Thunar doesn't seem to know I have partitions outside of the boot partition and trying to access them with GParted gives me the "Enclosing drive for the volume is locked" error, while Nautilus lets me mount & browse the contents of my other partitions fine.  One partition is ext4 while the other is FAT32.

---

### Post by azertyh on 2010-12-30
hello,
i had the same message with ubuntu 10.04 where i installed xfce.
i posted on xfce forum [http://forum.xfce.org/viewtopic.php?id=5458](http://forum.xfce.org/viewtopic.php?id=5458), they suggested that it is due to a conflict between hal, udisks, ... 
i didn't found a solution

---

### Post by Jose Catre-Vandis on 2010-12-30
Hmmm, what Ubuntu animal are you running, there were a couple of annoying bugs with thunar a while back 8.10 / 9.04 / 9.10, regarding flash drives.

---

### Post by BlueInkAlchemist on 2011-01-28
> **Jose Catre-Vandis said:**
> Hmmm, what Ubuntu animal are you running, there were a couple of annoying bugs with thunar a while back 8.10 / 9.04 / 9.10, regarding flash drives.

Sorry for the delay.  Things have been excruciatingly busy.

Anyway.

System Monitor on the laptop tells me my animal is 10.04, with the 2.6.32 kernel... yet also says I'm running Gnome.  Cue me saying "Bwuh?!?"

The laptop's very old, a Dell Inspiron 8600.  I figured Xubuntu with its undemanding XCFE would be a better match than standard Ubuntu.  But what's the point if GNOME's on it?  Hmm.  I think I might have installed one thing too many.

Would it behoove me to remove GNOME/Nautilus at this point?

---

### Post by AlphaLexman on 2011-01-28
Nautilus can be a heavy beast on an xfce system, I would try | check out: "pcmanfm'

---

### Post by newyorkcityjay on 2011-09-14
I have used both Nautilus and Thunar under Gnome and Xfce4.  I see good and bad about each, but not a definitive reason to use one or the other.  I tend to use Thunar now out of habit, but I have Nautilus installed because I want Dropbox.  Any ideas?  Any strong preferences?

---

### Post by drawkcab on 2011-09-15
Perhaps xfce 4.8 in natty has these expanded options?

---

### Post by Copper Bezel on 2011-09-15
If you don't mind installing Parcellite, you can copy Dropbox public links from Thunar, too. Just set this as a custom action:

```
dropbox puburl %f | parcellite
```

---

