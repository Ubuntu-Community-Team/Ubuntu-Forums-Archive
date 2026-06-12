---
title: "&quot;Allow Xfce to manage the desktop&quot; won't stay across sessions"
date: 2008-06-12
forum: Desktop Environments
---

### Post by mksql on 2008-06-12
After an issue where my disk filled to capacity, and some desktop settings got damaged, I have one problem left to resolve.

When I login to an Xfce session, the desktop is initially OK, but then reverts to the default Heron backdrop and a different icon layout. I have to go into Desktop Preferences in the Settings Manager, and re-check "Allow Xfce to manage the desktop". Selecting he save session option on logou does not help.

Is there a config file for this setting that may be damaged?

---

### Post by Xiong Chiamiov on 2008-06-12
Did you start from scratch again, or modify an existing profile?  If the latter, it might be a permissions issue - try making sure your ~/.gnome2 (I believe that's the one used by XFCE) folder is owned by you, and you have read and write permissions.

---

### Post by mksql on 2008-06-12
I am still using the original profile. Checked the ~/.gnome2, and my user is the owner.

---

### Post by Xiong Chiamiov on 2008-06-13
You might try changing the permissions appropriately (even though they should be right), just to apply it down to all the folders within.
```

chmod -R 755 ~/.gnome2

```

---

### Post by mali2297 on 2008-06-13
Do you use Nautilus?

If so, make sure that you start it with the command ```
nautilus --no-desktop
```

---

### Post by mksql on 2008-06-13
> **mali2297 said:**
> Do you use Nautilus?

Thanks, that reminded me that an experiment installing Nautilus occurred right before this problem started. Backing out the unneeded components solved the problem.

---

### Post by Nobby on 2008-07-01
Hi, I am also experiencing this problem where the setting "allow Xfce to manage the desktop" just won't stick.  
I've had ubuntu hardy installed previously (fresh install) and just installed the xubuntu-desktop package.  I've been into the gconf editor and unchecked the option apps/nautilus/preferences/show desktop, and I don't use nautilus anyway.  I've tried creating a new session, with the 'automatically save session on logout' option checked, but nothing seems to work. :confused:

---

### Post by eggkrate on 2008-12-20
Thankyou for this help. I un-installed Nautilus and my problem with Xfce switching to gnome desktop was fixed.

---

