---
title: "Cairo dock is a pain in my #$%@^"
date: 2009-11-05
forum: Desktop Environments
---

### Post by Danimal411 on 2009-11-05
I just upgraded to Karmic on my netbook.  I couldn't help myself, even though Jaunty was running perfectly.  I got itchy, ok?

Anyway, I had cairo dock running on the desktop, before it upgraded to the version using openGL.  Now, I can't get it to run correctly either running it with or without openGL.  The preference box opens up at startup, everytime I exit it, it restarts itself.  I grew frustrated and used synaptic to remove everything related to cairo dock.  Now the preferences don't load at startup, but the dock still loads!  I just can't kill this thing.  There is nothing left in synaptic that would support this thing loading up everytime.  I even removed it from startup applications, yet still it persists.  I'd either like to get it working or kill it.

Thanks,

Dan

---

### Post by fabounet on 2009-11-05
first of all, read the message in the dialog box that appears on startup.
It does not appear to ennoy you, but to explain you something ;-)

also, be aware that th eOpenGL version is working on more and more graphic cards (including ATI and Intel), but then you need the cutting edge drivers/X.
in case it doesn't work (yet), the cairo backend is still available with the command :
cairo-dock -c

---

