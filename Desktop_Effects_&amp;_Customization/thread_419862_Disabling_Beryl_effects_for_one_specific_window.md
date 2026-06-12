---
title: "Disabling Beryl effects for one specific window"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by almightybunghole on 2007-04-23
Hi all,

Well I'm an Ubuntu newbie and very much enjoying working in a non-Windows environment. I do however still need to access Windows servers so am using rdesktop ([http://ubuntuforums.org/showthread.php?t=224212](http://ubuntuforums.org/showthread.php?t=224212)) to do so seamlessly - which works very well I might add! I am also using Beryl for funky window effects, unfortunately though the combination of seamless rdesktop and Beryl is not a good one. 

What I would therefore like to do, if possible, is to disable Beryl effects for the rdesktop session. Is this possible? I am guessing that modifying some Beryl-related script might achieve this?

All comments appreciated! :) 
Cheers.
George

P.S. Guess I should mention that I'm using the Feisty beta...

---

### Post by kwaanens on 2007-04-23
> **almightybunghole said:**
> P.S. Guess I should mention that I'm using the Feisty beta...

Sorry, I can't help your situation, but unless you refuse to install updates via apt/synaptic/adept or whatever, you're not using Feisty beta. With all updates, it is now final.

- Ketil

---

### Post by almightybunghole on 2007-04-23
Fair enough! I am not sure whether Synaptic has updated me yet or not. I'm going to do a fresh install of Feisty final on a new HDD but at the moment I'm not quite ready for that.

---

### Post by madcow72 on 2007-04-23
Very simple to disable beryl whenever you want to.  Just click the red jewel beryl icon, go down to "Select Window Manager", and choose "Metacity"  (or Nautilus if you're on KDE.)  That will stop beryl and resume your default windows manager so that you can work with remote desktops.

---

### Post by almightybunghole on 2007-04-23
> **madcow72 said:**
> Very simple to disable beryl whenever you want to.  Just click the red jewel beryl icon, go down to "Select Window Manager", and choose "Metacity"  (or Nautilus if you're on KDE.)  That will stop beryl and resume your default windows manager so that you can work with remote desktops.
Hi madcow, yeah that's what I'm doing at the moment although I was hoping that maybe there was a way of automating the process so I don't have to manually disable Beryl every time?

---

### Post by kwaanens on 2007-04-23
It's possible that you can set something in beryl-settings-manager. I have the Norwegian translation, but it's the one with a + in a window, in Window Management
There is some criteria you can set there, but I don't know how it works.

- Ketil

---

### Post by revertex on 2007-05-02
this question was already answered here several times

[http://ubuntuforums.org/showthread.php?t=142160](http://ubuntuforums.org/showthread.php?t=142160)
[http://ubuntuforums.org/showthread.php?t=298971](http://ubuntuforums.org/showthread.php?t=298971)
you may also try this 
[http://ubuntuforums.org/showthread.php?t=363529](http://ubuntuforums.org/showthread.php?t=363529)
[http://ubuntuforums.org/showthread.php?t=427553](http://ubuntuforums.org/showthread.php?t=427553)

---

### Post by DarkN00b on 2007-05-02
This might work for you. First, make sure your rdesktop window is open. Open the Beryl Settings Manager and go to Window Management -> Window Specific Settings. On the right side, expand Disable ARGB Visual. Click the [+] button on the right and a dialog will pop up. In the dialog box, choose Window Class (above the Disable ARGB Visual checkbox) then click the [Grab] button. Now click your rdesktop window. Click the [OK] button to close the dialog.

Now you should see something like ```
c:rdesktop:1
``` under Disable ARGB Visual. That should disable most all effects for that window. If you have any questions, just post 'em here.

---

