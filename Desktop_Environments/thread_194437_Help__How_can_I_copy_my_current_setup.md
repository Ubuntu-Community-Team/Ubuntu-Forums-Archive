---
title: "Help:  How can I copy my current setup?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by n00buntu NJ on 2006-06-11
I've been playing around with different distro's of linux for the past three months now.  I started out as a windows geek but now I've gone cold-turkey, I sold my windows machine and I'm dedicated to making this work.  

I have installed, uninstalled and reinstalled Breezy/SuSE 10.1/Dapper several times - sometimes because I totally fried my xserver and lost the desktop and others because I just needed to start over and/or try out something different.

I've now become fairly comfortable in command-line mode (as long as I can get a command line - my TV is my monitor and it has this Auto-Sync mode that sometimes won't display the non-windowed environment, so if I lose my desktop sometimes I'm screwed) and now I've got both Dapper and SuSE 10.1 on my machine.  I really love Ubuntu and I'm about to drop the SuSE partition, but my question is this:  Everytime I get XGL/Compiz all setup with the latest and greatest and my desktop all the way I like it with no problems, but then eventually I'll be screwing around with something and I can't get it back to how I had it before...

Is there a way to make a backup of my entire systems settings?  I mean copying everything from / (except for my docs which are on a different HDD) so that I can just dump a mirrored copy onto another partition for backup?

Sorry for being long-winded but I'm really getting tired of having everything working great and screwing it up.

Thanks for any help.

---

### Post by rbalfour on 2006-06-11
image your disk.
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by elbryan on 2006-06-11
Norton Ghost it's a very very nice program to do a 1:1 image for partition/hard disk..
It saved my life many times :P

---

### Post by n00buntu NJ on 2006-06-11
[QUOTE=rbalfour]image your disk.
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)[/QUOTE]

And if I were to do that and copy it to another partition and start it up I would have the very same configuration as I have now?

EDIT:  With the exception of some drive mount points, etc...?  I'll give this a try...

---

### Post by mdurham on 2006-06-11
cp -Rfax / /media/backup_partition
should do it. It takes a few minutes but will save you hours if you screw around.

---

### Post by aysiu on 2006-06-11
Ubuntu-specific PartImage tutorial:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

