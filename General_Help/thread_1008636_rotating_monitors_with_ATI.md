---
title: "rotating monitors with ATI"
date: 2008-12-11
forum: General Help
---

### Post by DouglasAWh on 2008-12-11
I found this thread, [http://ubuntuforums.org/showthread.php?t=514155](http://ubuntuforums.org/showthread.php?t=514155), but no answers.  I have a different ATI card a 2400 XT.  At the moment, I have the Catalyst Control Center installed, but that can be uninstalled if need be.  Dual monitors also doesn't work correctly, but I've gotten that fixed before, so I think I can do that again.  I had a different 2400 XT at my last job that there are thread about here.  Those from before today are not this computer.  This is a fresh install from wubi of 8.10.

Thanks!

---

### Post by nzadLithium on 2008-12-11
what do you mean rotating monitors? Do you mean you want desktop effects? And to be able to rotate a desktop cube?

Cause to rotate the monitor you don't need any software, you just grab it and turn it round. XD

If you are looking for desktop effects:

```
sudo apt-get install compiz compizconfig-backend-gconf compizconfig-settings-manager compiz-core compiz-fusion-plugins-extra compiz-fustion-plugins-main compiz-gnome compiz-plugins compiz-wrapper
```

Thats all the relevant packages I have installed on my system, and its working. Also you may want to: 
```
sudo apt-get install fusion-icon
```
That will install an icon on your top panel, that you can use to setup compiz fusion easily.

---

### Post by linux_tech on 2008-12-11
Did you try
```
xrandr -o left
```

---

### Post by nzadLithium on 2008-12-11
ah you think he's tryin to spin the desktop sideways? :)

---

### Post by linux_tech on 2008-12-11
thats my impression

---

### Post by DouglasAWh on 2008-12-11
Here's a screenshot of where I'm at now: [http://www.flickr.com/photos/dawhitfield/3100880009/sizes/l/](http://www.flickr.com/photos/dawhitfield/3100880009/sizes/l/)

The screens are dual monitor, though I'm getting some funny residue.  Yes, I want the 24 inch monitor (right) to be vertical rather than horizontal.

---

### Post by DouglasAWh on 2008-12-11
> **linux_tech said:**
> Did you try
```
xrandr -o left
```

```

dwhitfie@ubuntu:~$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  160 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

---

### Post by nzadLithium on 2008-12-11
ah, I see what your getting at, thats probably going to require editing in your xorg.conf I'll take a look and see what I can find :D

---

### Post by nzadLithium on 2008-12-11
I have no idea how to only rotate one :S I can't find much anywhere. I would suggest looking for an ati configuration tool.

---

### Post by nzadLithium on 2008-12-11
the ati configuration tool is called aticonfig :D see what u can do from the options it gives u :D (You'll probably need to feed it --help).

---

