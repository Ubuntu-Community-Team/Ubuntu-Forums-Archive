---
title: "Problems with COmpiz water effect on Jaunty"
date: 2009-04-22
forum: General Help
---

### Post by JECHO on 2009-04-22
The water effect works when i turn it on with the Shift + f9 keybindings but when i try to draw the water (like i used to be able to do on Ibex) it doesnt work. Nothing happens no matter what i set the keybindings to...

Anyone know why? Jaunty bug? compiz bug?

---

### Post by AlexW573 on 2009-04-24
I'm having the same problem, fresh install (I'm using various other effects, including the Fire effect and all of them are running just fine).

HP Pavilion dv7-1020us

Graphics card:
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)

---

### Post by morfeasrev on 2009-04-24
I can confirm this as well.
:(
A bug ticket has also opened on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/348550]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/348550")

---

### Post by themusicalduck on 2009-04-25
I'm having this problem too, but I seem to have lost the close window fire effect as well.

In the animations window the close animation tab now shows as N/A, and the burn effect isn't listed. Is it just me with this problem or are others having it too?

EDIT: also just noticed there is no 'animation addons' plugin anymore, which probably has something to do with it.

---

### Post by jeremz on 2009-05-07
This is interesting. I am having a different problem. Fresh Jaunty install, water effect will not enable. I click on the check box, and it checks, then does that thing compiz does where it restarts and takes a few seconds. Then water unchecks itself. Oddly enough, any firefox browsers I had open at the time, will now be frozen and must be restarted.

---

### Post by Zoowey on 2009-05-08
> **themusicalduck said:**
> I'm having this problem too, but I seem to have lost the close window fire effect as well.

In the animations window the close animation tab now shows as N/A, and the burn effect isn't listed. Is it just me with this problem or are others having it too?

EDIT: also just noticed there is no 'animation addons' plugin anymore, which probably has something to do with it.

I think you may have a problem that I have posted a fix for in another forum, this will get your "Animations Add-ons" back with fire and all that but still won't get water to work unfortunately.

> **Zoowey said:**
> Ok guys, I think I've figured out the problem. I have been using the 3rd party Compiz repository, when I upgraded to Jaunty there was an update to a compiz package which then made the "Animations Add-on" tab disappear. 

So what I did is disable the 3rd party compiz repository, reloaded my sources, went into synaptic and searched for "compiz-fusion" I then marked both "compiz-fusion-plugins-main and "-extra" for "complete removal" then logged out and logged back in and then installed those 2 again and it worked. So basicly disable the 3rd party compiz repository, uninstall those 2 packages and reinstall them making sure the 3rd party repository is disabled.

I hope this helps you guys.

---

