---
title: "gnome won't start - kde having problems"
date: 2005-05-13
forum: Desktop Environments
---

### Post by scriptmonkey on 2005-05-13
I got Ubuntu Hoary installed on my new Dell Inspiron 9300 laptop and everything was going well.  But yesterday when I started it up, I got a gdm screen, at which I typed in my username and password.  Then nothing.  I tried reinstalling gnome, gnome-session, gdm, etc., but nothing worked.  I wound up reinstalling Ubuntu (fortunately, I have /home as a separate filesystem, so this wasn't a huge deal).  So, this morning when I tried to boot up, it did the same thing.  It just sat there.  The hard drive ground for a couple of seconds, but then just stopped.  After reinstalling because of this yesterday, I decided that I'd prefer to not go through this again - especially if this is going to be a regular occurence.  So I installed kubuntu-desktop.  But it froze up, too.  After I rebooted, everything looks OK, but this is really concerning me.  Anyone have any ideas?  


Jeremy Jones

---

### Post by exile on 2005-05-13
When you boot up can you change to a different virtual terminal and get a tail of the logs or a dmesg?

That might give some clues to what is going on.

I'm only guessing here but maybe it is something to do with the power management or adding unusual repositories that broke something that didn't rear it's ugly head until after a reboot?

If you can post some kind of error information that woud be helpful. Maybe changing your session to something other than gnome or kde (say flux?) to see if it is an gnome config thing or something deeper?

Good luck.

---

