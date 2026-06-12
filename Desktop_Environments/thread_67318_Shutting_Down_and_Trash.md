---
title: "Shutting Down and Trash"
date: 2005-09-19
forum: Desktop Environments
---

### Post by gobfrey on 2005-09-19
I have two things that really bug me about Ubuntu Linux, and I think they should be easy to fix, but I've been looking around and can't find the answer.

1)  Shutting down.  I never want to log out.  My machine has only one user.  I turn on, I turn off and occasionally I restart.  But to shut down I have to click system->logout->shut down->OK.  The thing that annoys me the most is that the default action is 'log out'.  For a desktop system I would guess that most home users generally don't want to log out, they want to shut down.  Can I change this default?  I want to be able to access the shutdown with fewer clicks.  Maybe a 'shutdown' icon on the top panel of the screen and a single <OK / Cancel> confirmation.  Alternatively, can I press a key combination (e.g. <ctrl><alt>X) and get it to shut down?

2)  Trash.  I've never wanted it, even in windows.  I'd like the default action of delete to be to delete things.  I don't want to have to worry about the trash.  Sure, sometimes I delete things by accident, but it's my responsibility to make sure what I want to delete is what I delete.  I particularly hate the way the computer creates hidden trash directories on every removable disk I stick in there.  And yes, I know I can <shift><delete>, but it seems the trash applet is using system resources doing something that is not valuable for me.

Adam

---

### Post by John.Michael.Kane on 2005-09-20
this should help with your trash issues  sudo rm -fr $HOME/.Trash/

---

### Post by gobfrey on 2005-09-20
Doesn't that just empty the trash?  I don't want trash in the first place.

Adam

---

### Post by John.Michael.Kane on 2005-09-20
Double click the trash icon you will then click edit-preferences- behavior you will see at the bottom options to bypass said icon..


Hope this helps

---

### Post by gobfrey on 2005-09-20
This adds the option to delete.  I want to get rid of trash completely.

Adam

---

