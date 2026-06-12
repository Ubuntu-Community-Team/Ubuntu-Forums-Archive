---
title: "DESKTOP LOCKS UP CANT GET ANY ! HELP from anyone!!!"
date: 2008-12-28
forum: Desktop Environments
---

### Post by bluemax7 on 2008-12-28
I have a AMDK8 winfast mother board with onboard video.
Sometimes the desktop locks up...
and sometimes the video gets corrupted.. like
the desktop does not handle window redraws correctly...

Scrolling and moving windows is all wierd..

reseting the screen resolution seems to get rid of that problem..
but it eventually comes back...

My RAM has tested perfect..
I have shut off all of the services that have to do with power 
saving... ect..

There is NO LOGS in any of the log files that record either of these incidents...

THE WORST IS WHEN THE DESKTOP LOCKS UP !!!
I am not sure if the Kernel is locked up...

But Ctrl-alt-backspace or ALT-F1 doesnt do a friggin thing...

Where the Hell do I find information instead of just trying 
this is or that... modify this or that setting...

Is there a way to get the desktop to log this problem...??
Is there anyway to get HELP WITH SUCH A PROBLEM???

---

### Post by jakon on 2008-12-28
> **bluemax7 said:**
> Is there a way to get the desktop to log this problem...??
Is there anyway to get HELP WITH SUCH A PROBLEM???

Probably!
Press ALT+SysReq+R to let the kernel regain control over the keyboard.
Then CTRL+ALT+F1 should give you a console.

I have seen such problems, too, disabling desktop effects solved it for me.

---

### Post by gettinoriginal on 2008-12-28
Ok, I know it's frustrating, but slow down a minute and I will try.  Not knowing what you have tried, I will start at the beginning.  You don't mention which Ubuntu you are running, but let's start here:

System > Admin > Hardware Drivers, let the system search, then activate it.

System > Pref > Appearance > Visual Effects  should be set to Extra or Custom.

Are you running Compiz ??  If so, install Compiz Fusion Icon (through synaptic) then find it in Applications > System Tools, click it, it will put an icon on your panel.  Right click it and make sure that your Window Decorator and Window Manager are checked as to your choice, and click "reload Window Manager"

---

### Post by steveneddy on 2008-12-28
I would check for hardware compatibility first and foremost. See if anyone is having issues with that MB.

Second I would disable Compiz and get the video drivers correct. 

Please list your system specs (what kinda hardware do you have?)
and tell us what you have done so far?

Please give links to previous threads?

---

### Post by bluemax7 on 2008-12-29
Thanks for the help:

System details: :::::::::::::::::::::::::::::::::::::::::::::::

Release 8.10 Intrepid
Kernel 2.6.27-9 generic
GNOME 2.24.1
Memory 373.3 Mib
Processor AMD Sempron 2800+
HD space 134.2 Gib
I am using an onboard VGA!!!!
can't figure out what it's chipset info is!!

Hardware drivers: ::::::::::::::::::::::::::::::::::::::::::::::
None will list -> no proprietary drivers are in use on this system

in the Xorg.0.log::::::::::::::::::::::::::::::::::::::::::::::::

(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.10.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340

(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.5.0.0)

Using MMX2 method for aligned and non aligned transfers to video ram

QUESTIONS:::::::::::::::::::::::::::::::::::::::::::::::::

1. If I use ALT_SYSREQ-R and then CTRL-ALT-F1 to get to the console
   how do I totally restart the window manager from the prompt so I do not have to reboot.. and get back to the desktop?

2. Where can I get, or how do I make the system search for proprietary drivers to work with my onboard VGA correctly?

OBSERVATIONS:::::::::::::::::::::::::::::::::::::::::::::::

1. Playing with Compiz made my desktop go white.. I was able to break
   out to the console.. but I couldn't figure out how to get back to the  Desktop


Brett

---

### Post by gettinoriginal on 2008-12-29
this will set compiz back to default:
 
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by bluemax7 on 2008-12-29
more information::::::::::::::::::

I used Dconf to get more info on the VGA controller::::::::::::::::::::

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
        Subsystem: Foxconn International, Inc. Device 0c92
        Flags: 66MHz, medium devsel, IRQ 5
        BIST result: 00
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at d000 [size=128]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] AGP version 3.0
        Kernel modules: sisfb

The motherBoard::::::::::::::::::::::::::::::::::::::

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
        Manufacturer: WinFast
        Product Name: 760GXK8MC


There you go...

I noticed that "sometimes" I can get it to lock up.. 
if I try moving 
a window while the HDD is busy.. perhgaps there is just some kind of scheduling conflict amongst everybody... like the video driver
assumes it has contiguos control.. 
but it doesn't, it gets interrupted 
or something..


- Brett

---

### Post by bluemax7 on 2008-12-29
Thanks for your help 

