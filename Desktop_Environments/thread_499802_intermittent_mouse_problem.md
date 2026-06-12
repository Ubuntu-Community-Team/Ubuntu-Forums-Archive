---
title: "intermittent mouse problem"
date: 2007-07-13
forum: Desktop Environments
---

### Post by gozzerd on 2007-07-13
I can't find other posts that describe this problem. 

My mouse is a wireless USB, Logitech mx 1000. It works fine most of the time. But if I download something large, like a 100 or 200 mb file, or a distro iso or something, part way through the mouse will stop operating smoothly. It will still function, but it is as if its signal is such a low priority now that it is only being sampled 1/1000 as often. I have to gently, slowly nudge it to a shutdown function and reboot.  It only happens when I leave it idle for awhile during the download. It also did it just a little while ago at the log-in screen. I left it there for several (10?) minutes while doing some chores, and when I came back and logged in, the  desktop started up, but the mouse was slow as molasses. No firefox had been started. No download.  But, I can leave the desktop idle forever, leave office app windows open, or nautilus, and the mouse is fine. I have checked system monitor, and there is little to no load when the mouse is slow, plenty of cpu cycles available. No signs of memory leakage. Swap is almost always empty. I'm running ubuntu 6.10 on an old dual p3 1ghz machine, via chipset, 1 gig ram, kernel is 2.6.17-10-generic. (I used envy to install nvidia driver and didn't want to redo it for 17-11.) This has been happening for a long time (months) and seems to be a system thing. I don't believe it happened with my previous mouse, a standard ps/2 wheel mouse. I believe it has only been happening since I got the wireless usb mouse a year ago Christmas. 

Is this a bug?

Geoff

---

### Post by rillip on 2007-07-13
I use a wireless logitech as well (not sure of the model right off) and have no issues.  I doubt it's a bug, though you could check the bug reports.

I think most likely it's the interaction of something with the mouse we aren't understanding.  It mostly happens when you're downloading something, so could it be an IRQ conflict or the like between the ethernet card and mouse?  Have you tried the mouse on another computer to ensure it's not just the mouse that's borked, at a physical level?  

You could try and install the mouse drivers for Windows using NDSI wrapper.

You could also try checking /var/log/dmesg for any errors regarding it.

You might also try using the mouse's/base's resynch button, see if that helps.  Sorry I don't have any specific advice, these are just some ideas to get you started.

---

### Post by gozzerd on 2007-08-05
It's definitely irq related. I tried to run mint from a live cd and it happened every time shortly  after reaching the desktop. Dropping to a virtual terminal the system message was always there: disabling irq 11. 

then tonight I ran vnc in terminal server client, and shortly after logging in to the other desktop, the mouse suddenly slowed down again. I dropped to the terminal on F2, logged in as root and did dmesg tail, and there was the "disabling irq 11 message again, and then a bunch of complaints from the usb system. I forget the exact message. But it seems clear the usb system handling my mouse is getting goofed up by irq 11 being turned off. Which makes sense, because cat /proc/interrupts shows uhci_hcd:usb1 and 2, so if the usb interrupt is disabled, I am suprised there is any mouse activity at all. So some sort of network traffic is causing a bunch of noise on interrupt 11 and making  it get turned off. My system is a dual p3 1ghz running the current feisty generic kernel, which detects the dual processors and runs in smp mode.  I really don't want to do the irqpoll option that I just read about on the xen boards. Seems like there should be a better fix. My chipset is via Apollo. Kinda old, I know.  Any ideas?

Geoff

---

### Post by lafa on 2007-08-05
tried to change batteries ? if the battery is low the mouse will act laggy at times becouse of bad connection.

### Sorry diden't read your post properly, but i doubt batteries is the problem but dosen't harm to try.

---

### Post by gozzerd on 2007-08-06
It has a recharge cradle and is topped up full almost all the time, so it's not the battery.  No this is some weirdness involving some module related to the smp kernel and network activity. Some form of network activity is creating a lot of spurious interrupt requests on interrupt 11, which is what my usb system is supposed to be using.  I have tun/tap installed for qemu, and the virtual box kernel module. Maybe it's one of them.

Heres the (I hope) pertinent dmesg stuff.

[ 1864.784984] irq 11: nobody cared (try booting with the "irqpoll" option)
[ 1864.785033]  [<c01543a4>] __report_bad_irq+0x24/0x80
[ 1864.785056]  [<c0102236>] __switch_to+0xc6/0x1f0
[ 1864.785069]  [<c015465e>] note_interrupt+0x25e/0x290
[ 1864.785087]  [<f8903f32>] usb_hcd_irq+0x22/0x60 [usbcore]
[ 1864.785164]  [<c01538d0>] handle_IRQ_event+0x30/0x60
[ 1864.785180]  [<c0154f91>] handle_fasteoi_irq+0xc1/0xf0
[ 1864.785196]  [<c0105b70>] do_IRQ+0x40/0x80
[ 1864.785216]  [<c0104233>] common_interrupt+0x23/0x30
[ 1864.785225]  [<c0101e00>] default_idle+0x0/0x60
[ 1864.785248]  [<c011c092>] native_safe_halt+0x2/0x10
[ 1864.785267]  [<c0101e3d>] default_idle+0x3d/0x60
[ 1864.785274]  [<c0101409>] cpu_idle+0x49/0xd0
[ 1864.785286]  [<c03d97f5>] start_kernel+0x365/0x420
[ 1864.785305]  [<c03d9230>] unknown_bootoption+0x0/0x260
[ 1864.785332]  =======================
[ 1864.785335] handlers:
[ 1864.785339] [<f8903f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[ 1864.785367] [<f8903f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[ 1864.785394] Disabling IRQ #11
[ 1868.280211] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd hald-addon-usb- rqt 192 rq 9 len 8 ret -110


The last line keeps repeating until I reboot.

I'm not really a newbie anymore, but that doesn't keep me from being pretty clueless. Any ideas?

---

### Post by rillip on 2007-08-06
Mmm, I believe in most bios there's a setting to use a different IRQ.  Might try that.  I know there's also a file that allows you to edit IRQs, but I don't recall what it is right off hand.  I would try changing from the bios first then try researching changing the IRQ, which I haven't done.

You could also try booting with acpi=noirq, but that will either make it work perfectly or break it completely, not sure which.

---

