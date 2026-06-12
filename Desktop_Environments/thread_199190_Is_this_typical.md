---
title: "Is this typical?"
date: 2006-06-18
forum: Desktop Environments
---

### Post by Dargo on 2006-06-18
Greetings,

Sometimes when I start up Kubuntu there's a notification icon in the tray signfying that there are updates available.  Today when I woke up, for instance, there were approaching 50 new updated packages.  Now, being the lazy sort I usually just apply them all -- it can't hurt to be the most current, right?

My question is this: today included in the updates was a kernel upgrade 2.6.15-23 to 2.6.15-25 which sounds nice but whenever I get one of these some things need to be recompiled for the new kernel version.  Does everybody just slog through this process, or is there some cool fancy way to automatically recompile/reinstall certain packages whenever there's a kernel upgrade?

For instance, today because of the kernel update I couldn't boot into the graphical KDE environment without first rebooting to the recovery console and rerunning the Nvidia installer.  Then, I couldn't get online because I had to recompile my madwifi driver.  I can do this stuff, it just seems like a high price to pay for sleepily clicking on "Apply All Updates" shortly after waking up this morning, and it would send my wife flying back to the grub menu faster than you can say "sudo reboot"!

So... is this what everybody does, or is there some easier way I missed along the line?

---

### Post by johnc4510 on 2006-06-18
This is what we all do when we get a kernel update. To most of us though, it is a small price to pay in exchange for what we think is a top notch operating system.

---

### Post by [S|G] on 2006-06-18
Well, you can create a shell script to automate the process of compiling lots of stuff. You'd still have to run the script every time you updated your kernel, but that way you'd only have to type one command instead of lots of them.

---

### Post by caserio on 2006-06-18
Hi,

Well,  kernel updating is a smooth and transparent process on my box. No madwifi driver to care about. No Nvidia installer to run (once again...) thanks to the linux-restricted-modules...

---

### Post by joelito on 2006-06-18
no problems here, all my drivers are either in the kernel or in the linux-restricted-modules

---

### Post by angkor on 2006-06-18
[QUOTE=Dargo]So... is this what everybody does, or is there some easier way I missed along the line?[/QUOTE]

You could just choose to update the kernel once a month for example, unless you have a specific reason to install the new kernel right away. Anyway, kernel upgrades don't come by a lot so it's not too much work.

---

### Post by Dargo on 2006-06-19
Thanks for all of the tips everyone! You guys have made this truly a friendly community.  

I think that I'll try my hand at shell scripting.  Can anybody think of a clever way that I could script (maybe during boot up?) that the the kernel version has changed so I could automatically recompile and reinstall the affected drivers?

---

### Post by Lunar_Lamp on 2006-06-19
I'm very new to shell scripting, so I won't risk screwing up your system by giving you real code, I'll just offer some semi psedo-code instead - don't quote me on syntax or anything - but hopefully it should give someone an idea of a potential way to tackle the problem:

```

PrevKernel=~/.CurrentKernel

if [ "uname -r" == "$PrevKernel" ]; then
    exit
else {do stuff}; uname -r > ~/.CurentKernel  
fi

```

---

