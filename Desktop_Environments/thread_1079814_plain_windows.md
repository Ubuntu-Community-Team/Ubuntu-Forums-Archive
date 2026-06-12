---
title: "plain windows"
date: 2009-02-24
forum: Desktop Environments
---

### Post by Dawei87 on 2009-02-24
hey, i just did a fresh install of ubuntu and installed the slickness black theme. everything is fine on most windows, except windows like synaotic, startup manager, login window, and pretty much everything from the system tab does not have a theme at all. they open with very ugly colors and buttons. is there anyway to make these windows blend in with my theme again?

---

### Post by k3ttc4r on 2009-02-24
it's supposed to be like that, to eleminate security risks, since those windows are run with root privileges.

so you see - you shouldn't have them open long enough to be disgusted by the way they look, anyways :D

---

### Post by Dawei87 on 2009-02-24
the way it used to be, all those windows would blend in with my current theme, but then if i wanted to run nautilus with root permissions, the icons would look different (ugly). I liked that setup, cause all my windows matched, but if i had a root nautilus window open i could always tell and would screw anything up.

---

### Post by denham2010 on 2009-02-25
What you need to do is set a theme for the root user. Currently, your theme is set for your username, and root has it's own.

To do this:

```
ALT + F2
```

and enter:

```
gksu gnome-appearance-properties
```

enter your root password and now you can change the root theme.

Cheers.

---

### Post by mcduck on 2009-02-25
You have installed your themes in your personal theme directory, while those programs run as root user (who doesn't have the themes). That's why root apps use default theme instead.

If you want  root apps to always have the same theme you are using, there's an easy trick to do this:
```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```
Running these commands links your theme & icon directories into root's theme and icon directories. So now root always has same themes available you have. :)

---

