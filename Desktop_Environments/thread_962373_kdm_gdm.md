---
title: "kdm gdm"
date: 2008-10-29
forum: Desktop Environments
---

### Post by lordgibbness on 2008-10-29
Hi all,

I recently installed xubuntu-desktop and kubuntu-desktop on my ubuntu machine which resulted in my splashscreen and desktop manager defaulting to kde.

I successfully changed the shutdown/startup screens back to ubuntu defaults using

```
sudo update-alternatives --config usplash-artwork.so
```

(Although I'm not sure why there is still a + sign next to the kubuntu image)

However, when attempting to change from kdm to gdm using

```
sudo dpkg-reconfigure gdm
```

It doesn't appear to have an affect.  Is there anywhere that I can check manually to see what it is set to?

Thanks,
Rob.

---

### Post by forger on 2008-10-29
perhaps this could sove it:
```
sudo apt-get purge kubuntu-artwork-usplash
```

---

### Post by lordgibbness on 2008-10-29
I'm not having any problems with the startup/shutdown images - it's the login manager which is the problem.

Thanks.

---

### Post by forger on 2008-10-29
I thought that you didn't want kubuntu usplash anymore, my bad :) 

Then try to reinstall the package:
```
sudo aptitude reinstall xubuntu-artwork-usplash
```

Edit: I don't seem to understand, can you rephrase?
usplash and gdm are two different things and different packages..

what did you expect to have? what happened?

---

### Post by lordgibbness on 2008-10-29
No problem...

I installed kubuntu-desktop, which resulted in the kubuntu usplash being displayed and kdm (rather than gdm) being used for logins.

I have corrected the usplash issue; but (as said if first post) when I issue the command to change back to gdm, the change does not take affect, and I am still presented with kdm for logins.

---

### Post by forger on 2008-10-29
ah then, no idea sorry, maybe someone else can help :)

---

### Post by lordgibbness on 2008-10-29
Update: Looking back at the login screen after changing it to gdm, it was actually the xubuntu theme displayed and not kubuntu - sorry!

Seeing this, I changed the theme using System > Administration > Login Window

Cheers.

---

