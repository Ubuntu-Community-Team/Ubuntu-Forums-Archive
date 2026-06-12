---
title: "Compiz trouble. Default icons, no effects."
date: 2011-03-12
forum: Desktop Environments
---

### Post by TheHL2Guy on 2011-03-12
Hi!

I have installed the newest Ubuntu (10.10?) on my laptop.

It's the desktop version, and I've installed Compiz Fusion to get the 3D cube effect.

I installed it, and it went fine. I got the cube working, and I had also wobbly windows (a cool effect) and such.

I had also the default 10.10 theme (ambiance theme)

So.. When I restarted my PC just to see if everything worked, I saw that the theme were the old gray "gnome" theme I think.. Well I don't want that!

So I opened theme manager and chose the ambiance theme.

The window borders and the top and bottom toolbar went into the ambiance theme, but the right click menu, explorer buttons, icons and such were not changed.

So I thought if I uninstalled Compiz Fusion it should be normal..

I restarted the PC and then icons were normal, so I went to theme manager to check if everything were right. It was, but the effects.. I couldn't change it, it were just gray.

Also the window borders are now gone..

and I can't have more desktops anymore.

I don't have any Graphics card driver, only the one that ubuntu had, and it works fine (atleast before)

Does anyone know how to get the effects back, and the window borders? :D

I kinda need Ubuntu working (with effects, because they improve my worktime) before monday because Ubuntu is the only OS that can get into our school network (it uses username and password and certificate that Ubuntu has), and I'm working on a newspaper that I need internet for.

Thanks!

---

### Post by Krytarik on 2011-03-12
First, you have to decide:
- If you want desktop effects, you have to re-install Compiz.
- If not, choose "None" in "System -> Preferences -> Appearance -> Visual Effects"

Then see this thread about the issues you experienced, start at the end:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

And to probably improve your video performance by choosing a better driver please tell me what video card/chip you have.

---

### Post by TheHL2Guy on 2011-03-12
> **Krytarik said:**
> First, you have to decide:
- If you want desktop effects, you have to re-install Compiz.
- If not, choose "None" in "System -> Preferences -> Appearance -> Visual Effects"

Then see this thread about the issues you experienced, start at the end:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

And to probably improve your video performance by choosing a better driver please tell me what video card/chip you have.

Yeah, ok. The video card I have is a Intel GMA 3150. I'll check the link thanks :)

I have tried to reinstall compiz several times, but then the icons goes back to default gnome

---

### Post by Krytarik on 2011-03-12
You may try the PPA of Ubuntu-X-Swat, they offer more recent drivers than the official repo:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Krytarik on 2011-03-12
To shorten your read time, see this post ;-):
[http://ubuntuforums.org/showthread.php?p=10541711](http://ubuntuforums.org/showthread.php?p=10541711)

---

### Post by TheHL2Guy on 2011-03-12
I've reinstalled only the compiz pack and not the advanced control panel as I had before, and now the window borders, icons and such is back, but when I try to change to extra effects the window borders disappear.. If i log off and on again the window borders are back.

So the problem now is the effects..

So I tried the command in the last link you gave:

sleep 10 && gnome-settings-daemon && killall nautilus
this is what I got:
```

lars@ubuntu:~$ sleep 10 && gnome-settings-daemon && killall nautilus

** (gnome-settings-daemon:3115): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:3115): WARNING **: Could not acquire name
lars@ubuntu:~$
```

---

### Post by Krytarik on 2011-03-12
Install "CompizConfig Settings Manager", it has no effect on the issue itself.

Then, is there a difference if you choose "Normal" or "Extra" in "Appearance -> Visual Effects", regarding the issue?

---

### Post by TheHL2Guy on 2011-03-12
> **Krytarik said:**
> Install "CompizConfig Settings Manager", it has no effect on the issue itself.

Then, is there a difference if you choose "Normal" or "Extra" in "Appearance -> Visual Effects", regarding the issue?

Nope, it just reverts back to "none"..

I installed the driver that you listed in the code, and restarted.. No difference..

---

### Post by TheHL2Guy on 2011-03-12
Got it working! :D

I just went to synaptic program thingy and searched for "compiz" and it were one uninstalled compiz pack that were missing. So after installing that, restarted PC, effects work!

The cube effect does work now, thanks for the help!

And it seems that the drivers made the cube even smoother! :D

---

### Post by Krytarik on 2011-03-12
Cool! Which package was missing then?

---

### Post by TheHL2Guy on 2011-03-12
> **Krytarik said:**
> Cool! Which package was missing then?

In the description it says:

```
This metapackage provides the components necessary for running compiz. It
provides the compiz core, a set of standard plugins, a window decorator using
the Gtk toolkit and the files necessary to integrate compiz with the GNOME
desktop environment.
```The package were called only compiz :D

I installed (and uninstalled) compiz from Ubuntu Software Center or something..

---