But I don't even know what the heck compiz is!!!

what is it?
some kind of you pick the window manager on the fly thing?

I don't care about niftiness.. I just want this problem to go away...
I want my video to behave itself.. and 

I DONT WANT TO LOCK UP THE COMPUTER!! thats it!

I am not playing HD video games.. or doing anything beyond 
boring limits for a computer... I am just asking it to
work.. 

What does Compiz do anyway?

---

### Post by gjoellee on 2008-12-29
> **bluemax7 said:**
> 
1. If I use ALT_SYSREQ-R and then CTRL-ALT-F1 to get to the console
   how do I totally restart the window manager from the prompt so I do not have to reboot.. and get back to the desktop?


I am not sure if the command: ```
sudo reboot
``` is a valid command in Ubuntu, it is in Arch. But: ```
sudo shutdown -h now
``` will shut down your system.

---

### Post by Therion on 2008-12-29
That SIS integrated graphics chip is what's killing you.  I've seen issue with SIS graphics since... Feisty I think; definitely with Gutsy and beyond.  Not sure what to tell you other than try using the generic "VESA" driver and see where that gets you.

Since you're running Intrepid (8.10), I can't tell you how to do that though, since X is handled so differently in Intrepid than it is in Hardy (8.04), but I'm sure someone will be able to tell you how to do that.

---

### Post by .arean on 2008-12-29
> **bluemax7 said:**
> If I use ALT_SYSREQ-R and then CTRL-ALT-F1 to get to the console how do I totally restart the window manager from the prompt so I do not have to reboot.. and get back to the desktop?

Type:
```
sudo /etc/init.d/gdm stop
```
then
```
sudo /etc/init.d/gdm start
```

---

### Post by bluemax7 on 2008-12-29
Well I guess if the onboard video sucks with the Desktop..
I should get a standard video card and plug it into the AGP..
and give that a hurl...

I just didn't want to have to do that...

I was just hoping on a way to debug
whats going on...

Isn't the Sis on board Video a popular chip?
This must be happening to other people all over the place?

Where can I find a compatible driver?
and load it in?

Like where do I start? :)

Thanks for the init.d/gmd stop and start!!!!
I'll give that a try the next time it locks up...

that alone will be a great improvement!

But... PROBLEM is still unresolved.

- Brett

---

### Post by bluemax7 on 2008-12-30
Okay it looks like I have the Sis 760 On board chipset
and it has inherent problems..due to the AMD processor 
managing memory, and the Sis 760 Chipset wanting to use 
the same memory..

The website I found [http://www.winischhofer.net/sisdri.shtml](http://www.winischhofer.net/sisdri.shtml)
digging around explains that ... 

in a gist..... ~~~ thats just the way it is!!!

looks like thats what I get 
for buying a motherboard named "WINFAST!"

Is there a "LinuxFast" mother board out there? 

I guess I have to go get a Video card then..

WHAAAAA WHAAAA WHAAAAAA!!!

Thanks for the help everyone!!! 

anyone know of a good video card that just works?

- Brett

---

### Post by Rohan Kapoor on 2008-12-30
> **bluemax7 said:**
> Okay it looks like I have the Sis 760 On board chipset
and it has inherent problems..due to the AMD processor 
managing memory, and the Sis 760 Chipset wanting to use 
the same memory..

The website I found [http://www.winischhofer.net/sisdri.shtml](http://www.winischhofer.net/sisdri.shtml)
digging around explains that ... 

in a gist..... ~~~ thats just the way it is!!!

looks like thats what I get 
for buying a motherboard named "WINFAST!"

Is there a "LinuxFast" mother board out there? 

I guess I have to go get a Video card then..

WHAAAAA WHAAAA WHAAAAAA!!!

Thanks for the help everyone!!! 

anyone know of a good video card that just works?

- Brett
I don't know exactly what video card to get, but my reccomendation would be to get Nvidia because they have better Linux support than AMD/ATI.

---

### Post by bluemax7 on 2008-12-30
okay Thanks!!!
NvidiA

Well thats how you learn ehhh?

- brett

---

### Post by Rohan Kapoor on 2008-12-30
> **bluemax7 said:**
> okay Thanks!!!
NvidiA

Well thats how you learn ehhh?

- brett
Yep. Glad to help!

---

### Post by JohnE1 on 2009-11-24
> **bluemax7 said:**
> Thanks for the help:

1. If I use ALT_SYSREQ-R and then CTRL-ALT-F1 to get to the console
   how do I totally restart the window manager from the prompt so I do not have to reboot.. and get back to the desktop?

Brett

If you use CTRL-ALT-F1 thru CTRL-ALT-F6 to get to any of those 6 virtual consoles. then use ALT-F7 to get back to the Xserver "console." Xserver is always run in virtual console 7 under Linux.

---

