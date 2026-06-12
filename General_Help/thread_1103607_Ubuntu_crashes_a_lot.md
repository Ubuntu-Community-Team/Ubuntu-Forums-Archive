---
title: "Ubuntu crashes a lot"
date: 2009-03-22
forum: General Help
---

### Post by Raskula on 2009-03-22
Before I thought it was the Nvidia driver that was crashing the system like 10 times a day. But then I formatted and didn't install the driver, and it still crashed.

The crash looks like a distorted multi-colored screen.

I have an emachine EL1200-o5w

AMD Athlon 2650e Processor
Nvidia GeForce 6150SE Graphics
DVD + RW Super Multi-Format Dual Layer Optical Drive
160GB Hard Drive
1 GB DDR2

This problem occurs on every single Linux Distro, and does not happen on Windows.


Does anyone know of what can be causing this? So far nobody could help me after a few months with this problem. 

Please, I really don't want to use Windows anymore as I love Linux so much.

---

### Post by linuxisevolution on 2009-03-22
> **Raskula said:**
> Before I thought it was the Nvidia driver that was crashing the system like 10 times a day. But then I formatted and didn't install the driver, and it still crashed.

The crash looks like a distorted multi-colored screen.

I have an emachine EL1200-o5w

AMD Athlon 2650e Processor
Nvidia GeForce 6150SE Graphics
DVD + RW Super Multi-Format Dual Layer Optical Drive
160GB Hard Drive
1 GB DDR2

This problem occurs on every single Linux Distro, and does not happen on Windows.


Does anyone know of what can be causing this? So far nobody could help me after a few months with this problem. 

Please, I really don't want to use Windows anymore as I love Linux so much.

What distros have you tried, and do you know what kernels you've tried?

Try something like Mepis Linux, they use a nice kernel :)

If you can install Ubuntu, do all the updates and then select the newest kernel from grub.

---

### Post by Raskula on 2009-03-22
Alright ill have a look into it tomorrow when I get more time. Thanks for the fast reply!

---

### Post by linuxisevolution on 2009-03-22
> **Raskula said:**
> Alright ill have a look into it tomorrow when I get more time. Thanks for the fast reply!

Ok. Your welcome! :p

---

### Post by Raskula on 2009-03-23
Yeah I tried Mepis it freezes in there too.

I don't know what the heck the problem is.


Does it have to do anything with  the fact that this message comes up every time I boot into linux?

"expected reference package element found type 0"

---

### Post by damis648 on 2009-03-23
Do the lights on your keyboard blink when this happens?

---

### Post by Raskula on 2009-03-23
Well what happens is,

I turn the computer on, all 3 lights near the numlock go on then off, but the numlock light stays on.

Then after the grub menu passes, the expected type thing error comes up and the numlock light goes out.

---

### Post by linuxisevolution on 2009-03-23
> **Raskula said:**
> Well what happens is,

I turn the computer on, all 3 lights near the numlock go on then off, but the numlock light stays on.

Then after the grub menu passes, the expected type thing error comes up and the numlock light goes out.

Thats normal. The reason we asked is because if the two keyboard lights blink it is a kernel panic. Since this isn't a kernel panic, it sounds like a Xorg problem.

Try a distro that uses a different frambuffer/X managment set:

try Damn small Linux.

---

### Post by themusicalduck on 2009-03-23
How did you install the nvidia drivers? If you are using the driver you can download from the nvidia site, it will usually overwrite your xorg with a custom one. It's also better than using the drivers from the repositories as it is much more up to date. Installing a different version of linux might not help if the problem is with the drivers.

If you download the nvidia drivers from the site and need more help on how to install it then don't hesitate to ask again since it isn't immediately obvious to a new user.

---

### Post by Raskula on 2009-03-23
I figured out it wasn't the Nvidia driver after I tried using the OS for a while without it.

I'll try DSL and get back to you.

---

### Post by themusicalduck on 2009-03-23
All I'm thinking is that the Nvidia driver from the website replaces the xorg config file with a custom one, I don't know if the one from the repos does this. It sounds a bit like it might be an xorg problem with the distorted screen you described. If you were using the driver from the website then obviously this won't help so you can ignore my suggestion :)

---

### Post by Raskula on 2009-03-23
Well I have no idea how to setup DSL, are there any others? Do you think Fedora might have it fixed now?

I think fedora doesn't even use xorg.conf.

If its an xorg.conf crash wouldn't I be able to alt+F1 or ALT+CTRL+Backspace? Because I have to shut off the power in order to get out of the crash.

---

### Post by linuxisevolution on 2009-03-25
> **Raskula said:**
> Well I have no idea how to setup DSL, are there any others? Do you think Fedora might have it fixed now?

I think fedora doesn't even use xorg.conf.

If its an xorg.conf crash wouldn't I be able to alt+F1 or ALT+CTRL+Backspace? Because I have to shut off the power in order to get out of the crash.

Well, it is possible that the kernel is simply not compatible and the devs don't know so they haven't fixed it in the newer releases. 

DSL has an older kernel, which is why I want you to test it. Download the cd and right click desktop and click setup >> install to hdd or something like that. Look around the menus until you find something about installing.

Once you start the installer it only takes ~5min.

---

### Post by moodhugs on 2009-04-02
I have Debian linux. and i also have an emachines el1200 and it is definately the newer kernel (debian's 2.6.26-1) that makes it crash. not distribution related and not video driver related (it still crashes with the display manager and X not running). i run on the debian etch kernel (2.6.18-6) and it does not crash at all. 

recently however, i did a software upgrade and my sound won't work with the old kernel anymore. so i need to find an answer why the new kernel is broken. i use the new kernel on my other computer and it works fine.

but on this computer it crashes spontaniously. either the kernel gets fixed or i have to reinstall all over again (unless there's another way to downgrade.)

would compiling a custom kernel of the new varient with options help? i need help.

---

