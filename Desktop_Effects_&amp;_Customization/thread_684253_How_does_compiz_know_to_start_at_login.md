---
title: "How does compiz know to start at login"
date: 2008-01-31
forum: Desktop Effects &amp; Customization
---

### Post by eteq on 2008-01-31
This is a relatively simple concept, but I can't seem to find anything that spells it out: In Ubuntu Gutsy, how does compiz know when/how to start? 

The reason for my question is that I want to setup some scripts to startup compiz with different command-line arguments (or at different paths), but I can't figure out what GNOME uses to know how to start compiz when it first logs a user in.  Is it some script somewhere, or something in the Sessions panel?

This seems fairly straightforward -- any help is appreciated.

---

### Post by eteq on 2008-02-09
No one knows the answer to this?  Doesn't it seem like a fairly basic thing?

---

### Post by kshane on 2008-02-10
> **eteq said:**
> No one knows the answer to this?  Doesn't it seem like a fairly basic thing?

I'm surprised that you haven't gotten an answer before now...    :confused:

Go to System>>Preferences>>Sessions.  It's pretty self-explanatory from there...  Hope this helped!

Kevin

---

### Post by eteq on 2008-02-10
I figured that was where to go, but it's not clear to me how to change the settings for the default session - I can have it clone my current session, but I don't necessarily want to do that - just change the command line parameters (or, alternatively, the path) for compiz, and it's not obvious how to do that in the sessions panel... is there something missing there to allow me to edit the session entries?

Thanks for the response, though!

---

### Post by benerivo on 2008-02-10
Just a guess, but maybe something here...

/home/ben/.gconf/desktop/gnome/applications/window_manager/%gconf.xml

---

