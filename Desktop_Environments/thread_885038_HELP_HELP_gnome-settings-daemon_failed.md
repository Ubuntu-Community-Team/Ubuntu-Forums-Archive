---
title: "HELP HELP gnome-settings-daemon failed"
date: 2008-08-09
forum: Desktop Environments
---

### Post by 4t0m1c_w07f on 2008-08-09
I just recently setup my dual display and after a while of using both screens, the gnome-settings-daemon failed and reverted to some ugly theme..

Here is the output from the terminal:
```

jared@4t0m1c_w07f:~$ gnome-settings-daemon 

** (gnome-settings-daemon:7482): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:7482): WARNING **: Could not acquire name
jared@4t0m1c_w07f:~$ 
```

**Please HELP!**

---

### Post by ploum on 2009-08-17
Look in your /etc/hosts file.

If you see :

127.0.0.1 localhost
127.0.1.1 my_name

Change it to :

127.0.0.1 localhost my_name


I know, this is pure non-sense but it seems to fix the issue.

---

### Post by juliobahar on 2010-10-15
> **ploum said:**
> Look in your /etc/hosts file.

If you see :

127.0.0.1 localhost
127.0.1.1 my_name

Change it to :

127.0.0.1 localhost my_name


I know, this is pure non-sense but it seems to fix the issue.

Wow this is massive. How on earth did you get to this solution? I'm impressed!!
By the way, I another thing to do to fix some screwed up and missing gnome files like when I mistakenly deleted gnome.panel, is:

```

sudo apt-get install gdm ubuntu-desktop
```

This occurred to me when I wanted to completely remove evolution from my ubuntu box

---

### Post by getut on 2010-10-15
> **ploum said:**
> Look in your /etc/hosts file.

If you see :

127.0.0.1 localhost
127.0.1.1 my_name

Change it to :

127.0.0.1 localhost my_name


I know, this is pure non-sense but it seems to fix the issue.

Ughh.. how do I get this fix to stay? I was having a similar issue ([http://ubuntuforums.org/showthread.php?t=1592561](http://ubuntuforums.org/showthread.php?t=1592561)) with gnome-settings-daemon and tried this as a possible fix. I wasn't getting any error and g-s-d startup but my hosts looked similar to what you posted so I tried it anyway.

Long story short, network manager keeps partially undoing the changes I make and partially setting it back to the way I was before the change, NOW I get the error that you post but its my own doing.

---

### Post by getut on 2010-10-15
NM.. I figured it out. Only g-s-d's that I try to open after the first one start throw the error. If the one I am starting will be the first or only one to run, then it runs with no errors at all.

At least I'm back to where I started now. Theming still isn't working but no hosts file related errors.

---

### Post by juliobahar on 2010-10-15
> **getut said:**
> Long story short, network manager keeps partially undoing the changes I make and partially setting it back to the way I was before the change, NOW I get the error that you post but its my own doing.

Have you tried this
```
sudo apt-get install gdm ubuntu-desktop
```

I can't explain what has network manager got to do with your /etc/hosts file.
We need more information about your error.
Thanks

---

