---
title: "Auto gamma correction script"
date: 2008-12-30
forum: General Help
---

### Post by dwalker0044 on 2008-12-30
Hi everyone,

I recently brought a new monitor which, by default, has awful gamma settings. I solved my problem initially by using xgamma in a terminal. Later I wrote a bash script which I can execute to do this automatically. What I would like to know is if there's a way to either:
[LIST=1]
[*]change the defaults of xgamma
[*]execute the script automatically on startup
[/LIST]

Thanks in advance for you help!

BTW: the monitor doesn't allow fine tuning of the individual gamma settings before you suggest that ;)

---

### Post by dwalker0044 on 2009-01-03
Anyone? Have I posted in the wrong area?

---

### Post by Aearenda on 2009-01-03
I've never used xgamma, but a look at its man page suggests that you can't change its defaults, and that you need to call it at logon rather than at startup.

I think I'd try adding the script you have made to the session startup - go to system->preferences->Sessions and hit the 'Add' button, give the new entry a name and then set the path to your script in the command area. After that it should run the script every time you log on.

---

