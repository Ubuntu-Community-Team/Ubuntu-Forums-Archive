---
title: "strange problem (ati?)"
date: 2006-06-02
forum: Desktop Environments
---

### Post by zopar on 2006-06-02
I have installed by zero dapper (kubuntu) and i have installed ati proprietary driver.

If i click shutdown or reboot button on kde menu, pc freeze with black screen,
but if i shutdown with "sudo halt" or reboot with "sudo reboot" on shell i don't have this problem and work correctly with usplah.

I suppose is a problem on X killing during the reboot (and shutdown) for initializing usplah but i don't have idea for fix this problem.

You have similar problem?
Have any ideas?

P.S. my laptop is an acer aspire 3023wlmi with ati x700 mobility radeon. (with vesa driver don't have problem)

---

### Post by zopar on 2006-06-02
up

another "problem related":
if running xawtv black screen (not freeze) for delet black screen i switch (ctrl alt f1) in console and re-switch (ctrl-alt-f7) in graphic mode. I suppose is a problem in ati driver o configuration, it's very similar to freeze problem on reboot and shutdown.

---

### Post by rogeriovinhal on 2006-06-02
I had a similar problem with many versions of dapper beta, and many other people. So they filled it a bug and sent to launchpad.
I don't know what have been done about it, but something that actually fixes it is using GDM instead of KDM.
Apparenttly, ATI has issues with this version of KDM. I switched it to GDM and have been working flawlessly.

---

### Post by BaffledMollusc on 2006-06-02
Yes! Someone else with the same problem as me. The same thing happens to me: after I installed the ATI proprietory driver for my X800 Pro, the system hangs on shutdown with a black screen.

There are some differences though. I'm using Gnome, not Kubuntu, so that doesn't seem to be the problem. Furthermore, the problem occurs even if I issue a "sudo reboot" from the terminal command line.

Anyone else have any ideas? Or can anyone tell me how to do a shutdown with lots of debug text so I can see what point it gets up to before hanging?

Edit: The hang occurs the moment I give the command "sudo /etc/init.d/gdm stop", if that helps. So it seems to have something to do with stopping the GDM, but I don't know what.

---

### Post by todak on 2006-06-03
When I installed Dapper, I let it install the default radeon driver and have 3D support with no problems at all. I used to install the proprietary drivers as a matter of course, but found they caused too many difficulties. Uninstalling the ATI driver and using the default driver should fix things for you.

Maybe we should be filing bug reports with ATI and tell them their drivers are broken!

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=todak]When I installed Dapper, I let it install the default radeon driver and have 3D support with no problems at all. I used to install the proprietary drivers as a matter of course, but found they caused too many difficulties. Uninstalling the ATI driver and using the default driver should fix things for you.[/QUOTE]
That would have been my choice, but unfortunately I had to install the binary ATI driver to solve another bug. The default installation was locked at 600x480 resolution and nothing I did could fix it. The correct modes and resolutions were in the xorg.conf file; they just didn't show up in the menu for changin resolutions. I tried for ages to fix it; nothing worked.

Finally I gave up and installed the proprietory ATI driver which fixed the resolution problem but introduced the "hang on shutdown or reboot" bug. I still haven't found a fix for this and it's *really* irritating.

Still, you've given me an idea: I'll uninstall the ATI driver and hope the resolution problem doesn't reappear. Worth a try, at least. 

Uh, how do I uninstall it and start using the mesa driver again? Do I just "remove all" for the fglrx driver in Synpatic, and then edit my xorg.conf file to use driver "ati" instead of driver "fglrx"?

---

### Post by todak on 2006-06-03
[QUOTE=BaffledMollusc]

Uh, how do I uninstall it and start using the mesa driver again? Do I just "remove all" for the fglrx driver in Synpatic, and then edit my xorg.conf file to use driver "ati" instead of driver "fglrx"?[/QUOTE]

Yes, that is how I did it. I have no video problems using the default driver on my Radeon 9600 card.

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=todak]Yes, that is how I did it. I have no video problems using the default driver on my Radeon 9600 card.[/QUOTE]
Unfortunately it didn't work. Reverting to the default driver brought back the 600x480 resolution problem, although it did fix my "unable to shutdown" bug.

I seem to have live with one or the other. Since 600x480 is unusable, I've gone back to the fglrx driver and will probably have to live with the shutdown hang problem.

Sigh.

---

### Post by zopar on 2006-06-03
I suppose is NOT a problem of ATI driver (if is a problem of driver ati is for last realease).
In fact during dapper development the problem is random!
with flight 3 for example no problem, aftter 10-11 days and 4-5 upgrade problem is present, another upgrade, no problem ecc ecc...

---

### Post by aouie on 2006-06-07
If you are having freezes (or crashes) while shutting down (or logging out / log out / end current session) then disabling spash in the bootup / shutdown sequence should bypass the bug.
As pointed out in [a different post]("http://ubuntuforums.org/showthread.php?t=190769")
disabling splash from /boot/grub/menu.lst will bypass the shutdown freeze.
It worked for me (upgraded to Dapper, NVidia 5950, Athlon 64).
Sincerely,
Aouie

---

### Post by grinias on 2006-06-07
[QUOTE=aouie]If you are having freezes (or crashes) while shutting down (or logging out / log out / end current session) then disabling spash in the bootup / shutdown sequence should bypass the bug.
As pointed out in [a different post]("http://ubuntuforums.org/showthread.php?t=190769")
disabling splash from /boot/grub/menu.lst will bypass the shutdown freeze.
It worked for me (upgraded to Dapper, NVidia 5950, Athlon 64).
Sincerely,
Aouie[/QUOTE]

But it didn' t work for ati X600 with fglrx driver...

---

### Post by grinias on 2006-06-07
I think the solution for fglrx is to put in comments the line

 Option          "DPMS"

of 

Section "Monitor"

in /etc/X11/xorg.conf

In fact I had to disable DPMS usage (and not only that) from /etc/default/acpi-support 
in order to have suspend and hibernation support in my ACER TM 4101 machine.

Keep testing :)

Elias

---

### Post by grinias on 2006-06-08
No, it didn't work finally. Today it happened again.
Sorry for that.

---

