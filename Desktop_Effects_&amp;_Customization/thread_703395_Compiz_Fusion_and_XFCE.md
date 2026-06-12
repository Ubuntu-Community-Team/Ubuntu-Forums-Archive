---
title: "Compiz Fusion and XFCE"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by ed3120 on 2008-02-21
I just replaced Gusty with the newest version of Mythbuntu, which has an XFCE desktop.  I had Compiz Fusion running on Feisty w/ Gnome and I was wondering how I can enable the desktop effects (wobbly windows, etc) in XFCE.

---

### Post by Dark Star on 2008-02-21
Have you installed Compiz Settings manager if not install it .. open the terminal and type

```
sudo apt-get install compizconfig-settings-manager
```

Open CCSM by pressing ALT+F2 and type ccsm .. It will open the settings manager .. Select the plugins you want to enable and it wil work for you ;)

Hope it helps
Regards

---

### Post by sisco311 on 2008-02-21
in xubuntu compiz is not installed by default you can install it:

```
sudo aptitude install compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins compizconfig-settings-manager libcompizconfig0 python-compizconfig
```to run compiz press Alt+F2 and type: compiz --replace

go to Aplications -> Settings -> Advanced Desktop Effects Settings an select your plugins you want

to autostart compiz edit your session file:

```
gksu mousepad /etc/xdg/xfce4-session/xfce4-session.rc
```and replace
> Client0_Command=xfwm4with
> Client0_Command=compiz

---

### Post by ed3120 on 2008-02-24
> **sisco311 said:**
> in xubuntu compiz is not installed by default you can install it:

```
sudo aptitude install compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins compizconfig-settings-manager libcompizconfig0 python-compizconfig
```to run compiz press Alt+F2 and type: compiz --replace

go to Aplications -> Settings -> Advanced Desktop Effects Settings an select your plugins you want

to autostart compiz edit your session file:

```
gksu mousepad /etc/xdg/xfce4-session/xfce4-session.rc
```and replace
with

I did all of the above, and I can access Advanced Desktop Effects Settings and check/uncheck the various options, but I never actually see any effects.  I edited the session file to autostart and rebooted and I still don't see any effects.  I've also tried starting compiz manually and I get the same result.

I'm using the nvidia restricted drivers.

---

### Post by ed3120 on 2008-03-04
> **sisco311 said:**
> to autostart compiz edit your session file:

```
gksu mousepad /etc/xdg/xfce4-session/xfce4-session.rc
```and replace
with

I can get compiz started with "sudo compiz --replace" but I for some reason editing the xfce4-session.rc file is doing nothing for me.  Is there another way to get compiz to load at startup?  My file now reads:

     Client0_Command=compiz

---

