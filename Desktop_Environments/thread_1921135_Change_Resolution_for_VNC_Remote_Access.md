---
title: "Change Resolution for VNC Remote Access"
date: 2012-02-06
forum: Desktop Environments
---

### Post by rollin77 on 2012-02-06
I have a PC at home running Ubuntu 10.04 desktop edition that I can remote into from my laptop at work, but I want to change the screen resolution to better fit the screen on my laptop.  I'm remoting in via an SSH tunnel, then using TightVNC viewer to give me a GUI screen.

The PC at home is not yet setup as a headless server, so in order for remote GUI access to function I have an old LCD monitor connected directly to the PC, (otherwise I can't remote in via TightVNC if this is not plugged in).  The problem is that the home PC's LCD monitor's resolution is 1280 x 1024, while my laptop's resolution is 1440 x 900.  This means if I leave it at full resolution the bottom portion of the screen is cutoff when using my work laptop to remote in.  The next resolution down that will fit in my laptop's screen is 1024 x 768, but it's a little too small so if it's possible I'd like it to match my laptop's 1440 x 900 screen completely.

Can anybody give me some tips on how to accomplish this?  I'm not too concerned about setting the PC up as a headless server, but if you have tips on that as well I'd be happy to get that working as well.  I could be wrong, but when I setup a headless server a while back on a different PC there was a place to edit the screen resolution size and that allowed me to change it to fit whatever screen I'm remoting from.

---

### Post by Blue Dude on 2012-02-08
I'm doing exactly the same thing.  I would also like to see some way of changing resolutions on the fly.

I'd settle for setting up a headless X server at the laptop resolution for every day work though.

---

### Post by rollin77 on 2012-02-21
bump anybody?

I'd also like to be able to change the resolution on the fly as Blue Dude mentioned if that is possible, but that isn't really too important since I mostly just remote in from my work laptop.

---

