---
title: "Compiz Fusion on Ubuntu Gusty!"
date: 2008-01-20
forum: Desktop Effects &amp; Customization
---

### Post by lightlink7 on 2008-01-20
Hi! I recently installed Ubuntu Gusty on my laptop today and I know that Compiz Fusion is already installed on it. But when I go to system preferences there is no advanced effects. Also when I click system preferences compizconfig settings manager it does not start! I looked at my restricted drivers and I have installed nvidia acclerated drivers but compiz fusion still  does not work. I do get the expo effect when i press super and e. But nothing else works and the compiz config settings does not come on. Can someone please help!

---

### Post by Ub1476 on 2008-01-20
System>Preferences>Appearance>Visual-Effects

```
sudo apt-get install compizconfig-settings-manager

sudo apt-get install compizconfig-settings-manager --reinstall

ccsm
```

---

### Post by lightlink7 on 2008-01-20
> **Ub1476 said:**
> System>Preferences>Appearance>Visual-Effects

```
sudo apt-get install compizconfig-settings-manager

sudo apt-get install compizconfig-settings-manager --reinstall

ccsm
```

I tried that and it still does not work. There still is no advanced visual effects and i cant get to compizconfig settings manager

---

### Post by lightlink7 on 2008-01-20
Please help. I tried typing ccsm in terminal and all i got was this:
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /var/lib/python-support/python2.5/compizconfig.so: undefined symbol: ccsStringToEdges

---

### Post by rosegarden78 on 2008-01-20
Advanced 3D effects were known to crash some EE and FF systems.   I think they're ####.  I liked the speed, power and simplicity of XFCE with KDE + GNOME running Nautilus.  If you want your X Server to crash and freeze like Windows go ahead and install 3D effects.  You're not missing anything.  Trust me.

P.S. Only applies to Edgy and/or Feisty with Intel GM915 graphics cards but now it is fully functional in Gutsy.

EDIT:  I love Compiz Fusion now in Ubuntu GG with the Avant Window Manager and Xfce!

---

### Post by lightlink7 on 2008-01-20
> **rosegarden78 said:**
> Advanced 3D effects are known to cause system instability.  Plus they give me a headache.   I think they're ugly.  I like the speed, power and simplicity of XFCE with KDE + GNOME running Nautilus.  If you want your X Server to crash and freeze like Windows go ahead and install 3D effects.  You're not missing anything.  Trust me.

Wow, i googled those things you mentioned and they look quite nice. But still I just want to at least try out the effects on compiz fusion and get a mac look.

---

### Post by Ub1476 on 2008-01-20
Alright, I assume you upgraded, right? If that's right, remove the repos which you used to install compiz for Feisty (Trevinos repos maybe?), then go into Synaptic and search for compizconfig. Remove it, then install it again.

[Source]("http://ubuntuforums.org/showthread.php?t=593105")

---

### Post by Ub1476 on 2008-01-20
> **rosegarden78 said:**
> Advanced 3D effects are known to cause system instability.  Plus they give me a headache.   I think they're ugly.  I like the speed, power and simplicity of XFCE with KDE + GNOME running Nautilus.  If you want your X Server to crash and freeze like Windows go ahead and install 3D effects.  You're not missing anything.  Trust me.

That is only spam. Running Gnome, KDE and XFCE on the same system is what will break it, not running Compiz-Fusion. Lightlink is already running Gnome, and should be fine with that, Nautilus is default. Surely, desktop effects is not as fast as running none, but if you have a capable driver, a regular user wont feel much difference. It do not freeze either. The Ubuntu devs has blacklisted those drivers which do not work properly with CF already, and X wont crash without editing the xorg.conf file.

---

### Post by lightlink7 on 2008-01-20
> **Ub1476 said:**
> Alright, I assume you upgraded, right? If that's right, remove the repos which you used to install compiz for Feisty (Trevinos repos maybe?), then go into Synaptic and search for compizconfig. Remove it, then install it again.

[Source]("http://ubuntuforums.org/showthread.php?t=593105")
Actually I did not upgrade, it was just an install of ubuntu gusty on my laptop. Also now when I activate effects i cant minimize can you please help. I still cant use compiz...

---

### Post by Ub1476 on 2008-01-20
That is very strange. Like you said here:

> Also when I click system preferences compizconfig settings manager it does not start!

This was how it was in Feisty.

However, try to do this:

```
sudo apt-get autoremove

sudo apt-get install ubuntu-desktop --reinstall
```

---

### Post by rosegarden78 on 2008-01-23
I got it working it wasn't spam it did cause problem for me in Feisty that's why it wasn't included until Gutsy sorry for not clarifying.  If you really want to get a MacDock and Vista eye candy try this tutorial worked for me: Even on this old Intel GM915 graphics card.  I'm using compiz it's included in Gutsy it's awesome!  If the menu or title bars vanish on loading compiz, go into Synaptic and install the compiz-kde and compiz-gnome and any other add-ons for gnome and kde.  But you should get rid of Feisty and upgrade as soon as possible.  One more thing...you might need to run compiz by pressing Alt-F2 or make a launcher on your desktop.

[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

Now who's full of spam, huh?  :lolflag:

---

### Post by rosegarden78 on 2008-01-23
> **Ub1476 said:**
> Running Gnome, KDE and XFCE on the same system is what will break it, not running Compiz-Fusion.

Really?  I'm assuming you installed GNOME, KDE and XFCE flawlessly like myself?  I suppose having a choice of sessions at login is bad?  Unlike yourself I take the time to revisit and/or correct my posts.  May I suggest you consider yourself of spam?

P.S.  Remember to do unto others as they do unto you.  :KS

---

### Post by rmcder on 2008-01-23
> **lightlink7 said:**
> Hi! I recently installed Ubuntu Gusty on my laptop today and I know that Compiz Fusion is already installed on it. But when I go to system preferences there is no advanced effects. Also when I click system preferences compizconfig settings manager it does not start! I looked at my restricted drivers and I have installed nvidia acclerated drivers but compiz fusion still  does not work. I do get the expo effect when i press super and e. But nothing else works and the compiz config settings does not come on. Can someone please help!
Did you install XGL?  In many cases it is required to get customization to work.

---

