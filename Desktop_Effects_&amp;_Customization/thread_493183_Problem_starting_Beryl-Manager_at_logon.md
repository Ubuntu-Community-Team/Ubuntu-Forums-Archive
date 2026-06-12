---
title: "Problem starting Beryl-Manager at logon"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by kill4killin on 2007-07-05
Hey, I just re-installed Beryl after finding the tutorial on how to do it on the beryl wiki page. I got everything running without a hitch and then continued on to install Emerald Theme manager and Beryl-Manager. The problem I am having is with starting Beryl-Manager at logon. I tried going and doing it the normal way through System > Preferences > Sessions, however, I add Beryl-Manager to the startup and then close the window and when I re-open the Sessions window it is no longer placed in the startup list... I have done this before for other programs so I'm pretty sure it works but it won't with Beryl-Manager.

My question is, how can I get it to start up when I login to my user? I have a launcher on my top panel so I can just click it at login to start it up but I would really like it to start at logon.

Thanks in advance!

---

### Post by notwen on 2007-07-05
Not sure what's stopping your settings from being saved?  Perhaps adding it to your startup, launching Beryl and having your gem icon in your notification area, then saving your session and rebooting?  It's worth a shot, I've noticed alot of odd things revolving around your session not being saved, as far as startup applications go.  Hope this helps. =]

---

### Post by number3pencil on 2007-07-05
I had the exact same problem.  Somehow the permissions were screwed up.  Change the permissions on the folder ~/.config/autostart.

---

### Post by kill4killin on 2007-07-05
What did you change the permissions of that folder to number3pencil?

::EDIT::

Thanks guys, I got it, I just did the following:

```
gksudo nautilus
```

change group permissions of ~/.config/autostart to my user and give full access to the folder

opened up sessions and added Beryl-Manager to the startup

Change group permissions back to how they were before I changed them to avoid problems that might arise later (I figured I can change them back if necessary in the future)

---

