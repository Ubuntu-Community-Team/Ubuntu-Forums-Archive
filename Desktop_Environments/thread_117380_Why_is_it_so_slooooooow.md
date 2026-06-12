---
title: "Why is it so slooooooow?"
date: 2006-01-14
forum: Desktop Environments
---

### Post by Conrad on 2006-01-14
I just installed ubuntu 5.10 on my machine.

Intel Celeron 2.40 GHz
128Mb RAM
19Gb hard drive.

The desktop is nice but way too slow to be useable.
Example:  While writing this I selected the Calculator.  It took over 45 secondes to
show up!  And then swiching back to Firefox took almost 5 seconds to redraw itself
on top of the calculator.

I used to run Windows XP Pro SP1 on this machine, and everything was fine.

Any ideas?

---

### Post by ritger on 2006-01-14
Lots, is DMA enabled on all drives? Are you using the correct drivers for hardware? Did you check your logs and boot-up stuff to see what went wrong? Did you try google? Did you try to look in a few maillists, or the huge amount of `Tweaking you linux installs'?

That's just a few though ;-)

---

### Post by aysiu on 2006-01-14
[QUOTE=Conrad]I
128Mb RAM[/QUOTE] Why is it so slow? This is why.

128 MB of RAM won't run Gnome or KDE properly, and--in my experience (obviously yours was different)--it barely runs XP either.

Try XFCE4 instead.
1. First link of my sig.
2. ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
3. Log out.
4. Session
5. XFCE
6. Log in.

---

### Post by rado_london on 2006-01-14
Hi
Ubuntu and Linux in general use much RAM rather than CPU. So the problem probably is your amount of memory. If you can upgrade your memory it will be great, if not you can try XFCE as alternative DE.

---

### Post by Mustard on 2006-01-14
Did you change the theme at all?  It's possible that if you changed the theme its affecting things.

-edit-

Apart from the obvious issue with 128mb of RAM, it possible that its related to another issue that I have been reading about....but its hard to tell atm from what little information we have to work with. :)

---

### Post by Conrad on 2006-01-14
Thanks to all who replied.  I also though it was a memory issue.
I was just trying to get free from MS, but it aint' gonna happen anytime soon!
I still can't believe that Windows would require less RAM than any other OS...
Oh well...
Thanks again to all.  At least the Linux community is better behaved than...

---

### Post by aysiu on 2006-01-15
[QUOTE=Conrad]Thanks to all who replied.  I also though it was a memory issue.
I was just trying to get free from MS, but it aint' gonna happen anytime soon!
I still can't believe that Windows would require less RAM than any other OS...
Oh well...
Thanks again to all.  At least the Linux community is better behaved than...[/QUOTE] Why not just use XFCE, as suggested earlier?
It's far less memory-intensive than Gnome or KDE. It'll zip on 128 MB of RAM.

---

### Post by Edho on 2006-01-15
Hello Conrad,
Just for info...

My 1 Ghz , 256Mb RAM , runs fine with Ubuntu-Gnome.

When i look in Applications > System Tools > System Monitor > Resources..

Memory used = 154 Mb.
That is with only two user-programs running.
( System Monitor himself + Opera webbrowser )

So it looks like your 128 Mb - RAM   is to less.


Tip :
Firefox webbrowser 1.07 was verry slow for me.
Installed Opera 9 beta (static).
I think Opera is about 10 times faster then Firefox.

---

### Post by Gowator on 2006-01-15
[QUOTE=Conrad]Thanks to all who replied.  I also though it was a memory issue.
I was just trying to get free from MS, but it aint' gonna happen anytime soon!
I still can't believe that Windows would require less RAM than any other OS...
Oh well...
Thanks again to all.  At least the Linux community is better behaved than...[/QUOTE]
There is plenty of eye candy you can turn off in KDE which would speed it up.  I run linux on a XBOX wirh only 64MB RAM!  However I don't usually use KDE but a lighter weight windows manager.  

Ubuntu and Kubuntu both ship with eye-candy because people complain if its not there ... but you can turn it off.

---

### Post by veloct on 2006-01-15
XFCE, openbox, fluxbox, icewm.  You can try any of those, or you could bump your memory.  Even an additional 128 would be very beneficial.

---

### Post by syklitengutt on 2006-01-15
lol...
do you have a swap partition?

---

