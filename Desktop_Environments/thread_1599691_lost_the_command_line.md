---
title: "lost the command line"
date: 2010-10-18
forum: Desktop Environments
---

### Post by jarrah-95 on 2010-10-18
i have been trying to create a ubuntu install from the commandline and have run into a little truble. i installed the gdm (plus all of the dependancys) but then accidently booted into it. to problem is that now it always boots to gdm, not my old cli. and  havent installed any gui terminals (eg gnome terminal) or a package manager. so i cannon do anything with it.

---

### Post by mister_p_1998 on 2010-10-18
hmm do you ever WANT a GUI? if not just sudo apt-get remove ubuntu-desktop

Steve

---

### Post by jarrah-95 on 2010-10-18
i want the gui, but the problem is that i cannot access the cli, and cannot install anything from the gui

---

### Post by coffeecat on 2010-10-18
Simply press alt-ctr-F1 or alt-ctrl-F2 (....F3...F4...F5...F6) to get one of the virtual consoles to log into.

---

### Post by jarrah-95 on 2010-10-18
thanks but ive tryed that to, im using virtual box to run it, and when i do that it gives me a terminal, but for the host not the virtual machiene i want it to do it in

---

### Post by sikander3786 on 2010-10-18
As **coffeecat** mentioned, you can login to virtual console.

In addition you can select Recovery Mode from Grub Menu and Drop to root shell.

> cannot install anything from the gui

Why so? It is a serious problem. What happens when you try to install anything?

---

### Post by jarrah-95 on 2010-10-18
oh and just to add another thing, because theres no other os on the machiene, grub doesn't appear at boot so i cannot get access to recovery mode

---

### Post by coffeecat on 2010-10-18
You need to mouse-click on the VirtualBox window to capture the keyboard and mouse I should think before you press alt-ctrl-F1.

Or - boot up in recovery mode. You'll get an option to choose drop to root terminal with networking. When you get the # prompt you are root, so you can apt-get and do whatever else you need without using sudo.

**Edit:** you posted the comment about the grub menu just as I posted. You need to capture the keyboard and mouse in the same way so that you can press SHIFT to show the grub menu. But you'll have to be very quick. I had a similar problem instaling Vista to a Vbox guest machine, trying to press F8 to get safe mode and not being quick enough capturing the mouse.

---

### Post by jarrah-95 on 2010-10-18
nope, even when i click in (capture the mouse) it still launches it in the host.

---

### Post by jarrah-95 on 2010-10-18
thanks, that worked, all i had to do was hold down shift (took about 3 trys).
just thought i should post a hard question for once. hopfuly i dont get stuck with the same problem when i do it for real with the computer.

---

### Post by coffeecat on 2010-10-18
OK - a couple more thoughts/ideas.

Set the virtual machine to boot from an Ubuntu live ISO. Once you're in the live desktop, you can mount the virtual HD in the usual way from the Places menu. Then you could either:

Edit whatever system files you need to edit to stop gdm launching so that next time you boot you get the CLI.

OR..

Chroot into the virtual HD install. By doing that you'll have a root terminal in the HD environment and you can continue with apt-getting whatever you need.

Post back if you need help with chrooting.

**Edit:** OK, I see that SHIFT worked eventually. But just for fun, why not try one of the above, even as a tryout to see how it works. :)

Good luck!

---

### Post by sikander3786 on 2010-10-18
For the host, you can add **Option "DontVTSwitch" "true"** in xorg.conf. Lucid doesn't use xorg.conf so you'll have to create a blank file with proper options.

Might be coffeecat can enlighten better on this.

---

### Post by coffeecat on 2010-10-18
> **sikander3786 said:**
> Might be coffeecat can enlighten better on this.

No, that one's new to me so thanks for posting it.

---

