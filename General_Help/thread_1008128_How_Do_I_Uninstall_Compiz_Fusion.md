---
title: "How Do I Uninstall Compiz Fusion"
date: 2008-12-11
forum: General Help
---

### Post by satans aunt on 2008-12-11
So,

I'm very new to this whole Ubuntu experience and as such I managed to ruin what was essentially a perfect desktop environment by installing and enabling too many compiz fusion options. 

It would appear that there was a conflict between at least two of the options I selected, I now have the joy of looking at a black screen when the cursor hovers over a column or the panel.

I've looked online but there isn't much (any) help that I found.

Essentially, I need to find a way to uninstall compiz fusion pre-boot. 

Is that possible? If so how?


Thanks for your time/help. I await your suggestions.

---

### Post by eternalnewbee on 2008-12-11
Go to: **Main Menu > System > Administration > Synaptic Package Manager**, and in the **searchbar** enter **compiz** and uninstall related packages.

---

### Post by damis648 on 2008-12-11
Better yet, press Alt+F2 and type in
```
metacity --replace
```
To replace compiz with metacity. You can now enter compizconfig and disable the plugins.

---

### Post by satans aunt on 2008-12-11
Thanks guys.

Much appreciated.

Currently posting in Ubuntu. As nature intended.

ALt+f2 worked a charm, even though I was doing it blind.

---

### Post by eternalnewbee on 2008-12-11
Good one Damis648.
I was thinking she only wanted to uninstall.

---

### Post by satans aunt on 2008-12-11
Wow,

So now I have a new, more serious problem. I was carefully selecting options in Compiz fusion when all of a sudden my screen became a sequence of mutli-color lines.

I am now finding that I can't stay logged on for more than a few seconds before I am automatically logged out.

If you guys help me out here I promise to uninstall fusion and never, ever  install it again.

What a freaking nuisance this has turned out to be....

---

### Post by Diabolis on 2008-12-11
Maybe you need a different driver for you video card. In your log in window, look for a option that says **sessions** and then select **safe graphics mode**, so you can log in.

---

### Post by satans aunt on 2008-12-11
As far as I can tell I don't have the option of a 'safe graphics mode'.

I've tried all the ones available to me but the problem remains.


:(

---

### Post by eternalnewbee on 2008-12-11
> 
If you guys help me out here I promise to uninstall fusion and never, ever install it again.

What a freaking nuisance this has turned out to be....
Go to: **Main Menu > System > Administration > Synaptic Package Manager**, and in the **searchbar** enter **compiz** and uninstall related packages.

---

### Post by satans aunt on 2008-12-11
**"Go to: Main Menu > System > Administration > Synaptic Package Manager, and in the searchbar enter compiz and uninstall related packages."**

That option isn't available to me, sadly.

I wish it were that simple.

---

### Post by Diabolis on 2008-12-11
After you log in, press **<Ctlr><Alt>F1**, you'll be prompted to log in. After that, uninstall compiz:
```
sudo apt-get --purge remove compiz
```

With **<Ctlr><Alt>F7** you can go back to your graphical session.

---

### Post by satans aunt on 2008-12-11
:(

---

### Post by satans aunt on 2008-12-11
Uninstalled compiz (apparently), many thanks to Diabolis.

But the problem remains the same.

Looks like another win for Windows.

:(

---

### Post by damis648 on 2008-12-11
Sounds like a graphics driver issue, if we can manage to fix it then you can reinstall compiz. :popcorn: Enter the TTY again with Ctrl+Alt+F1 and type in
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```
and see if that works. :popcorn: If it does, enter the restricted drivers manager and see if you can re-enable the proprietary driver.

---

### Post by satans aunt on 2008-12-11
Thanks for all your input guys.

I grew impatient and rm rf(ed) the hell out of ubuntu.

Currently restoring my data (mainly settings and programs) using sbackup.

Let's see how this goes.


P.S.
Damis I've only just now seen your comment. I wish you'd have gotten here a tad earlier...

---

### Post by cael_shadowhunter on 2009-02-03
I had compiz problem where menus appeared as snow when opened, windows were also only snow. I tried:  

> **damis648 said:**
> Better yet, press Alt+F2 and type in
```
metacity --replace
```
To replace compiz with metacity. You can now enter compizconfig and disable the plugins.

reinstalled compiz 


worked a charm

---

