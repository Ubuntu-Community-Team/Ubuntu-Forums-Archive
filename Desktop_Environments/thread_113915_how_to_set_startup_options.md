---
title: "how to set startup options"
date: 2006-01-07
forum: Desktop Environments
---

### Post by N6REJ on 2006-01-07
I need to make a few changes to my boot options. 
[LIST=1]
[*]numlock on at boot time.
[*]dma on for dvd ( hdc )
[/LIST]
I know about numlockx but that doesn't seem to work permamently.  I've even told KDE to have numlock on.
I can manually turn dma on for the dvd but on reboot its off.
I want numlock to always be on not just with x
I tried searching but didn't find anything.
Troy

---

### Post by ounas on 2006-01-07
Try this out for DMA - Troy


How do I speed up CD/DVD-ROM access (enable DMA)?
	

   1.
      Assuming that /dev/cdrom is the location of CD/DVD-ROM

   2.

      sudo hdparm -d1 /dev/cdrom 
      sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup 
      sudo gedit /etc/hdparm.conf

   3.

      Append the following lines at the end of file

      /dev/cdrom {
      dma = on
      }

   4.

      Save the edited file

This was from the following link:
[URL="http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447"]
http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2514447[/URL]

Check out the StarterGuide..
[URL="http://doc.gwos.org/index.php/BreezyCust"]
http://doc.gwos.org/index.php/BreezyCust[/URL]

-Ounas :razz:

---

### Post by Sp@z on 2006-01-07
Automatix does both these things automatically.....:) If you are using Ubuntu use the link I provided, if you are using Kubuntu search the forums try kubuntu automatix......

[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

---

### Post by ounas on 2006-01-07
Your right about that sp@z..

-Ounas :razz:

---

### Post by N6REJ on 2006-01-07
sorry I didn't look closer.

---

### Post by ounas on 2006-01-08
[QUOTE=N6REJ]sorry I didn't look closer.[/QUOTE]

No need to be sorry, glad to be of help.

-Ounas :p

---

