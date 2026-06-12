---
title: "Splashy problems+Beryl issues."
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by 2pacalypse on 2007-10-17
I have two issues that are driving me crazy here...

First problem Splashy just wont work, I've installed it 4 days ago and have been struggling to get it up ever since. I did as all the guides said but the default ubuntu splash (using usplash) keeps going up instead of my splashy one.

Heres the things i've done step by step:

```

apt-get install splashy

```

```

sudo gedit /boot/grub/menu.lst

```
changed the orig:
```

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1a1a7ea7-3f9d-4b1b-aae6-c1c949be61d9 ro quiet splash

```

to:

```

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1a1a7ea7-3f9d-4b1b-aae6-c1c949be61d9 ro quiet splash **vga=791**

```

```

splashy_config -i ~/Desktop/fingerprint-1.0-theme.tar.gz
splashy_config -s fingerprint
grub-update
iupdate-initramfs -u -t -k `uname -r`

```

but nothing happened, still the default ubuntu splashy :/.

now my guess is that the reason is here:
> 
Customizing Splashy

In order to install Splashy in your own custom distribution or variant of UNIX system, you would need to:

   1.
      tell the system to start ”/sbin/splashy boot” as early as possible
   2.
      some “glue” to calculate the progressbar and update it using: splashy_update “progress NN”
   3.
      you will need to exit Splashy at some point with: splashy_update exit



I dont know how to do the first part... how to make it boot up in the very beginning, and usplash probably boots up before him, hence the default usplash ubuntu theme.

Second Problem is that my Beryl stopped working from some reason yesterday... I see the Beryl icon in the gnome toolbar, but not its effect.... everything is as the human gnome theme... this isnt the first time it happened but all the other times I could simply restart X to fix it but now even a whole restart wont fix it. the only thing I've done between the last time I saw Beryl work and now is the splashy reinstallation and general internet browsing, nothing I havent done before with Beryl working... I tried to restart Beryl but it doesnt work.... I dunno what to do.

So if anyone knows what to do with either problem, please help

---

### Post by 2pacalypse on 2007-10-19
Can anyone please assist me with these issues? its been 2 days and no reply

---

### Post by 2pacalypse on 2007-10-22
Anyone? Please help me out....

---

