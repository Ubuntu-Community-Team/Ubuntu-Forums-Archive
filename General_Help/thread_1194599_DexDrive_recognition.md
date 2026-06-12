---
title: "DexDrive recognition"
date: 2009-06-22
forum: General Help
---

### Post by FeyerbrandX on 2009-06-22
I will admit that this is verging on a level that only Rube Goldberg has reached.

I have a DexDrive.  This thing was even when it was new was a nightmare to make work.  I dual boot with Vista (I'll say no more about *that*).

Now to make it interesting, my current computer does not have a serial drive.  I got a Lindy Serial->USB adaptor.  I have already followed the procedure to get it to work found here:
[http://forums.reprap.org/read.php?12,4546]("http://forums.reprap.org/read.php?12,4546")

It identifies it as a Prolific Tech Serial Converter.

Now for phase 2.  Following this forum thread I managed to compile the program mentioned, despite the fact that it is as old as dirt.

[http://ubuntuforums.org/showthread.php?t=369504]("http://ubuntuforums.org/showthread.php?t=369504")

Finally, the README file of the package says to move to folders to the bin directory.  I moved the "dex" and "dex-off" files to usr\bin.

Now what would be the final step?  I don't see anything labeled with "Dex" in the applications drop down.  Nor do I see anything in synaptic or "Add/Remove Applications".

I've restarted, but still I see nothing positive.  Do I need to somehow mount the DexDrive as a physical drive, or something?

Any help would be appreciated.

---

### Post by adrianj2012 on 2011-04-16
Hey, there. I hope that you're still interested, since I noticed it's been awhile, but this might be helpful to anyone else out there.  If it helps, I'm currently running Ubuntu 10.10 Maverick.

(Here goes nothing)

I managed to get my DexDrive to recognize and read my memory card, here's how:

I am using Wine [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu) to run a program called Dexter to read the cards.  It can be downloaded at the bottom of this page: [http://www.neillcorlett.com/dexter/](http://www.neillcorlett.com/dexter/)

However, when I just installed it, it wasn't reading it, so I figured it might have to do with the COM port itself.  I then installed "Serial Port Terminal" (I searched the repositories using the Ubuntu Software Center).

I looked at my settings using Configuration > Port and set the "Flow Control" option to RTS/CTS for the COM drive. (Got the inspiration after reading this: [http://linux.koolsolutions.com/2008/04/10/how-to-test-serial-ports-under-debian-linux/](http://linux.koolsolutions.com/2008/04/10/how-to-test-serial-ports-under-debian-linux/))

If you then open up Dexter, it will be able to read your cards, although with mine it says there is "inconsistency" (not sure why, but it still works fine).

If you have any questions, I'll see what I can do to help (considering I'm somewhat-new to this myself).

Hope that helps!

Edit: Sorry for not actually answering your question, but I felt this workaround could be of some use to you!

Edit2: It worked once, but after that, it stopped working for some reason.  Now, I installed the Dexplorer software and it picked up my DexDrive right away, although the program looked a bit glitchy graphics-wise.

It can be found here "Updated Dexdrive Software":
[http://www.legendcup.com/gamesaves.php](http://www.legendcup.com/gamesaves.php)
... and what led me to that site was *this* discussion on the possibility of using an N64 Dexdrive with a serial-USB adapter.
[http://s9.zetaboards.com/Nintendo_64_Forever/topic/7069537/1/](http://s9.zetaboards.com/Nintendo_64_Forever/topic/7069537/1/)

---

