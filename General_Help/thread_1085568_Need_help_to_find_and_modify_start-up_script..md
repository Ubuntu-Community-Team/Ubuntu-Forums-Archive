---
title: "Need help to find and modify start-up script."
date: 2009-03-03
forum: General Help
---

### Post by Chilli Bob on 2009-03-03
OK, long story short, I've installed Intrepid minimal install, and added IceWM (as per Psychocats website).  It's working OK, but I'm having trouble getting my desktop appearance to work.  According to the IceWM FAQ I have to replace "icewm" with "icewm-session" in my start up script.  It also says.....

> In order to run IceWM, you must assure that the executable (called icewm) is in your path. You should then add IceWM to your X start-up script (which could be .xinitrc, .xsession or .Xclients).


So I assume I have to find this script and change "icewm" to "icewm-session", but I can't find .xinitrc, .xsession or .Xclients anywhere.

Do any of these exist, and if so where.  If not, what would be the script I need to find?

Thanks in advance,

Chilli Bob

---

### Post by kilroy423 on 2009-03-03
Hey Chili Bob,

I wasn't able to find .xsession or .Xclients  .  But .xinitrc is located at /etc/X11/xinit/xinitrc .  Good luck!

---

