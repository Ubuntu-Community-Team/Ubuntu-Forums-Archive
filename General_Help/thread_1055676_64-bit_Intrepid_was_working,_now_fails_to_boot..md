---
title: "64-bit Intrepid was working, now fails to boot."
date: 2009-01-30
forum: General Help
---

### Post by mjpatey on 2009-01-30
Hi, group-

I just tried booting into my 64-bit Ubuntu 8.10 install... during boot, I start to see the Ubuntu usplash animation, then it backs out to  some text:

> Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/b2c26272-2888-4963-9035-74dde0f182ca) = dev(8,6)
kinit: trying to resume from /dev/disk/by-uuid/b2c26272-2888-4963-9035-74dde0f182ca
kinit: no resume image, doing normal boot...

Ubuntu 8.10 mjpatey-desktop tty1

mjpatey-desktop login: mjpatey
Password:
init: tty1 main process (3680) killed by SEGV signal
init: tty1 main process ended, respawning

Ubuntu 8.10 mjpatey-desktop tty1

mjpatey-desktop login: _As you may be able to tell, I attempt to log in as myself, then type my password, and it responds by saying it was killed by a SEGV signal, and respawns tty1, asking me for username and password again.  This continues as an endless loop if I keep trying to log in.

So I'm stuck without the ability to boot into my 64-bit Intrepid install.  I want to at least try "startx", but I can't get to a command prompt, because I can't log in.  I tried booting to an earlier kernel, but that doesn't work, either.  I do have a 32-bit install that I can fully boot into; it and the 64-bit install share a /home partition, so all is not completely lost, thankfully.

Still, I want my 64-bit install back... any idea what to do?  Thanks in advance for any light you can shed!

-Mark

---

### Post by mjpatey on 2009-01-31
Just a couple of notes... I am able to access the partition that my 64-bit installation lives on, by booting to the 32-bit OS.  I can see and edit all the files, etc., but don't know what needs to be done.

Also, I tried booting to the 64-bit OS in "recovery" mode, and even got to a root command prompt.  I tried "startx", but to no avail.  Every time I try to do something from a root prompt, it fails, saying this is a read-only filesystem.

Indeed, when I tried repairing the X server and repairing broken packages, the system was unable to download files, copy files, etc., because the filesystem is supposedly "read-only".  This looks like it might be the source of the problem, but I don't know why it's the case.  Any idea how to fix it?

Thanks in advance!

-Mark

---

### Post by studavis on 2009-03-10
Hi there, did you ever find a solution? My 8.10 32 bit has just locked me out..  entering user name/password returns "killed by SEGV" and then just loops back to login. It's worled fine for months.

Help! I've had many problems with Ubuntu/OO 3 and I think this is the last straw. Pity...

---

### Post by mjpatey on 2009-03-10
You know, I think I just re-installed.  I tend to over-tinker sometimes, and break things!  Fortunately, if you have a live CD you can boot into it, copy your important documents to somewhere safe, and re-install.

I'm sure there is a "real" solution to this problem somewhere, but I'm not advanced enough to know what it is.

Hope you get things back in working condition soon!

-Mark

---

### Post by studavis on 2009-03-11
Thanks for the reply. All attempts to recover my files using from the various Windows applications to read Linux files(I'm dual boot, thank goodness!), failed, perhaps cos it was a Wubi install. 

Eventually made a USB 8.04 which seemed to work better than 8.10 (better choice of screen resolutions for a start) and could recover my files with the exception of the e-mail files. 8.04 would not let me access, permission denied. Guess it was looking for original user/password. Not being able to find a way round that, I read (in this forum), if you unistall Wubi, it will ask you if you want to save the home folder. Don't believe that, it's now gone for good....
And with this last episoede sadly my 3 months with Ubuntu must come to an end as well. Not worth the risk in a working environment.

PS - I know I'll probably try again, I'm a tinkerer too and I really liked working with Ubuntu and OO3 despite it wiping out all the table in a document that HQ sent me...

---

