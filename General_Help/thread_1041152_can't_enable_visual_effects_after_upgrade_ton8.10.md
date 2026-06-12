---
title: "can't enable visual effects after upgrade ton8.10"
date: 2009-01-16
forum: General Help
---

### Post by luke0927 on 2009-01-16
I posted this in the multimedia/video but that must not be the best place can anyone give me any ideas...it was working fine in 8.04 i never install a driver or anything but now my visual effects is set to none and it will not let me enable it...it also does not pop up to select a driver here is some info....

Well i don't have a big graphics card just the intel built in video card and just had a basic cube in 8.04...all other video looks fine is this a driver problem or did a certain program get removed during the upgrade?

> luke@luke-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

> luke@luke-desktop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity

here is some info can anyone tell whats wrong?

thanks for the help

---

### Post by redilyn on 2009-01-16
Your card has been blacklisted as buggy in intrepid when using compiz.

You can bypass the blacklist and force the load of compiz by doing the following

```

sudo gedit ~/.config/compiz/compiz-manager

```

This will open a blank file. Add the following line and then save the file

```

SKIP_CHECKS=yes

```

Then try to enable your visual effects.

If you do this please do not post about any issues you have with stability or video playback problems, that's why your card was blacklisted in the first place.

---

### Post by luke0927 on 2009-01-16
Thanks!! i will try this...if i have problems i guess i should just get a basic nvidia card right?  I don't do any thing with grapichs or play games thats why i just have an integrated card....the problems would only show up in compiz right?

I'll update how it goes.

---

### Post by redilyn on 2009-01-16
Ya, if you really must have compiz you could just get a cheap nvidia card so you can run it.

---

### Post by luke0927 on 2009-01-16
Nope it really doesn't like changing it...so strange that it worked find with the older version of ubuntu but not the new...

thanks for the help though!

---

### Post by redilyn on 2009-01-16
You also try this from the command line and see what error you get

```

SKIP_CHECKS=yes compiz

```

---

