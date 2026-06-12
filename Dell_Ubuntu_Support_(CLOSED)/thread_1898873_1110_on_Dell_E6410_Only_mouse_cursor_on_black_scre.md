---
title: "11/10 on Dell E6410: Only mouse cursor on black screen w/ docking station"
date: 2011-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jeff Murdoch on 2011-12-22
After updating my Dell Latitude  E6410 fro Ubuntu 10/10 to Ubuntu 11/04-64 and kernel 2.6.38-13 no boot was possible at all when connected to an external display or docking station/port connector.

So I updated to 11/10-64. Now it's able to boot if the external display is connected to the notebook's vga port - and startup is also successful in docking station with no external monitor connected.

But when I switch on in docking station with monitor connected to a "external" port (dvi/vga the same) I get  no login screen but only a blank black screen, sometimes with a mouse cursor on it - and have to restart. When I connect the monitor to docking station's port after boot process has finished and Unity desktop shows up - everything's ok.

I also got no problem at startup with monitor connected to docking station, if I boot from a Ubuntu live CD!

Not so funny again. Might the two update steps from 10/10 to 11/04 and from 11/04 to 11/10 have messed up some configuration? What could I do? Would I have to reinstall completely?


TIA!

---

### Post by Jeff Murdoch on 2012-01-02
Edited my question to supply more precise info.  Any help appreciated!

---

### Post by mathman316 on 2012-01-12
I have a similar problem, on a Dell e6510 with Ubuntu 11.04.  Boot works properly if I am not docked, or if I dock *after* the login screen appears.  However, when starting up or restarting after docked, at some point in the boot process the laptop screen goes blank (off), display switches to external monitor only, and when the "ubuntu with five dots" splash appears the whole system hangs and will not boot; I have to do a forced shutdown with the power switch.

Recently I have also seen a related problem: if I dock the computer while suspended, wake up from suspend, then both monitors work correctly.  I log in, and *then* disable wireless by turning off the wifi switch.  *Both* screens turn off and system stops responding completely; again I must force shutdown.

Ubuntu 11.04, kernel 2.6.38-13, Dell Latitude e6510 (dual boot with WinXP SP3)

---

### Post by mathman316 on 2012-01-12
Clarification: the wifi switch freeze problem I mentioned above started a couple days ago, after using **rfkill** to work with the wireless.

A couple days ago, I enable wifi by the hardware switch but the wifi indicator didn't light, and in the networking menu the entry "Wireless disable by hardware switch" was still present.  I discovered **rfkill** and used **rfkill list**, which indeed showed that the wifi adaptor was software-enabled and hardware-disabled, *contrary to the fact that the switch was enabled*.  Before rebooting, I tried **rfkill unblock <number>** to see if that would activate the wireless, and voila! the wireless was activated and indicator was lit.  Strange....

But only after this did deactivating wireless via hardware switch while docked, cause a total freeze/hang.

---

