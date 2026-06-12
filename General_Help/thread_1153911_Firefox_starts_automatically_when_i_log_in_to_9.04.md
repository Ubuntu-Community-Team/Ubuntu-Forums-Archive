---
title: "Firefox starts automatically when i log in to 9.04"
date: 2009-05-09
forum: General Help
---

### Post by j7%&lt;RmUg on 2009-05-09
I have been able to sort out all the problems iv had with ubuntu so far and have been using it since december last year. But for some reason i cant seem to solve this problem no matter what i do.

For some strange reason whenever i log in to ubuntu (9.04 final release) firefox 3.0.10 ALWAYS starts up every time. Iv looked in startup applications and its not listed in there, neither is anything related to firefox. I think it might be related to an anonymous application that seems to always be running. Because when i go to logout using any method it comes up with a dialog box that says that an unknown application is still running and would i still like to logout regardless. Im also using GNOME if that makes any difference. I can provide more information on request.

I really just cannot figure this out even though im pretty experienced with computers it must be my ubuntu experience that is failing me.

All help is greatly appreciated.

---

### Post by pro003 on 2009-05-09
Check: System > Preferences > Startup Applications

...and 'uncheck' Firefox (if there's one, I suppose there is...)

---

### Post by j7%&lt;RmUg on 2009-05-09
Thanks for trying but as i said in my first post i have already checked that.

---

### Post by drs305 on 2009-05-09
This has worked for me on a few persistent apps:

The next time you are about to shut down your computer, close out all applications (if you are really picky you could also run "killall firefox" or whatever firefox process you are running). Once everything is closed, go to the System, Preferences, Startup Applications, Options and select "Automatically remember..." and then log out. That might override the "saved state" info and get rid of the firefox entry. Once you log back on, go back and deselect that setting.

---

### Post by j7%&lt;RmUg on 2009-05-09
Yes! Thats doen it. Thanks man.

All that happened is that yesterday i had checked that option, logged out with firefox still there and logged back in, i then unchchecked that option but it remained in that state. So all i had to do was exactly what you said.

Thanks for your help.

This issue is now solved!

---

### Post by ontwowheels on 2009-05-17
This worked.

What didn't I think of that?  I checked the remember box to make sure it was NOT on, but I didn't think to check it on with no apps running then do a shut down....then uncheck it.

well done....THANKS

---

