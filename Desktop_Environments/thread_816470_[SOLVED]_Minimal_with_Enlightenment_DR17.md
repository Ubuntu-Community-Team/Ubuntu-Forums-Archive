---
title: "[SOLVED] Minimal with Enlightenment DR17"
date: 2008-06-02
forum: Desktop Environments
---

### Post by Inxsible on 2008-06-02
I installed a minimal with DR17 late last night. Everything went well.

But how do I start the GUI? I tried the normal ```
startx
``` But it said```
startx is not installed. You can install it by installing gnome-init package
```Even a reboot did not bring up the GUI and I can't even shutdown the computer even though i did ```
sudo shutdown now
``` it just comes back to the login prompt.

I do NOT want to install any GDM or KDM on it. I was hoping I would simply do a CLI login and then start the GUI manually. Save me some space on the disk and RAM.

Do I have to install the GDM to be able to get to the Enlightenment desktop ?


EDIT: It suddenly dawned on this dork, that I probably didn't install xorg. It was 4 am last night when I did this. Let me check this tonight and I shall get back either way...

Until l8r....

---

### Post by kellemes on 2008-06-02
> **Inxsible said:**
> 
Do I have to install the GDM to be able to get to the Enlightenment desktop ?


EDIT: It suddenly dawned on this dork, that I probably didn't install xorg. It was 4 am last night when I did this. Let me check this tonight and I shall get back either way...

Until l8r....

:-)
That was my thought indeed..
You don't need gdm, just "startx /usr/bin/enlightenment_startscript" (don't know the name of it)

---

### Post by Inxsible on 2008-06-02
> **kellemes said:**
> :-)
That was my thought indeed..
You don't need gdm, just "startx /usr/bin/enlightenment_startscript" (don't know the name of it)
I installed xorg...and i finally gave up and installed gdm to be able to log in.

I tried ```
startx
enlightenment
enlightenment_start
```all separately of course.... but I guess I will try out what you suggested and see if that works.

---

### Post by Inxsible on 2008-06-02
Sweet !!!

thanks kellemes... I just tried your suggestion and it worked.... I had to give in the path after startx like so```
startx /opt/e17/bin/enlightenment_start
```That's where I installed e17 from cvs.

I uninstalled gdm too... I just think its a waste as its hardly useful after login. Saves a lot of space and RAM on my dino here.

Now to find out how I can run a logon script and add that command to it..so it will be automated.

---

### Post by kerry_s on 2008-06-02
you got it, i just replied on the fluxbox thread on that.

---

