---
title: "desktop theme not inherited by some applications"
date: 2007-11-09
forum: Desktop Environments
---

### Post by realthor on 2007-11-09
Hi,  my configuration in the Appearance Preferences is royale blooper as the Controls tab theme and Human for Window Border. The problem is that some applications like Synaptic and others from System>Administration panel seem to not inherit the Human theme and look like they use the Raleigh Controls theme. For all the other applications the look and feel for the controls (menus,buttons,etc) is Human-like (which is defined in the Window Border tab of Appearance Preferences). If I choose Human also in the Controls tab the look of these apps is ok.

Do anyone have any ideea why with installed themes (because for me it happened with all themes that did,'t come default) some applications don't take the Human-look, defined in the Window Border?

Thanks,

    realthor.

---

### Post by Denis on 2007-11-09
Normally when you want the programs you run as a root to look like the rest, you have to chose the same theme for the **root user**.  

gnome-appearance-properties is the program you use to change themes. 
So if you run "sudo gnome-appearance-properties", you can set the theme for the root user. 

I hope this solves you problem.

---

### Post by Johan_SV on 2007-11-12
It's better and cleaner to set up these symlinks:

```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

Make sure to insert your username on the right places.

---

### Post by Palmyra on 2007-11-25
Since people do not normally run as root, root should automatically assume the theme preferences for the default user.  It makes no sense to separately identify a theme for root, considering the fact that root is not used as often as the default user.

I should probably report this on Launchpad.

---

### Post by man40 on 2007-11-28
or you could just copy your themes and icons in
/usr/share/themes
/usr/share/icons
they will become available for all users including root
...just like human theme :)

---

### Post by Whiffle on 2007-11-28
The problem is that the settings for roots theme preferences are in /root, and yours are in your home directory.  You can't write the ones in /root without using sudo, which is why I don't think it will ever happen.  You could do those symlinks above and maybe copy .gconf (i think) into /root and it should take the settings along.

---

### Post by mcduck on 2007-11-28
> **Palmyra said:**
> Since people do not normally run as root, root should automatically assume the theme preferences for the default user.  It makes no sense to separately identify a theme for root, considering the fact that root is not used as often as the default user.

I should probably report this on Launchpad.

The themes would work if you installed them system-wide, into /usr/share/themes. But if you install them into your home directory it's normal behavior that they are only available for your user, not others.

The system is already assuming that graphical applications run as root should have the same theme, it just can't find the theme in root's .themes -directory or in /usr/share/themes. Creating those symbolic links mentioned here will make the themes installed in your own .themes available for root as well.

---

### Post by GaryUK on 2008-01-05
> **Johan_SV said:**
> It's better and cleaner to set up these symlinks:

```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

Make sure to insert your username on the right places.

I found this quite useful but it did not fix my problem with my window borders missing on Synaptic only. After a lot of head scratching I tried the following:

```
sudo ln -s /home/<insert your username here>/.emerald /root/.emerald
```

This seemed to fix the problem once I restarted the X server as I am using emerald as the window decorator.

Thanks Johan_SV !! :)

---

### Post by Carbonfish on 2008-01-05
Hi all,

I just wanted to thank Johan V as well as I just upgraded to Gutsy (for the second time, but that's another story) and my themes weren't persisting after reboot. After taking Johan's linking advice, all seems well theme-wise.

Thanks!

KC

---

