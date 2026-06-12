---
title: "Need instructions/guide to booting to run level 3 without X for NVIDIA driver install"
date: 2010-12-30
forum: Desktop Environments
---

### Post by lyk13 on 2010-12-30
Hi all,

thanks for the help in advance. I've scoured the forum but have a mixture of doubts or uncertainties regarding how to properly go about doing it.

What I need is to install the latest nvidia drivers for my graphics card, but it requires the use of X not running and thus initial requirements were to boot to runlevel 3.

But from what I have read, upstart which has since replaced how init levels are ran(may be wrong) denotes that runlevels 2 to 5 are almost similar?

I'm also confused as to how exactly do I modify certain files to disallow the start of X and boot to runlevel 3. I do know of the rcX.d folders but...that's about it.

Please advise in detail thanks!!! Greatly appreciated!

Edit: Initially I tried "init 3" and it brought me to a blank screen with a prompt blinking, wasn't able to do anything from there. Subsequently, "sudo init 3" does nothing, but my "runlevel" returned N 2 and then 2 3.

Edit2: Forgot to state that I am using Ubuntu 10.10

---

### Post by lyk13 on 2011-01-02
Bumpz, appreciated!

---

### Post by hhh on 2011-01-03
You shouldn't need to exit to init 3 in Ubuntu for Nvidia. Just go to System>Hardware Drivers and choose the recommended driver.

---

### Post by lyk13 on 2011-01-03
> **hhh said:**
> You shouldn't need to exit to init 3 in Ubuntu for Nvidia. Just go to System>Hardware Drivers and choose the recommended driver.
There's no Hardware Drivers under System, the closest one is to add proprietary drivers...

I'm trying to install Nvidia's latest drivers for linux which is of the extension .run

And all the instructions mentioned has to shut down X before I can install it, but I have trouble getting out of X.

Do advise thanks!

---

### Post by hhh on 2011-01-03
Proprietary drivers, there should be an option for 2 or three Nvidia drivers, use the recommended one.

---

### Post by Krytarik on 2011-01-03
Though I also recommend using the proprietary drivers offered via "Additional Drivers" (in 10.10) -- because if you compile the kernel module on your own, you have to repeat it each time the kernel is updated -- if you really want to do it this way:

Press Alt+Ctrl+F1 (e.g.) to get one console and enter:
```
sudo /etc/init.d/gdm stop
```

After you are done use the "start" option instead.

Greetings

---

### Post by lyk13 on 2011-01-03
> **hhh said:**
> Proprietary drivers, there should be an option for 2 or three Nvidia drivers, use the recommended one.
There's only 1 and I've installed that.

> **Krytarik said:**
> Though I also recommend using the proprietary drivers offered via "Additional Drivers" (in 10.10) -- because if you compile the kernel module on your own, you have to repeat it each time the kernel is updated -- if you really want to do it this way:

Press Alt+Ctrl+F1 (e.g.) to get one console and enter:
```
sudo /etc/init.d/gdm stop
```After you are done use the "start" option instead.

Greetings
Thanks for the enlightenment. I guess if the newest drivers do not provide extensive benefits as compared to what is available, one wouldn't usually update as such am I correct?

I will act according to circumstances, but am glad to at least know how to get to the booting command.

Thanks!

---

### Post by Krytarik on 2011-01-03
To clarify: The proprietary drivers are compiled against the running kernel. If the kernel packages are upgraded, and you are using the driver downloaded directly from the Nvidia-website, upon the next boot you land at the console login and you have to manually compile the driver against the new kernel, via executing the *.run-installer.

---

### Post by lyk13 on 2011-01-03
So basically installing new drivers basically have to compile with our existing kernel before it is installed?

BTW, does anyone know why I get a blank screen with a prompt when I attempt to init 3 in my first attempt(not recently)?

---

### Post by Krytarik on 2011-01-03
When you install the Nvidia drivers through the *.run-process, the kernel module gets compiled against the running kernel.

When the kernel gets upgraded, you have to run this process again, even if you don't want to upgrade the Nvidia driver at the same time, executing the exactly same *.run-file.

As for the runlevel 3 thing: I've come over this a few years ago, Ubuntu doesn't support booting into a lower runlevel.

---

### Post by lyk13 on 2011-01-04
Oh so in short, Ubuntu may be trying to get us to just use what they provide as it has been test and tried, as opposed to the 'raw' ones out there eh?

---

### Post by Krytarik on 2011-01-04
> **lyk13 said:**
> Oh so in short, Ubuntu may be trying to get us to just use what they provide as it has been test and tried, as opposed to the 'raw' ones out there eh?
I guess they have "optimized" the boot-up process some way, which as a side doesn't allow specifying a runlevel.

---

### Post by lyk13 on 2011-01-04
/nod Thanks!

---

### Post by nerdy_kid on 2011-01-04
you can use the latest nvidia drivers from the xswat ppa, that way you get the best of both worlds -- up to date drivers and auto installs when the kernel upgrades.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by lyk13 on 2011-01-05
> **nerdy_kid said:**
> you can use the latest nvidia drivers from the xswat ppa, that way you get the best of both worlds -- up to date drivers and auto installs when the kernel upgrades.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
Thanks! Will look into it and feedback if necessary. :D

---

### Post by Krytarik on 2011-01-06
This one seems to can do it:
[http://ubuntuforums.org/showthread.php?p=10323038#post10323038](http://ubuntuforums.org/showthread.php?p=10323038#post10323038)

---

### Post by lyk13 on 2011-01-06
> **Krytarik said:**
> This one seems to can do it:
[http://ubuntuforums.org/showthread.php?p=10323038#post10323038](http://ubuntuforums.org/showthread.php?p=10323038#post10323038)
Will try it thanks!

---

