---
title: "how do i reactivate"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by darksora145 on 2007-11-17
how do i reactivate the desktop effects without lagging? and what are the keys for the desktop cube?

---

### Post by smartboyathome on 2007-11-18
1) What do you mean by "lagging"? Do you mean without making the system slow, without such a slow startup, or something else?

2) You need to install CompizConfig Settings Manager to activate the cube. Use synaptic to locate compizconfig-settings-manager and install it, and then go to system > preferences > Advanced Desktop Effects and put a check mark next to the Desktop Cube.

---

### Post by darksora145 on 2007-11-18
well yeah  without like making everyything all slow. Uhhh someone told me to do meta something --replace and it went all back to normal so. but i want to use the effects again

---

### Post by darksora145 on 2007-11-18
hello?

---

### Post by smartboyathome on 2007-11-18
There is no way to make it faster, as far as I know. Also, using emerald --replace should replace your decorator. Try it.

---

### Post by Forlong on 2007-11-18
> **darksora145 said:**
> hello?
Hi :)

How 'bout telling us about your system?
What version of Ubuntu are you using and particularly what graphics card + driver?

---

### Post by darksora145 on 2007-11-18
im using the ubuntu gutsby gibbon newest one and i have a integrated graphics card from mac

---

### Post by Forlong on 2007-11-18
Like smartboyathome said, there's not much you can do about the slowness. I guess your graphics chip is just not good enough.

As for enabling the effects again, go to *System &#8594; Preferences &#8594; Appearances &#8594; Visual Effects*

And about the cube, see [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) under "Getting the cube".

---

### Post by xAEE on 2007-11-18
I would uninstall Compiz using the Synaptic Package Manager and then reinstall it using the following command.

```
sudo aptitude install compizconfig-settings-manager
```

Then, go back into Synaptic to make sure all the packages are installed. Search "desktop effects".

---

