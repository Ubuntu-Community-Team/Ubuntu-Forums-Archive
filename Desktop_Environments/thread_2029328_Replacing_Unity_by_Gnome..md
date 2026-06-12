---
title: "Replacing Unity by Gnome."
date: 2012-07-19
forum: Desktop Environments
---

### Post by Johnread on 2012-07-19
I wish to use Gnome desktop in place of Unity. I have downloaded Gnome but need instruction in replacing Unity with Gnome.  I am running  Ubuntu 11.10. Thank you.

---

### Post by Frogs Hair on 2012-07-19
When you login select the desktop environment from the icon on the right side of the greeter box.

---

### Post by 3Miro on 2012-07-19
Unity is just a shell on top of Gnome 3, technically Unity is Gnome. If you want to use a different Gnome interface, you can install either Gnome-shell or Gnome-session-fallback that will give you either Gnome-shell or Gnome-classic interfaces.

See Frogs Hair's screenshot on how to select the interface on login.

---

### Post by kansasnoob on 2012-07-20
> **Johnread said:**
> I wish to use Gnome desktop in place of Unity. I have downloaded Gnome but need instruction in replacing Unity with Gnome.  I am running  Ubuntu 11.10. Thank you.

I made some notes about gnome classic (no effects) here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

I should perhaps note that if you installed the meta-package 'gnome' it's still gnome 3, but actually gnome 3.0 (the version currently used in Debian testing at that time) whereas the version of gnome used in Ubuntu Oneiric is gnome 3.2.

[ATTACH]221530[/ATTACH]

---

### Post by bogan on 2012-07-20
Hi!, **Kansasno**ob.

I do not know if it is significant, but in my 12.04 Classic [no effects] installation, 'gnome-shell' [installed] shows as v.3.4.1, but 'gnome' [not installed] shows as: 1.3.0+6 confirming your note in that respect.

The other gnome features show as your Synaptic Screenshot.

Chao!, **bogan.**

---

### Post by kansasnoob on 2012-07-20
> **bogan said:**
> Hi!, **Kansasno**ob.

I do not know if it is significant, but in my 12.04 Classic [no effects] installation, 'gnome-shell' [installed] shows as v.3.4.1, but 'gnome' [not installed] shows as: 1.3.0+6 confirming your note in that respect.

The other gnome features show as your Synaptic Screenshot.

Chao!, **bogan.**

To the best of my understanding the standard "gnome" packages are available because Canonical cross-develops with Debian in order that both Ubuntu and Debian benefit, and those packages are typically what's available in "Debian testing" rather than stable, unstable, or experimental. The same is true of Lubuntu vs LXDE, Xubuntu vs XFCE, etc.

So I think sometimes people think, "I want Gnome, not Unity", so they'll install the package "gnome", and they'll then just be surprised with gnome-shell, and since that version is still 3.0 they'll be very disappointed :(

---

### Post by zombifier25 on 2012-07-21
> **Farstanley said:**
> Came here for that very reason but the rant threads aren't listed under Main Support Categories, where are they ?

Most of them will end up in [Recurring DIscussions](http://ubuntuforums.org/forumdisplay.php?f=302).

---

### Post by Elfy on 2012-07-21
Trolling posts removed.

Recurring discussion is where they are - however ranting and trolling will not help you much.

---

### Post by kyphi on 2012-07-21
Whether or not you want to use Unity or Cinnamon or MATE or Gnome-shell or whatever else is entirely up to the user.  There is no need to change your operating system.

My preference is for Gnome-shell and this is how to install it:

```
sudo apt-get install gnome-shell gnome-session gnome-tweak-tool
```

then add whichever extensions you want from:

[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by Elfy on 2012-07-21
> **kyphi said:**
> Whether or not you want to use Unity or Cinnamon or MATE or Gnome-shell or whatever else is entirely up to the user.  There is no need to change your operating system.


Exactly :)

Took me 20 minutes - but I actually installed a clean xubuntu ...

Apparently though you need to 

```
sudo apt-get install troll-threads-on-forum-because-no-ones-done-that-yet gnome-shell gnome-session gnome-tweak-tool 
```

---

