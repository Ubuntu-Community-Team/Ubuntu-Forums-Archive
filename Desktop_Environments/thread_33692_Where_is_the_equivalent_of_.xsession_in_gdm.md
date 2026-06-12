---
title: "Where is the equivalent of .xsession in gdm?"
date: 2005-05-11
forum: Desktop Environments
---

### Post by bcrowell on 2005-05-11
People have posted on this forum already about the problem with fluxbox being extremely slow to log in. I've seen the info at 
[http://ubuntuforums.org/showthread.php?t=32212](http://ubuntuforums.org/showthread.php?t=32212), but am not having any luck applying it to my situation.

I'm used to having a .xsession file that starts my fluxbox session, but in this ubuntu install, I have gdm (which I've never used before) rather than xdm, and there's no .xsession file, so I'm having trouble figuring out where to put the "export LC_ALL=C". AFAICT from reading the gdm docs, the equivalent would be a script in /etc/X11/gdm/Sessions. Well, in that directory I have only the script /etc/X11/gdm/Sessions/fluxbox, which looks like a script that's actually intended to start fluxbox. However, changing this file has no effect, and I don't think it's even being run. For instance, if I comment out the final line that is actually supposed to start fluxbox, it makes no difference, and fluxbox still starts up. Likewise if I put an 'echo "hello" >~/a.a' in it, it doesn't actually do that when I log in. So is there some script somewhere else that is really what I need to be modifying?

TIA!  :grin:

---

