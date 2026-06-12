---
title: "Altering the default desktop"
date: 2007-03-17
forum: Desktop Environments
---

### Post by kesomir on 2007-03-17
I'm the ICT Coordinator at a UK primary school and I've been slowly moving the IT systems towards open source. Lots of OS running behind the scenes and on the windows desktops. The next phase is to start introducing Linux Desktops as a replacement for the Win XP ones.

To that end I have converted one of the "open to all" staff machines which is mostly used for web and open office in an attempt to butter up users with speed and eye candy over the windows alternative.

I have beryl set up and working fantastically on the intel 950 graphics, found the instructions on the beryl site to make beryl load for all users and tests this works with new user accounts.

**What I want to do now is alter the new desktop template to change the theme, wallpaper, icons (possibly the beryl settings) etc so that new users / all users get by default the settings I configure** (I'm not looking to lock the desktop at this stage, just customise the template). 

So.. Any ideas? I've had a less than fruitful search of forums, google etc.

The step after this is to authenticate against the AD server so they can log into their accounts and access files from the ubuntu box without me creating local accounts.

Any help appreciated.

---

### Post by kerry_s on 2007-03-17
I believe desktop templates can be set in /etc/skel. I think you just copy the stuff to there and everything in there is added to new accounts.

---

### Post by kesomir on 2007-03-17
I forgot to specify that the DE in use is **gnome.**

I've had a quick look in /etc/skel/ but could only see a linked folder "examples" with a few odt files, graphics and the ubuntu movie.

I don't see where I can alter the default wallpaper, icon set and theme that way - I was thinking there may be a config file somewhere with these parameters set since edubuntu changes the default user account from ubuntu.

EDIT: I've stumbled onto a gnome admin guide at gentoo which looks promising:

[http://gentoo-wiki.com/HOWTO_Gnome_Desktop_Admin_Guide](http://gentoo-wiki.com/HOWTO_Gnome_Desktop_Admin_Guide)

EDIT2: using gconf-editor as root will enable you to right click on options and make them default or mandatory  - WOOT. I hope this is useful for someone else.

Thanks for the /etc/skel tip kerry_s - will be useful for placing defaults into home folders (will see later what effect it has on AD homes).

---

### Post by Patrick-Ruff on 2007-03-17
thanks, this will definately be useful to me.

---

### Post by mcduck on 2007-03-18
There are also GUI tools for this kind of things, Pessulus and Sabayon. Pessulus is for locking things down, while Sabayon is for managing the desktop settings for users&groups.

---

### Post by kesomir on 2007-03-18
I'd heard of sabayon, but not pessulus, will check that out.

gconf-editor is a GUI tool though, v. easy to use but seems to be a little buggy - Some of the options I set to mandatory become unwriteable so you can't change them.

---

