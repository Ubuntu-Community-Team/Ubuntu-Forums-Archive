---
title: "Screen stays black after ever Xorg restart"
date: 2005-05-04
forum: Desktop Environments
---

### Post by Xgkkp on 2005-05-04
This is a problem that has been bugging me for a while, and I can't seem to get started. Everything is working, I can log in and use the computer fine, except if I log out, or X crashes it trys to reload but simply stays at a black screen. I know the background is still working because my music keeps playing (I use a daemon-based music player), yet I cannot even switch to any of the virtual consoles using ctrl-alt.

I had a quick look at the bottoms of the Xorg.log files, but can't see anything immediately standing out.

does anyone have any idea what is wrong, or how to start fixing it? (or at least finding out what the problem is)

---

### Post by oled on 2005-05-05
I have a similar problem. If I try to shutdown, reset X(ctrl+alt+bcksp) or open a console the screen just goes blank and nothing more happends after Gnome closes. 

I think it may be a problem with nvidia drivers and dualview.

What kind of gfx do you have ??? I have a gf ti4200.

I haven't had time to test it yet. Can't live without my tvout, so i would rather live with having to turn of my computer the hard way, than to live without tvout. 

OleD

---

### Post by liljencrantz on 2005-05-05
[QUOTE=oled]I have a similar problem. If I try to shutdown, reset X(ctrl+alt+bcksp) or open a console the screen just goes blank and nothing more happends after Gnome closes. 

I think it may be a problem with nvidia drivers and dualview.

What kind of gfx do you have ??? I have a gf ti4200.

I haven't had time to test it yet. Can't live without my tvout, so i would rather live with having to turn of my computer the hard way, than to live without tvout. 

OleD[/QUOTE]

I have exactly the same problem with my nVidia card.

---

### Post by Stormy Eyes on 2005-05-05
I have this too sometimes. I solve it with the following steps.

1. Hit CTRL+ALT+F1
2. Login.
3. sudo /etc/init.d/gdm restart && exit

---

### Post by Xgkkp on 2005-05-06
[QUOTE=Stormy Eyes]I have this too sometimes. I solve it with the following steps.
1. Hit CTRL+ALT+F1
[/QUOTE]
As I said, this doesn't work for me

---

### Post by Sethleben on 2005-07-05
[QUOTE=Xgkkp]This is a problem that has been bugging me for a while, and I can't seem to get started. Everything is working, I can log in and use the computer fine, except if I log out, or X crashes it trys to reload but simply stays at a black screen. I know the background is still working because my music keeps playing (I use a daemon-based music player), yet I cannot even switch to any of the virtual consoles using ctrl-alt.

I had a quick look at the bottoms of the Xorg.log files, but can't see anything immediately standing out.

does anyone have any idea what is wrong, or how to start fixing it? (or at least finding out what the problem is)[/QUOTE]
 Every time I hit Ctrl+Alt+Backspace to restart GNOME I get a black screen followed by a prompt to login, and then a password prompt. After typing the password in I get a grey screen with a cross in the centre, and a terminal window then appears, but nothing else.

Consequently I always end up rebooting fully when all I need to do is restart GNOME. I am using an nVidia MX 4000, but the problem was there before I installed the nVidia drivers, and also on my last graphics card (which was some old ATi thing, I can't remember what).

Anyone have any ideas?

Cheers.

---

### Post by jimchristopher on 2005-12-27
I have this problem as well, I am using an ATI X800XL with the fglrx driver, Shuttle SN25P,  this happens in gnome and in KDE.  If I log out/exit session whatever, it just dumps me to a black screen. I never get a prompt, and I cant tell if its accepting keyboard input.  I've tried typing startx, init 3/init 5/startx etc.  nothing will get the system back except a ctrl alt del reboot.

---

### Post by rivethead on 2006-06-08
This problem is still present for me on a Dell XPS Gen2 laptop after a Dapper Update, anyone have any fixes for this yet?

-Rvt

---

### Post by isak_b on 2007-09-28
I have this same problem after installing fglrx, in order to use Beryl with my X800XL, and ViewSonic VP191b.

I have edited the xorg.conf file and it seems to be correct. If I start in recovery mode and type **startx**, X starts as it should. If I press CTRL+ALT+BACKSPACE, my monitor just turns black and then its led switches to orange (same effect as if the signal turns off).

If I exit X, the same thing happens.

When I boot up normally -- or if I use recovery mode and type **sudo /etc/init.d gdm (re)start** -- I get the same error, and will have to do a hard reboot.

It seems as if the fglrx driver cannot go to the terminal (CTRL+ALT+F1) either...

Any help will be very much appreciated, since I would really like to try Beryl on this computer.

[B]
In my Xorg.0.log file, I have these errors and warnings:[/B]
[LIST]
[*](EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7

[*](WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[*](WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[*](WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found <------ this is my second PCI express slot, I suppose... not used
[*](WW) fglrx(0): board is an unknown third party board, chipset is supported
[*](WW) fglrx(0): Option "VendorName" is not used
[*](WW) fglrx(0): Option "ModelName" is not used
[/LIST]

---

