---
title: "Always On"
date: 2007-06-19
forum: Desktop Environments
---

### Post by kfarrell on 2007-06-19
Hello,

How can I make Ubuntu 7.04 always stay on. It's set up as a display machine, cycling through photos. I have no keyboard or mouse attached, I just VNC in. 

Despite me turning power managment to never turn anything off, it still turns off the monitor after a while. :(

---

### Post by dreadlord_chris on 2007-06-19
> **kfarrell said:**
> Hello,

How can I make Ubuntu 7.04 always stay on. It's set up as a display machine, cycling through photos. I have no keyboard or mouse attached, I just VNC in. 

Despite me turning power managment to never turn anything off, it still turns off the monitor after a while. :(

There are a few changes that you'll have to make to **xorg.conf**
first bring up the Run dialog - Alt-F2 - cut/paste:
```

gksudo gedit /etc/X11/xorg.conf

```

First, in Section **ServerLayout** add the following options:
```

    Option 	   "BlankTime" "0"
    Option	   "StandbyTime" "0"
    Option 	   "SuspendTime" "0"
    Option	   "OffTime" "0"
    Option 	   "NoPM" "true"

```

Next scroll down to Section **Module** and look for the line:
```

    Load     "extmod"

```
change it to this:
```

    SubSection     "extmod"
	Option	   "omit DPMS"
    EndSubSection

```

Save & reload X - your monitor should now stay on until you actually turn it off.

---

### Post by revelation.now on 2007-06-19
Two guesses. One, is the screen saver configured? I think the default is to blank the screen.

Secondly, and probably less likely, is there power management set for the screen in the bios?

---

### Post by kfarrell on 2007-06-19
Awesome reply, thankyou.

---

### Post by dreadlord_chris on 2007-06-19
> **kfarrell said:**
> Awesome reply, thankyou.

No problem - it actually took weeks of digging before I came up with those settings.... glad to pass them along...

---

