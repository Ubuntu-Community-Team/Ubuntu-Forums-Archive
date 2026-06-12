---
title: "Gnome/GTK File Dialogs Slow and Pausing"
date: 2009-03-26
forum: General Help
---

### Post by Simon G Best on 2009-03-26
Since finally getting round to upgrading to 8.10 a few days ago, I've found that GTK file dialogs can be very slow, and often pause for periods of time.

The file dialogs in question are the ones that come up when choosing such menu options as "Save As...".  It's the GTK dialogs that are affected, such as often used in Gnome.  Firefox (3.0.7) uses these dialogs, too.

Sometimes these dialogs are just very slow when listing files.  They're also slow when creating new folders, and take a moment to list the newly-created folders.  But sometimes these dialogs just pause for some time, usually when freshly opened, with nothing displayed where files and folders should be listed.  Eventually, the pause ends, and the contents get listed.  When being slow, CPU load is at maximum (for one core, I think), used by the program with the slow dialog.

I'm using Ubuntu 8.10, with Xfce, on a Dell Inspiron 530n (came with 7.04 pre-installed, and has been upgraded up to 8.10).

I've already searched these forums, but without much success.  Tracker certainly isn't the problem, as it's uninstalled.

Anyone know what the problem is?

---

### Post by Simon G Best on 2009-04-12
I've just spent a number of minutes waiting for a file saving dialog box to list files and folders.  It's obviously a bug of some kind.  It has to be.  It's not like I'm using a 386.

Prior to 8.10, such GTK dialog boxes were working fine.  It's so frustrating that something that was working fine has been somehow "improved" into not working properly :mad:

---

### Post by crc294 on 2009-04-29
I am experiencing a similar problem, though mine only happens when you first open the dialog. E.g., when I do "Save As", it might be 10 or 15 seconds until the dialog box shows up, and the window I am working in grays out in the meantime. However, once it does show up, it operates normally.

I just upgraded to jaunty, and this didn't seem to happen to me in intrepid.

---

### Post by lukerazor on 2009-05-06
Same problem here after upgrading to JJ.

After googling for an answer I have seen a couple of suggestions

1. The Icon theme - There was an older post suggesting that if the icon theme was based on the svg format there could be delays
2. The Tracker Tool - The suggestion here is that the Tracker search tool (Accessories -> Tracker) was locking something and blocking the dialog.[See This]("http://ubuntuforums.org/showthread.php?t=1035533")

Removing the Tracker tool worked for me, but I had to restart the machine to see the fix

---

### Post by pbubenik on 2009-06-01
I've had this problem with intrepid and jaunty. I don't have tracker installed, and I am using the default icons.

---

