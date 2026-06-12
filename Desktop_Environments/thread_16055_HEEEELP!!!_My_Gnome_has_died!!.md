---
title: "HEEEELP!!! My Gnome has died!!"
date: 2005-02-18
forum: Desktop Environments
---

### Post by CitricAcid on 2005-02-18
Hello!

X server has started and login screen appeared. I typed my login nad pass.
Then a window appeared saying that my gnome was running under 10 seconds.

I looked into my .xsession-errors and this is what I saw:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "citricacid"
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:4057): WARNING **: Unable to read ICE authority file: /home/citricacid/.ICEauthority 


What to do? (I am a newbie)

---

### Post by kassetra on 2005-02-18
From a terminal, check the permissions on that file:
    
     ```
ls -l /home/citricacid/.ICEauthority
```
    
    As long as it's owned by citricacid and has at least a rw------- then that's not the issue...
    
    If it's NOT owned by you or if the permissions don't say rw------- do this:
     ```
sudo chown citricacid /home/citricacid/.ICEauthority
  sudo chmod 600 /home/citricacid/.ICEauthority
``` 
    
    log out & log back in.  (or try to)

---

### Post by CitricAcid on 2005-02-19
Thanks a lot. Now it works :)

---

### Post by kassetra on 2005-02-19
you're welcome!  I can't even tell you how many times something like that has happened to me!  :)

---

### Post by us3rQUE on 2005-02-26
Does any one know what is the cause of this?

---

### Post by kiddo on 2005-03-14
Oh, I love those forums ;) always find some neat answers out there! Thanks!
Mine was most likely caused by the major crash I had last night, trying to run enemy territory and/or amarok and/or azureus and/or america's army :)

---

