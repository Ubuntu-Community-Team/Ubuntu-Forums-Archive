---
title: "Compiz Reset at Restart! Stuck at 'Visual Effects: None'"
date: 2009-11-15
forum: Desktop Environments
---

### Post by gunith on 2009-11-15
Hi guys,

My machine, a [Dell Vostro 220s]("http://www.dell.com/us/en/business/desktops/desktop-vostro-220st/pd.aspx?refid=desktop-vostro-220st&cs=04&s=bsd") with integrated Intel®  GMA X4500HD and a Viewsonic E50c Monitor was running 'Normal' or even 'Extra' setting properly till yesterday on the very new Karmic (even though it didn't pass 'None' in 9.04)

Did do a bit of experimenting with the Compiz manager yesterday.

Today I turned it on to find my Display settings disappeared!. 

Tried 'compiz-check'.. Here's the output

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


```
Somehow, Rendering method returns 'None'

glxinfo returns this,

```
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

Even tried removing my Compiz settings.. Still nothing

Tried stuff by Googling but never quite worked

Attached my Xorg.0.log

Please help! Thanks a lot in advance :)

---

### Post by JBAlaska on 2009-11-15
From looking at your xorg log, there seem to be some ATI fglrx modules loading;

```
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.4.0, module version = 1.0.0
```

```
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.66.10
```

Since I'm no expert and no longer have a Intel gpu based system to compare with, I'm not 100% sure if this is "normal" or not, but by looking at my Nvidia system's xorg log, there are NO ATI fglrx modules loading.

Please post the contents of your ```
/etc/X11/xorg.conf
``` and I'll try to help you get this sorted.

---

### Post by gunith on 2009-11-15
Thanks a lot JBAlaska for the quick reply...

This is an awesome find.. BTW, i thought in these lines and found this post: [http://ubuntuforums.org/showthread.php?t=640024](http://ubuntuforums.org/showthread.php?t=640024)

Tried the steps with no luck :(

I think my xorg.conf is pretty default [attached], It was like this even before I did the steps of above...

The only clue how those files got there maybe when i was installing or configuring something. BTW, I also noticed this in my PC's product page,
[http://www.dell.com/us/en/business/desktops/desktop-vostro-220st/pd.aspx?refid=desktop-vostro-220st&cs=04&s=bsd](http://www.dell.com/us/en/business/desktops/desktop-vostro-220st/pd.aspx?refid=desktop-vostro-220st&cs=04&s=bsd)

> **Discrete Graphics options from ATI:** 
256MB ATI RadeonTM   HD 3450 (DVI, HDMI) - Low Profile


Would that be any help :-?

---

### Post by gunith on 2009-11-15
Something else I tried and failed: [URL="https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel"]https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel
[/URL]

---

### Post by JBAlaska on 2009-11-15
[quote="gunith"]Discrete Graphics options from ATI:
256MB ATI RadeonTM HD 3450 (DVI, HDMI) - Low Profile [/quote]

Do you by chance have this optional video card? You may have the intel on-board graphics and this optional card both, look at the connector ware your monitor cable connects to your case, do you see another connector like that back there?

If so we can deal with that, also please post the output of this command run in the terminal:
```
sudo lspci
```

I have to get some sleep (4:00 am here) I will check this thread in the morning.

---

### Post by gunith on 2009-11-15
Good night JBAlaska.. And thanks :D

Will get back

---

### Post by gunith on 2009-11-15
Nope... I do see another serial port, but it got a different notation (10101) compared to the monitor one (|[]|)...

Here's the output from lspci
```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

Interesting that it too doesn't mention anything ATI...

---

### Post by JBAlaska on 2009-11-16
Sorry it took me so long to reply (busy day) before we do crazy s*** like reconfiguring xorg and reinstalling FGLRX...let's try something non-invasive. You said desktop effects worked before..so try booting to the LiveCD, and enabling desktop effects.

If that works, copy your Xorg0.log from the LiveCD session and compare it to your current one.

And Big Bump to others..I said I'm no expert on intel GPU's...so a little help would be nice lol.

---

### Post by gunith on 2009-11-16
Awesome news...

LiveCD worked like a charm! 

While I was browsing the software installed, I figured that I got some ATI Control Center installed somehow :S... (have no idea how it got there)

I managed to remove it and restarted gdm and VOILA! Now things are back in action!

Thanks a lot JBAlaska! & Sorry for being a pain! You're awesome!

---

### Post by JBAlaska on 2009-11-16
Glad I could help in a small way, No way are you a pain..you stuck with it and got it fixed!

Have a great one!

---

