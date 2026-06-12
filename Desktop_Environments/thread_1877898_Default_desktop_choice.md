---
title: "Default desktop choice"
date: 2011-11-08
forum: Desktop Environments
---

### Post by Mazate on 2011-11-08
I was recently shown (in this forum) how to make gnome 3 my default desktop.  It was a terminal command which did what it was supposed to do.  However, what command would I use to make Ubuntu load whatever was the last desktop I was using each time I turn on my computer rather than always default to Gnome 3?

---

### Post by Frogs Hair on 2011-11-08
Unity , the Gnome Shell , and Gnome Fall Back Session all run on top of Gnome 3 in 11.10 . I use Unity and the Gnome Shell and what ever desktop was used last is what boots the next time unless the selection is changed in the login screen .

If auto login was in use it would default to unity unless a command was used to change the default . My installation already does what you are asking (I think) with manual login .

---

### Post by Mazate on 2011-11-08
> **Frogs Hair said:**
> Unity , the Gnome Shell , and Gnome Fall Back Session all run on top of Gnome 3 in 11.10 . I use Unity and the Gnome Shell and what ever desktop was used last is what boots the next time unless the selection is changed in the login screen .

If auto login was in use it would default to unity unless a command was used to change the default . My installation already does what you are asking (I think) with manual login .

So if I use auto login (which I do) then I have to choose a default?  (or keep Unity as the default)  It won't just auto login to the last desktop I used before logoff?

---

### Post by Frogs Hair on 2011-11-08
> **Mazate said:**
> So if I use auto login (which I do) then I have to choose a default?  (or keep Unity as the default)  It won't just auto login to the last desktop I used before logoff?

I think auto login will use the default , which is Unity . As I remember with 11.04  the default could be changed from login settings , but that GUI is no longer in gnome 3 . Kind of a catch 22 because how would you choose a desktop when you are automatically logging in .

If you auto logged in to Unity logged out and decided to use the shell and then shutdown I don't know if the shell would be selected at next boot . You could give it a try .

---

### Post by oscarivera9 on 2011-11-08
I think to do what you want it *_is_* necessary to do manual login.  Automatic login is exactly that, it logs you in** automatically** **the** **same** **each and every time. ** If you want to login using the last desktop environment that you were using then the only way to do that is by using the manual login, which is what I do.  I don't mind having to spend the extra 15 seconds to log in so I use the manual login every time.  This also gives me the flexibility to use whichever desktop environment I want when I log in.
Think about it:
> Kind of a catch 22 because how would you choose a desktop when you are automatically logging in .  I have Unity, Unity 2D, Gnome, Gnome Classic, Gnome Classic (no effects), OpenBox, Gnome with OpenBox, and Xfce Desktop Environment available to me when I turn on my PC.  However, unless I want to change my desktop environment, I don't have to decide which one I want, the last desktop environment that I used is automatically the one that loads up every time.
  I am not 100% sure, but I am 99% certain about it.  In other words, maybe someone will prove me wrong, but I really doubt it.  So, if you can then just go back to using the manual login.

---

### Post by Mazate on 2011-11-09
> **oscarivera9 said:**
> I think to do what you want it *_is_* necessary to do manual login.  Automatic login is exactly that, it logs you in** automatically** **the** **same** **each and every time. ** If you want to login using the last desktop environment that you were using then the only way to do that is by using the manual login, which is what I do.  I don't mind having to spend the extra 15 seconds to log in so I use the manual login every time.  This also gives me the flexibility to use whichever desktop environment I want when I log in.
Think about it:
  I have Unity, Unity 2D, Gnome, Gnome Classic, Gnome Classic (no effects), OpenBox, Gnome with OpenBox, and Xfce Desktop Environment available to me when I turn on my PC.  However, unless I want to change my desktop environment, I don't have to decide which one I want, the last desktop environment that I used is automatically the one that loads up every time.
  I am not 100% sure, but I am 99% certain about it.  In other words, maybe someone will prove me wrong, but I really doubt it.  So, if you can then just go back to using the manual login.

Ok, well I just assumed it could be done with auto login because it can be done with Fedora.  However, it's not a big issue in the end.  Thanks for everyone's input.

---

