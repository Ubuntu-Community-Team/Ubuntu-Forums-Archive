---
title: "How to start &quot;xubuntu xfce4&quot; instead of stock xfce4"
date: 2011-12-14
forum: Desktop Environments
---

### Post by stevenmnance on 2011-12-14
When starting a new x head from command line how to I start up the xubuntu styled xfce4 instead of the stock one?

I've tried startxfce4 and xfce4-session both resulting in the stock xfce environment.

If it matters this is over an x2go connection.

Thanks in advance.

---

### Post by 3Miro on 2011-12-14
There is only one xfce. If you have installed xubuntu-desktop, then you are running "xubuntu's" xfce. The difference between xubuntu-desktop and xfce4 is that xubuntu-desktop comes with xfce4 + some default settings + some extra packages and tools.

---

### Post by LewisTM on 2011-12-14
It's true that launching startxfce4 is equivalent to choosing 'Xfce session' in the login manager, whereas there is no easy way to launch the 'Xubuntu session' from the CLI.

It has always been a mystery to me why there would be two very similar session choices. They both launch the same desktop with the same apps and same panels but the styles may be subtly different: colors, wallpaper, fonts, icons.

In your case just stick to the Xfce one and set it up to your liking.

---

### Post by mikodo on 2011-12-14
Good to know.

---

### Post by stevenmnance on 2011-12-14
Interesting, so how are the settings stored then? How does ubuntu launch the "xubuntu session"?

Also, if there is no way to start the xubuntu session from command line will session settings be persisted through logins with xfce4 as long as I continue to use the same user?

---

### Post by LewisTM on 2011-12-15
After experimenting a bit, I found that after using startxfce4 or the Xfce session login, I end up with a slightly different desktop. Looks like the default Tango Ubuntu theme.

However, once I make changes to the appearance, they get applied to both the Xfce and Xubuntu sessions. From then on, they look the same. So really, there is no need to worry. If it's a bug, it's the smallest I've ever seen.

---

### Post by gmargo on 2011-12-15
Try this:  Instead of using **startxfce4**, use **startx** and the **DISPLAY_SESSION** environment variable.

```

env DISPLAY_SESSION=xfce startx

-or-

env DISPLAY_SESSION=xubuntu startx

```After X comes up, check your XDG_CONFIG_DIRS and XDG_DATA_DIRS environment variables.

xfce will have:
```

XDG_CONFIG_DIRS=[COLOR=Red]/etc/xdg/xdg-xfce[/COLOR]:/etc/xdg:/etc/xdg
XDG_DATA_DIRS=[COLOR=Red]/usr/share/xfce[/COLOR]:/usr/local/share/:/usr/share/:/usr/share

```while xubuntu will have:
```

XDG_CONFIG_DIRS=[COLOR=Red]/etc/xdg/xdg-xubuntu[/COLOR]:/etc/xdg:/etc/xdg
XDG_DATA_DIRS=[COLOR=Red]/usr/share/xubuntu[/COLOR]:/usr/local/share/:/usr/share/:/usr/share

```

---

### Post by LewisTM on 2011-12-15
Interesting.

On my system:
1) Using startx fails. I have to use startxfce4. Setting the variable (e.g. env DISPLAY_SESSION=xfce startxfce4) does nothing and the variables set later are /usr/share and /etc/xdg alone

2) Choosing the Xfce vs Xubuntu in LightDM does set the environment variables as described

BUT

3) /etc/xdg/xdg-xfce and /usr/share/xfce don't exist!

So that might explain why we get a plain looking, default Xfce desktop upon first entering the Xfce session. Looking at the Xubuntu-specific directories, they seem to contain some extra default settings. Nothing critical but it might be a good idea to simply create symlinks from them to the missing xfce directories.
```
sudo ln -s /etc/xdg/xdg-xubuntu /etc/xdg/xdg-xfce
sudo ln -s /usr/share/xubuntu /usr/share/xfce
```

---

