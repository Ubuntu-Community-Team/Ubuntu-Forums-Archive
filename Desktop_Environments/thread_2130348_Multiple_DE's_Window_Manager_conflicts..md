---
title: "Multiple DE's Window Manager conflicts."
date: 2013-03-29
forum: Desktop Environments
---

### Post by vynonline on 2013-03-29
I have installed Ubuntu 12.04 and later installed cinnamon.

```
[INDENT]sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
[/INDENT]

```

I hade conflicts with nautilus being loaded for desktop instead of nemo and therefore not displaying my desktop icons. Therefore i uninstalled Unity and Nautilus.
Then nemo was used as window manager for desktop.

I later installed ubuntu-desktop to get unity back and also nautilus.
Now in unity, nemo is being loaded as desktop window manager displaying icons. There is no issue with that expect i dont get the menu bar sort of options situated in the top panel for desktop in ubuntu. Other applications works fine with their options in the top bar.

I edited **/usr/share/gnome-session/sessions/ubuntu.session** as 

```

[GNOME Session]
Name=Ubuntu
RequiredComponents=gnome-settings-daemon;
RequiredProviders=windowmanager;panel;filemanager;
DefaultProvider-windowmanager=compiz
DefaultProvider-panel=compiz
DefaultProvider-filemanager=nautilus
IsRunnableHelper=/usr/lib/nux/unity_support_test
FallbackSession=ubuntu-2d
DesktopName=Unity

```

which still uses nemo for desktop and opens nautilus filemanager as an window during login.

I also edited **/usr/share/gnome-session/sessions/cinnamon.session** as

```

[GNOME Session]
Name=Cinnamon
RequiredComponents=cinnamon;gnome-settings-daemon;
RequiredProviders=windowmanager;
DefaultProvider-windowmanager=nemo
IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated
FallbackSession=gnome-fallback
DesktopName=GNOME

```
which works alright using nemo for desktop.

I would like to try out other DE's like MATE,LXDE,XFCE etc..but each has different window managers and i would like to use each with their own window manager for desktop and also have all of them in my PC

---

### Post by sudodus on 2013-03-29
> **vynonline said:**
> ...

I would like to try out other DE's like MATE,LXDE,XFCE etc..but each has different window managers and i would like to use each with their own window manager for desktop and also have all of them in my PC

I have an Ubuntu system with unity + lxde + kde and a Lubuntu system with lxde + xfce. I have used

```
sudo apt-get install kubuntu-desktop
```
```
sudo apt-get install lubuntu-desktop
```
```
sudo apt-get install xubuntu-desktop
```

to get these systems, and the desktops work properly. The only problem is that the menus have some doublets for application programs.
--
Maybe your installation of cinnamon via the ppa is not quite compatible with the Ubuntu desktop system.

---

### Post by vynonline on 2013-03-29
I mean about the file managers interacting between both environments desktops. Desktop is maintained by a file manger right? cinnamon has nemo and unity uses nautilus. When i installed cinnamon. nautilus is the default for desktop unless i logout select cinnamon in login. if i reboot again in cinnamon nautilus is used as file manager for desktop.

So  I removed nautilus and unity . Then when later on i installed ubuntu-desktop nemo is used as file manager in unity .

I would like to know how to set-up seperate File managers and Window managers for seperate Desktop environments.

---

### Post by sudodus on 2013-03-29
I see your problem, but I'm saying this kind of problem is not big (maybe none at all) if you use the command lines in my previous post. But when you run Nautilus in the other desktop environments, you can use this alias to stop it grabbing control of the desktop

```
 alias nautilus='nautilus --no-desktop'
```

I don't know enough about the cinnamon ppa to help you with the interference with nemo.

---

### Post by vynonline on 2013-03-30
Running that in the terminal helps?

---

### Post by sudodus on 2013-03-30
```
nautilus --no-desktop
```
will not grab the desktop. This can be run from a terminal window (via an alias as I suggested) or from a menu entry or from a desktop starter file (something.desktop).

But I can't help you with the problem that might depend on the cinnamon installation via that ppa. However, I'm sure it is easy to solve for someone with experience of cinnamon installations in Ubuntu. Let us hope some of these guys will see this thread and help you.

---

### Post by vynonline on 2013-03-30
Thank you for your assistance.
I have removed unity , but i have kept nautilus since i read that removing nautilus may affect applications such as Brasero disc burner . If nemo is a fork of nautilus , I assume it shouldn't cause much trouble.

---

