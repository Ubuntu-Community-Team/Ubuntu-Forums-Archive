---
title: "adding gnome to kubuntu?"
date: 2007-11-11
forum: Desktop Environments
---

### Post by ubuntu.daemon on 2007-11-11
so is there a proper way to add the gnome desktop environment without fraking up your existing kde installation?

---

### Post by kugn on 2007-11-11
Would 
apt-get install ubuntu-desktop

not do the trick?

---

### Post by ubuntu.daemon on 2007-11-11
lol see the thing is i actually installed 
apt-get install gnome
is the proper thing, but then my login screen was using the gdm one for some reason
and it didnt have proper files etc.  It was just being a pain in the ***, so i uninstalled the whole gnome packages, but now i am having issues with i think my java based applications,
azureus, firefox wont let me save anythign, pictures, etc, and picasa is now having issues...
im kinda at a loss bc it was never this hard fofr my desktop with Gentoo, it just worked.....

:mad:
thx in advance lol

---

### Post by kugn on 2007-11-11
I'm afraid I can't help you with that. I have in the past installed other desktop environments using the *ubuntu-desktop meta packages, but never just 'gnome' or 'kde' or 'xfce'. Those times that i installed them i never quite had your problems. The login manager and boot splash would change to that of the new DE (like in your case, from gdm to kdm), but that could be changed. I remember it was through dpkg, but there are other methods. this thread shows another 
[http://ubuntuforums.org/archive/index.php/t-376374.html](http://ubuntuforums.org/archive/index.php/t-376374.html)

In any case, now that you've got a rather broken setup, have you tried reinstalling the apps that you have problems with? like restalling java, firefox, azureus etc? Since you didn't mention that your kde apps have suffered, I suppose in the uninstallation process some of the gnome/gtk packages that firefox depends on are gone. reinstalling those apps might pull them back again.

good luck

---

### Post by bharadwaj on 2007-11-11
Iam not sure and i have never tried this thing. but why don't you reinstall the KDE

---

### Post by asimon on 2007-11-11
> **ubuntu.daemon said:**
> but then my login screen was using the gdm one for some reason

You can switch back to kdm by doing```

dpkg-reconfigure kdm
```
in a console and choose kdm as default login manager. And to return to Kubuntu's boot splash do
```
dpkg-reconfigure kubuntu-artwork-usplash
```

---

