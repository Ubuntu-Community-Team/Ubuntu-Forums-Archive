---
title: "Gutsy Boots to Command Line. Unable to Start GDM"
date: 2008-06-06
forum: Desktop Environments
---

### Post by dee_kay on 2008-06-06
The problem started yesterday.  I'm not sure if this is the place to post this so if mods want to move this, feel free.

My problem is this . . . 

I boot, via the default option in GRUB and get the splash screen (orange loading bar and Ubuntu logo).  Before this I'd then get the login screen and then the beige screen for a bit (I think that's the right sequence)and then the gnome desktop would appear.

Now I get a command line and a login prompt.  I can enter my uid and pw to login but I can't start GDM using any of the methods I've seen suggested.

I've tried 

# startx
# sudo /etc/init.d/gdm start

I'm away from my laptop right now and I'can't recall whether they failed quietly or spat some errors.

Any suggestions would be gratefully received.

Rgds,
Dave

P.S.  I noticed that when I arrive at the command line I am tty3.  Not sure if that's relevant.

---

### Post by ibutho on 2008-06-06
To better diagnose the problem, run "sudo /etc/init.d/gdm start" and post back the error messages.

---

### Post by benerivo on 2008-06-06
You could also try to reinstall gdm with```
sudo apt-get --reinstall install gdm
```

---

### Post by dee_kay on 2008-06-06
> **benerivo said:**
> You could also try to reinstall gdm with```
sudo apt-get --reinstall install gdm
```

I'll try this when I get home later but part of my problem is that sudo apt-get <anything> isn't working for me.  I can't remember how it errors though.

Thanks,
Dave

---

### Post by dee_kay on 2008-06-06
> **dee_kay said:**
> I'll try this when I get home later but part of my problem is that sudo apt-get <anything> isn't working for me.  I can't remember how it errors though.

Thanks,
Dave

Okay . . . tried the above at the command prompt in tty1.

#sudo apt-get --reinstall gdm

Result is

> apt-get: error while loading shared libraries: libapt-pkg-libc6.6-6.so.4.5: cannot open shared object file: No such file or directory 

I also tried:

#sudo /etc/init.d/gdm start

and the result appeared to be nothing.  I was just returned to the command line.

Does this help?

Thanks,
Dave

---

