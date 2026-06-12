---
title: "Ubuntu Studio and Desktop Effects/Compiz"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by the_lex on 2007-07-18
Hello gang,

I am running Ubuntu Studio on my IBM ThinkPad, and I would really like some of that pimp-tastic Compiz action for myself. I have checked the sole post on this topic and it lead to near-flaming so I'm a bit apprehensive about asking, but anyway:

Enabling Desktop Effects wrecks all my windows and leaves me on the white screen until the response time runs out and it defaults back to normal. I have tried booting with the 2.6.20-16-generic kernel as well as the low-latency build just to check it's nothing to do with this. I know Desktop Effects are compatible with my Intel card as they work in regular Ubuntu Fiesty off the Live CD. I do dabble in audio work so I wanted studio, though I'd like the prettiness when I'm not working on audio. 

Furthermore, I can't seem to get Compiz to properly install. I've installed all the packages and dependencies through package manager (Compiz-GNOME, Compiz-Core etc.), but it's not in my menus and I don't know how to access the settings through terminal without running the compiz --replace command which gives me the white screen issue again.

Help on these issues would be very much appreciated! Thanks :)

---

### Post by hyperair on 2007-07-18
I hear that the "intel" driver has some problems. So here's something: 
Run this command:
```

sudo dpkg-reconfigure xserver-xorg

```

Answer the questions, and when it asks you what driver to use, select the i810 driver instead of the intel driver. Then just press enter all the way unless you know what you're doing.
After that you'll have to restart your X server (Ctrl+Alt+Backspace)

---

### Post by the_lex on 2007-07-18
Tried it and it didn't work. First it killed Nautilus, and I still get the white screen when enabling desktop effects :(

Thanks for the quick reply anyway, much appreciated

---

### Post by linuxuser/palmprogrammer on 2007-07-25
I think you installed the wrong packages. That's probably not the problem, though. You should edit /etc/X11/xorg.conf and replace your card's driver (somthing like vesa maybe) with i810. At least that worked for me.

Dont forget to restart X! Ctrl+Alt+Backspace

Look around-this is a VERY common problem.

---

