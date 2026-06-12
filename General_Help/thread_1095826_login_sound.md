---
title: "login sound"
date: 2009-03-14
forum: General Help
---

### Post by tempo500 on 2009-03-14
hi i can not turn off the login sound in gnome ubuntu 8.10. i have disabled the login sound in the sound preferences, but it still plays when i login... i searched gconf-editor but no luck... any suggestions? thanks phil

---

### Post by artheus on 2009-03-14
If you are constantly tweaking your setup the way I do, the login sound will drive you crazy after a short while. Of course, if you are constantly tweaking your setup, it's very unlikely that you are reading this article because you already know how to do this.

To change or disable the login sound, go to System \ Preferences \ Sound and click on the Sounds tab.

Change the dropdown to No sound.

taken from:
[http://www.howtogeek.com/howto/ubuntu/disable-the-login-sound-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/disable-the-login-sound-on-ubuntu/")

EDIT: 
and here's a link with a problem more similar to yours:
[https://answers.launchpad.net/ubuntu/+question/21118]("https://answers.launchpad.net/ubuntu/+question/21118")

> The drum sound is actually an audio event handled by GDM (the Login Manager). You can disable this event by going to System -> Administration -> Login Window. Select the "Accessibility" tab, and un-check the "Login Screen Ready" sound event option.

The Other preferences are for Gnome sound events, after the GDM is finished with the login process.

---

