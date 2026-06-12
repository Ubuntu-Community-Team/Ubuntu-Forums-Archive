---
title: "Beryl disaster how do I get back to Metacity?"
date: 2007-03-01
forum: Desktop Environments
---

### Post by otazman on 2007-03-01
My Beryl disaster is complete. I have uninstalled Beryl and Emerald and the GUI still won't load. How do I tell ubuntu to load the Metacity interface on boot up using terminal mode?

---

### Post by Peepsalot on 2007-03-01
You should be able to type "metacity" in a console and have it load up.  Then go in your Session settings and remove Beryl from loading on startup.  You might try killing beryl processes first too.

Edit: sorry, I think I misunderstood you question.  What does it do when you boot up?  Does the login screen load at all?

---

### Post by otazman on 2007-03-01
I ran these two commands:
sudo apt-get --purge remove beryl emerald-themes
sudo aptitude remove beryl

So I think I got beryl removed.

When I try to run metacity I get this error? 
'Unable to open X display'

I have removed beryl from my startup and have restored my original /X11/xconf.config whatever it is called has been restored.

---

