---
title: "Change default runlevel"
date: 2008-05-11
forum: Desktop Environments
---

### Post by dallascisco on 2008-05-11
I just installed Ubuntu 8.0.4 and I'd like to change the runlevel to 3. I can't find the inittab file under etc.

---

### Post by p_quarles on 2008-05-11
Umm, why? I have to say that this is unnecessary except for very specialist usages. 

In any case, you would change the GRUB menu to alter the default runlevel. Add something like "init=3", I believe. inittab has been replaced in Ubuntu by various other configuration files.

---

### Post by dallascisco on 2008-05-11
Why? Because this machine is going to run stanford folding at home and i want to keep thew running processes to a minimum. Folding doesn't require X to function.

Does anyone know the file I need to edit?


> **p_quarles said:**
> Umm, why? I have to say that this is unnecessary except for very specialist usages. 

In any case, you would change the GRUB menu to alter the default runlevel. Add something like "init=3", I believe. inittab has been replaced in Ubuntu by various other configuration files.

---

### Post by p_quarles on 2008-05-11
> **dallascisco said:**
> Why? Because this machine is going to run stanford folding at home and i want to keep thew running processes to a minimum. Folding doesn't require X to function.

Does anyone know the file I need to edit?
Then it would be easier to just stop X from running in runlevel 2, rather than altering the runlevel itself. For a standard Ubuntu installation, this would consist of running:
```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/D30gdm
```
Do that, and you will get an old-fashioned console login rather than the heavier graphical login. 

If you should ever require an X session afterward:
```
sudo /etc/init.d/gdm start
```

---

### Post by marmux on 2008-05-14
Hi,

my problem is the opposite. I want to recover the standard hardy configuration of the various /etc/rc?.d/ links.
When I upgraded from gutsy, the process froze and I had to force a reboot. After that, I managed to get it working with a 'sudo dpkg-reconfigure -a' and other things.
but most of the time (not always though) i still got a hal initialization failure after logging in. Every time I had to logout and relogin, and it worked.
I solved this problem by renaming /etc/rc2.d/S13gdm to /etc/rc2.d/S30gdm, so that it is loaded after /etc/rc2.d/S24hal.
With this the issue with hal is gone, but the boot process now hangs when loading sendmail (which I have as /etc/rc2.d/S21sendmail). It eventually moves on, but it takes a while.
Is there some configuration tool to automatically configure the right sequence for all the links without being temptative?

Thanks

---

### Post by worksofcraft on 2008-08-16
I too need to change default run level, but only temporarily and later restore it.
Why?
Well I need to install new graphics driver from NVIDIA and apparently I can't do that while X is running... (or so their help page says). They too suggest editing /etc/inittab, but Ubuntu hasn't got one :confused:

so the question is... how do I make Ubuntu boot into a root command line prompt without X for the time being and then later restore it like wot :it is now?

ty in advance  :lolflag:


oh btw I tried that /etc/rc2.d/S30gdm rename and sure enuf it boots to command prompt. The Nvidia installation runs for a bit but eventually fails. It sez "No precompiled kernel interface found...." to compile one I suppose I better do "sudo apt-get install build-essential"
to get libc header files and whatever
...to be continued...

---

### Post by worksofcraft on 2008-08-16
Just incase anyone else doing this... that was easy: after installing the build-essential libc header files Nvidia driver installation automatically compiled whatever it needed and then I just renamed that S30gdm back again and... well Runescape works in high detail mode :)

---

### Post by gsmbk on 2008-12-21
> I just installed Ubuntu 8.0.4 and I'd like to change the runlevel to 3In Ubuntu, or Debian in general, runlevel 2-3-4-5 are the same.
So there is no point to change it from 2 to 3 !!

Thought, what you want, to start with a shell, no GUI, here is what you have to to..
$sudo vi /etc/inittab
- add the following line```
: id:1:initdefault:
```, the number represents the chosen runlevel
- After re-booting, you'll have a list, choose "Drop a shell session", you are done! :)

If you ever want to go back to the GUI login, change the line to ```
: id:2:initdefault:
```Hope that get you what you want :)

---

### Post by hictio on 2008-12-21
> **worksofcraft said:**
> I too need to change default run level, but only temporarily and later restore it.
Why?
Well I need to install new graphics driver from NVIDIA and apparently I can't do that while X is running... (or so their help page says). They too suggest editing /etc/inittab, but Ubuntu hasn't got one :confused:


To do that, logout of Gnome, or what ever Desktop Environment you are using, type Ctrl + Alt + F1 or F2 or F3, login as your user, and type:

```

sudo /etc/init.d/gdm stop (ENTER)

```

It'll ask your password. When you are done, to start it, type:
```

sudo /etc/init.d/gdm start (ENTER)

```

---

### Post by gsmbk on 2008-12-21
> **hictio said:**
> To do that, logout of Gnome, or what ever Desktop Environment you are using, type Ctrl + Alt + F1 or F2 or F3, login as your user, and type:

```

sudo /etc/init.d/gdm stop (ENTER)

```It'll ask your password. When you are done, to start it, type:
```

sudo /etc/init.d/gdm start (ENTER)

```

This exactly the easiest way to do the driver update.

You can always do that, Ctrl + Alt + F1 or F2, having a shel session, by doing that. Not necessary for installing the driver, but just for the sake of having a shell session :P

If you want to get back to your GUI Ctrl + Alt + F7, assuming that you already logged in INIT 2.

---

### Post by gsmbk on 2008-12-21
Again, another thought....

Just turn into runlevel 1 and do the update...

$ sudo init 1

that will do so as well.

---

