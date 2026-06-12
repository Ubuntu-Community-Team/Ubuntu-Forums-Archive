---
title: "How to truely kill beryl?"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by narnie on 2007-05-11
I'm trying to switch users after first killing beryl because both users start beryl by default.

This seems to have worked before, but not now. 

I have first tried by using beryl-manager to change to metacity, then killall'd beryl-manager, beryl, and emerald.

When I then try to switch users (after I have to fix the mouse not moving by changing to a nongraphical tty and back to the GUI tty [any ideas on how to solve that, too?]) it tries to start up the new user that also calls beryl on startup. I see everything working fine until it tries to start beryl-manager. It then crashes that session and goes to the switch user dialog with the original user where I can sign back on, or again, try to switch users. I can switch to a non-beryl user just fine.

I have also made a script to kill the above and start metacity automatically. It still will crash on the next beryl user's session.

Any ideas? Is/are there any other process(s) that I need to kill to remove any vestige of beryl before trying to start it on another user?

TIA,
Narnie

---

### Post by gigaferz on 2007-05-15
hello, i have been experiencing a lot of problems with beryl too,

since you can actually log into your computer, 

why dont you uncheck the option to save changes to your session, 

I set up my computer to change sessions, now a friend used beryl, and it broke my system.

now Also there is the start up manager and the Boot up manager, and you could try installing them, to prevent beryl from starting.

I have been reading alot and it looks like its a edgy issue....

---

### Post by narnie on 2007-05-16
I would like Beryl to start up auto. I actually added it to my startup list. What I want is to know how switchuser works. I'm thinking it is part of the screensaver app. I'd like to kill it on userswitch and, preferably, start it again.  Basically, make beryl available to the current X server user.

I really like beryl and want it up. So, if I lock my session and the kids want to get on (they like beryl, too), I'd even run a script before switching users to kill all of beryl, but it seems there is something of it left even when I kill beryl, beryl-manager, and emerald. I don't know what else may be attached to beryl that is crashing.

I hope they make the next upgrade multiuser.

I'd love to incorporated into my script the switching of users, but I don't know how to initiate it.

---

### Post by gigaferz on 2007-05-20
why dont you launch htop?

then launch beryl and see all the new porcesses, so you can adjust your script properly.

Thanks to this, I found out firefox was using a lot of cPu power, so I just use something else,....hope this helps a little.

When I had beryl, even when I closed the program, the effects didnt go away...

Maybe ts needed to change the window manager to metacity, and disable the effects manually...

---

