---
title: "Grub2 installation how-to."
date: 2009-01-11
forum: General Help
---

### Post by Slug71 on 2009-01-11
Ok so it seems a few people have tried to install Grub2 and have run into problems after the reboot, me being one of them. Now i DONT recommend installing Grub2 as IT IS STILL IN DEVELOPMENT but if you want to give it a try then follow this simple little how-to which got me up and running with it after battling with a error after a reboot and trying to chainload into Grub2. REMEMBER TO BACK UP ALL DATA.

First install Grub2 with Synaptic.
A little box 'Configuring grub-pc' will pop up during the installation with a command line box. Mine was blank and just left it that way and clicked 'forward'. Installation will complete.

Then open Terminal and run:

```
sudo update-grub2

sudo upgrade-from-grub-legacy

sudo update-grub
```

And yes you read that right. Do the complete upgrade BEFORE rebooting thus avoiding the chainload option like other 'how-to's' say.
Unfortunately it seems the 'safe' way is the riskiest way since you have to skip the 'safe' chainload method but it seems to avoid the Error messages some people have been getting after reboot.

All that is left now is to reboot hopefully everything went ok. :)


If you are dual/multi booting with other OS's you may want to run:

```
sudo os-prober
```

to make sure it detects them and:
```

sudo update-grub
```

If os-prober is not installed then run:

```
sudo apt-get install os-prober

sudo os-prober

sudo update-grub

```

And you are done. :)

---

### Post by skotos on 2009-03-01
Thank you very much indeed, Slug71.

I went into the same troubles just a few hours ago. It's good you documented this behaviour, since it is very important for all of us, newbies and not, to know what we can expect from a package that seems so easy to run by just clicking on it in Synaptic.

I am still interested in it, but not for a production notebook. No doubt Grub is too old and Grub2 is a long awaited package, but - probably - it currently needs some more adjustments: the boot process can hurt so much!

If I had read your post before clicking, I would have saved a heartache. Eh eh eh...

---

### Post by malathion on 2009-12-05
I just got a new hard drive in the mail and after installing karmic x64 I was stuck on the blinking cursor. I ran these instructions and got this:

> ubuntu@ubuntu:/media$ sudo os-prober
/dev/sda1:Ubuntu 9.10 (9.10):Ubuntu:linux
ubuntu@ubuntu:/media$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) yes
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ubuntu@ubuntu:/media$ 
So that's promising. I'm going to reboot now and hope this works.

---

### Post by malathion on 2009-12-05
No luck. Back to the drawing board...

---

