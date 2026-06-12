---
title: "Can't launch Gnome/Openbox session"
date: 2009-12-29
forum: Desktop Environments
---

### Post by DannyBiker on 2009-12-29
Hello,

I installed Openbox on my Karmic and while the Openbox session works just fine, I can't seem to launch the Gnome/Openbox session. It just go back to the main log screen.

Is there a solution for this ? The problem seems to be known for several distributions now but I haven't find something really up-to-date (understand, for 9.10) and I don't want to mess up with my system files.

Thanks !:)

---

### Post by MooPi on 2009-12-29
Are you logging out then trying to start a Gnome session? You should be using GDM for login. At the bottom of the screen should be a selector that gives you an option to change the session.

---

### Post by bailout on 2009-12-30
Did you get a fix for this? I am thinking of installing ubuntu on my netbook and if gnome openbox would work I would stick with that rather than unr.

---

### Post by sisyphus1978 on 2010-01-01
I was having trouble with this. Installing openbox allowed login to an openbox session, but GNOME/openbox would just loop back to login screen. Basically load gconf-editor and change > Key:
/desktop/gnome/session/required_components/windowmanager
 To value:
openbox
 

---

### Post by MPowers49 on 2010-01-02
> **sisyphus1978 said:**
> I was having trouble with this. Installing openbox allowed login to an openbox session, but GNOME/openbox would just loop back to login screen. Basically load gconf-editor and change

Having the same problem.  Openbox session works ok, but I loop back to the login screen when I pick Gnome/Openbox.  Tried the above suggestion. No luck.

---

### Post by buddyd16 on 2010-01-25
I have the same problem does anyone have a solution?

---

### Post by J V on 2010-04-08
Severely gimped asking for help :?

---

