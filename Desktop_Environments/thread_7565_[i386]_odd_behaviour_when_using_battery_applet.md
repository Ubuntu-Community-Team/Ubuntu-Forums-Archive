---
title: "[i386] odd behaviour when using battery applet"
date: 2004-12-08
forum: Desktop Environments
---

### Post by feneks on 2004-12-08
Hello to all!

I just have a funny problem. I recognized that my mousepointer jerks und sometimes  randomly jumps to another point of the screen. First I thought that the Xserver (XFree86) isn't well configured but regardless of which configuration I set the mouse kept it's odd behaviour.

Later on I realised that the mouse does well in GDM and starts to tease me when the battery applet is started. As soon as I deleted the applet from the panel the mouse did fine.

I don't think it's a matter of lack of RAM. - having 256MB
I'm using the touchpad. 
It's an "IPC Highnote U" notebook (the firm is now known as "Chilli Green")
It's a bit old so I use APM.

Has ANYONE an idea why this happens?  [-o<   :???: 
Thanks for any hints.

---

### Post by feneks on 2004-12-08
I just had a look at my dmesg and found some disturbing lines:

[COLOR=Olive]...
Synaptics Touchpad, model: 1
Firmware: 4.1
Sensor: 8
new absolute packet format
input: SynPS/2 Synaptics TouchPad on isa0060/serio2
mice: PS/2 mouse device common for all mice
...
ohci_hcd 0000:00:01.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
psmouse.c: TouchPad at isa0060/serio2/input0 lost synchronization, throwing 4 bytes away.
psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio2/input0 - driver resynched.
ohci_hcd 0000:00:01.3: irq 11, pci mem cfa70000
ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
... [/COLOR]

doesn't look fine ...

/var/log/messages is filled with similar lines.
[COLOR=Olive]Dec  8 23:27:47 localhost kernel: psmouse.c: TouchPad at isa0060/serio2/input0 - driver resynched.
Dec  8 23:27:48 localhost kernel: psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
Dec  8 23:27:48 localhost kernel: psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Dec  8 23:27:48 localhost kernel: psmouse.c: TouchPad at isa0060/serio2/input0 - driver resynched. [/COLOR]

---

### Post by blujay on 2005-01-14
I've been having this exact same problem.

FINALLY, by upgrading to a 2.6.10 kernel (Debian 3.1 testing, used kernel-image package from unstable), it is fixed!

If anyone else is having this problem, e-mail me and I will try to help you.

---

### Post by feneks on 2005-01-16
Thanks a lot. I'm happy that this bug vanished in the kernel.
In my case I solved the problem in a different way. I realiced that my Notebook is capable of ACPI after all. It's a very simply support but it works and the odd behaviour doesn't occur anymore.

---

### Post by xy77 on 2005-03-19
Hello,

I still have this problem with a 2.6.10-5-ubuntu kernel on my DELL Inspiron 4000 which I'm going to give to my wife (I got me an IBM Thinkpad T42p).

Stopping powernowd via
```
sudo /etc/init.d/powernowd stop
```
works, but I don't want her to have to execute this command. I tried to uninstall powernowd, but it wants to uninstall the ubuntu-desktop:
> 
The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).

which I'd rather not uninstall due to update issues.

Can anyone recommend a good solution, that's no hack (it might be a script, though)?

Thanks in advance.

greetings,
  David (xy77)

EDIT: Perhaps I should note, that I use Hoary, not Warty, but I don't think this will make a big difference.

And: Hello members of the ubuntu-community! This is my first post and I'm using Ubuntu since two weeks, now, coming from Gentoo (just for a bit of background information).

---

### Post by xy77 on 2005-03-19
Okay, after a short visit in #ubuntu I found out that it's easy to disable daemons by using rcconf (install it with synaptic). Just run the program ```
# sudo rcconf 
``` and uncheck powernowd.
To stop the service:
```
sudo /etc/init.d/powernowd stop
```
Next time you start your computer, it won't start again. You might have deleted all /etc/rc*X*.d/S20powernowd , but to use rcconf is nicer IMHO.

This is only a workaround, since powernowd won't be available any more (which means CPU-frequency scaling is not applied. It may be, that different daemons can take the job over, but I don't bother to find out. Perhaps eventually the kernel bug will be removed.

greetings,
  David (xy77)

---

### Post by CowPie on 2005-04-11
[QUOTE=xy77]Okay, after a short visit in #ubuntu I found out that it's easy to disable daemons by using rcconf (install it with synaptic). Just run the program ```
# sudo rcconf 
``` and uncheck powernowd.
To stop the service:
```
sudo /etc/init.d/powernowd stop
```
Next time you start your computer, it won't start again. You might have deleted all /etc/rc*X*.d/S20powernowd , but to use rcconf is nicer IMHO.

This is only a workaround, since powernowd won't be available any more (which means CPU-frequency scaling is not applied. It may be, that different daemons can take the job over, but I don't bother to find out. Perhaps eventually the kernel bug will be removed.

greetings,
  David (xy77)[/QUOTE]
Thank you for this highly informative post; it's fixed my problem. Strangely enough, I am using a normal desktop pc...not a laptop.

---

### Post by xy77 on 2005-04-15
[QUOTE=CowPie]Thank you for this highly informative post; it's fixed my problem. Strangely enough, I am using a normal desktop pc...not a laptop.[/QUOTE]

I guess there's powermanagement with desktop pcs as well. Standby, Suspend to Disk etc, isn't it? (I haven't owned a desktop since 3-4 years, so I don't know exactly)

Greetings,
  David (xy77)

---

### Post by eoosting on 2005-04-24
I had the same problem with my laptop. The mouse would ocasionally hang then jump to another part of the screen. Like you guys, I figured out that disabling powernowd would fix the problem. I did a bit more troubleshooting and I found that the I could corolate the mouse hangs with the exact time that the powernowd daemon would switch the CPU frequency on my processor.

If you want to try this for your self, simply kill the powernowd process and run it again as root like "powernowd -vv -d" ... This will put it in verbose mode and ask it not to detach from the controling vty. Then to a tail -f /var/log/messages in another window.

The next step is easy, find a cpu hog like a short compile, and kick it off while moving the mouse. As soon as powernowd detects over 80% cpu it will kick the processor into high gear, if you are using your mouse at the time, your mouse will hang and a message "lost sync at byte ..." or other ps2 error message will print. When the copile is done, your processer will begin to step down, when it gets to the lowest level if you are moving your mouse it will again hang and another message will print.

This isn't a problem with powernowd so much as it is either a problem with the ps2 mouse driver or the kernel. powernowd is just changing the frequency of the cpu ... its easy to imagine a case where a processor frequency switch could cause a loss of sync with some of the perepherals.

My next step is to figure out if it is a problem with the cpu scaling part of the kernel or the mouse driver. If anyone else has ideas, let me know.

Eric

---

### Post by apos on 2008-02-23
Add "i8042.nomux=1" to your kernel boot parameter list and the problem should be gone!

(GERMAN) [http://forum.ubuntuusers.de/topic/84596/?p=1245699#1245699](http://forum.ubuntuusers.de/topic/84596/?p=1245699#1245699)

---

