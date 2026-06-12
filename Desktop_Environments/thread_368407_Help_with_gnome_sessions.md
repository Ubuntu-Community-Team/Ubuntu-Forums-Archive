---
title: "Help with gnome sessions"
date: 2007-02-23
forum: Desktop Environments
---

### Post by DefectiveHW on 2007-02-23
Hi I am having some trouble setting up sessions in gnome.  I would like to have a choice of 2 sessions at login, one with beryl one without.

I have created a couple of sessions in the session manager I assume I need to then log off and back on with the other session to re configure it.

How do I select one of the sessions I have created?  When I click on sessions at the bottom left corner of the login screen I get a few options 

Last session
Gnome session
Gnome failsafe

but I don’t see either on the ones I created.

Any ideas?

---

### Post by louis_nichols on 2007-02-23
Sessions you see on the boot screen and sessions you see under System>Preferences>Sessions are 2 different kinds of sessions. Well, not entirelly...

You can add entries in the folder /usr/share/gnome/ and select from them on the login screen. So for example you can make a file:

/usr/share/gnome/beryl.session

and edit that to contain the command beryl-manager (I'm not sure about the syntax right now, but it should be pretty intuitive). Then, you can select it at login and beryl-manager will start. And you can have another session

/usr/share/gnome/no-beryl.session

without the command for beryl-manager, so it won't start beryl (obviously).

All these login options will be available to all users.

The settings under System>Preferences>Sessions are user-specific and they can only add features to the ones already set under /usr/share/gnome/*.session but cannot prevent a feature from executing.

---

### Post by DefectiveHW on 2007-02-23
That makes sense.


Thanks :)

---

