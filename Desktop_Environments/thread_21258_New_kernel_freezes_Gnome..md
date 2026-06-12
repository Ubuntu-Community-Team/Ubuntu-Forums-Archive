---
title: "New kernel freezes Gnome."
date: 2005-03-21
forum: Desktop Environments
---

### Post by MicroChris on 2005-03-21
Hey guys,

I don't know if anyone has a similar problem.

I installed the 2.6.11.x-686 kernel last night and tried to boot it, but I get passed the login screen and Gnome totally locks up. My Hard Drive light doesn't do anything. Seems like somethings sending the kernel into a panic.

I did some searching and found that some people had this problem with 2.6.10.x, but no solid answer as to why it caused this.

Anyone know a solution?

Thanks!
Chris

---

### Post by Joeb on 2005-03-21
I had the same problem.  Gnome started to draw the desktop but just froze.  I had to go back to the latest 2.6.10.x kernel.  BTW, I wasn't using 686 version and still had this problem, so I don't think it is related to that.

On another note, are odd numbered kernels for production or are they development releases (ie is 2.6.11 the development release on it's way to becoming 2.6.12)?

---

### Post by eljo on 2005-03-21
[QUOTE=Joeb]On another note, are odd numbered kernels for production or are they development releases (ie is 2.6.11 the development release on it's way to becoming 2.6.12)?[/QUOTE]

You're right that odd numbered kernels are development releases, but this applies to the second digit:
2.4.x is a production release
2.5.x is a development release

Sadly, at this time there is no 2.7 and there seems to be much development going on in the 2.6 line.

---

### Post by Rock on 2005-03-21
I had this problem as well.

---

### Post by sucho on 2005-03-21
same problem here, but with xfce :(

---

### Post by fackamato on 2005-03-21
It's a problem with the nvidia driver, search for patches, on nvnews and rage3d.

---

### Post by sucho on 2005-03-23
i dont think its nvidia problem, i have intel graphics card

---

### Post by Trevor Bramble on 2005-03-23
[QUOTE=sucho]i dont think its nvidia problem, i have intel graphics card[/QUOTE]

Agreed, I have ATI and I'm seeing the same thing.


**edit**

Actually, in the weak hope that this thread may succeed where so many others have failed, here is some more info (as posted to the Ubuntu users listserv and comp.os.linux.x):

[INDENT]So, I've gone around and around and around with this problem and still
no solution is in sight.  I now humbly beg Usenet for help.

Gear:
Tyan Tiger 230 (S2507 D) w/ Apollo Pro 133A
ATI Radeon 9000 64MB DDR (AGP 2x/4x)

Environment:
Ubuntu Hoary 5.04
Linux 2.6.10-5-686-smp
X.org 6.8.2

Driver:
ATI Proprietary Linux x86 Drivers for XFree86/X.Org Version 8.10.19

Logs, configs, lists:
[http://trevorbramble.com/linux/fglrx/](http://trevorbramble.com/linux/fglrx/)

Goal:
Hardware accelerated 3-D rendering.  I'm a gamer among other things, and
attempting to convert wholly to a Linux desktop.

Scenario:
After fighting through a variety of errors and problematic
configurations I have succeeded in creating a configuration that does
not result in any errors.  AGP, DRI, all seems to be initialized correctly.

However all is not right.  GDM will start, prompting me for my username,
and then for my password.  After entering them, I hear the startup
music, the hard disk grinds a bit, and nothing at all changes onscreen.
~ I see the password window as if it were now the wallpaper for a desktop
without toolbars - completely flat with no way to interact.

Keyboard input of any kind is totally ignored.  Though I can change to
tty screens and back using alt+f?/f7 before submitting the password,
after submitting it the keyboard is just a lump of plastic.  My mouse
pointer will glide around on screen as long as my frustrated claw
continues to direct it.  I'm forced to bounce the machine.

I'm far from new to computers and Linux, but that does not include X,
Gnome, or related graphical items in Linux.  So I wouldn't be surprised
if I made some ignorant error that is causing this.  However at this
point I estimate I've read between 400 and 50,000 pages of material
regarding the ingredients of my recipe of discontent, and I feel I'm
unlikely to turn up anything new using that method.

I've experienced a variety of problems on this journey, both with Ubuntu
Warty, using XFree86, and Slackware 10 (my first choice) with X.org
prior to the Ubuntu Hoary and X.org setup.  I've attempted using the
free driver (radeon) in all cases first, with even less success than I'm
seeing now.

So... help?

Thanks in advance.

Cheers,
Trevor [/INDENT]

And a later follow-up in the usenet thread:

[INDENT]Thanks for you advice, Martin.  You appear to be correct.  The problem
is with Gnome.  If I load xinit from runlevel 3, glxinfo reports the
Radeon 3d drivers are loaded.

I installed fvwm to see how that would go, but loading it from GDM lead
to a total lockup within about a minute of use.

Unfortunately, I have no idea how to proceed at this point (other than
filing a bug with Ubuntu).  I'm not interested in KDE, and not
comfortable enough with desktop Linux to trade Gnome for a more minimal
window manager yet (though I intend to eventually). [/INDENT]

---

