---
title: "cpu usage too high regardless of desktop"
date: 2013-02-08
forum: Desktop Environments
---

### Post by mshallop on 2013-02-08
Hi -

Just installed 12.10 on a new server and I'm seeing incredible cpu usage by compiz - 260 - 350% cpu use keeping my load between 2.5 and 3.0...

I tried the various tweeks suggested elsewhere in the forum to reduce the cpu use but no luck - I've also tried the gnome desktop and I see the same issue with the gdm process.

I'm using this server as my dev platform and have several services running (RabbitMQ, mongo, mysql, memcached, etc.) and the impact of managing the desktop become evident after a few work-space switches and I have to wait for things to settle down before I can do things like move and click the mouse.

My laptop uses the same set-up flawlessly - with no appreciable cpu load - so I know it's something in the video stack - I just don't know where to look or, other than the obvious tweeks I mentioned earlier, where to go next.

Here's some sysinfo output:

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde PRO [Radeon HD 7700 Series] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 0427
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f7e00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at e000 [size=256]
    Expansion ROM at f7e40000 [disabled] [size=128K]
    Capabilities: [48] Vendor Specific Information: Len=08 <?>
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Capabilities: [270] #19
    Kernel driver in use: radeon
    Kernel modules: radeon


sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Cape Verde PRO [Radeon HD 7700 Series]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:46 memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:f7e40000-f7e5ffff

```Thanks - and apologies in advance if I've derped over something painfully obvious...

--mike

---

### Post by mörgæs on 2013-02-11
Hi, welcome to the fora.

You are using the open-source Radeon driver. Have you checked if closed-source drivers are available? 

If nothing else works you could consider a lighter desktop environment like XFCE.

---

### Post by mshallop on 2013-02-11
I tried the proprietary drivers and things got a lot uglier.  I tried both the fglrx and fglrx-updates.  I also tried the new(er) drivers direct from ATI/AMD using the catalyst 13.1 package installer configured for generic X and for the detected ubunto release.

The fglrx drivers both yielded the same results - the default login environments gave me the desktop but no window manager, unity, etc.

flgrxinfo:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

Didn't matter if I was gnome or default ubuntu desktop.

Will try the XFCE but I suspect it's something deeper in the stack that's dinging whatever WM I'm using...

Currently, my load is at about 4.4 and compiz is eating over 300% of the cpu...

---

### Post by mshallop on 2013-02-19
I tried the following desktops with these results:

Gnome: same CPU hit as Unity.  (unacceptable)
KDE: consistently hovered around 6-10% CPU usage.  (better)
E17: Similar to gnome
XFCE: 0-4%, hovers around 1%
LXDE: similar to XFCE

I also tried desktops: Fluxbox, OpenBox, Razor-qt, and Mate.  I didn't bother recording CPU usage for these desktops mainly because I personally didn't care for them.

I ended up with LXDE over XFCE simply because LXDE seems to be more configurable -- for example, I can't get my dual-monitor display configured correctly under XFCE so I quickly abandonded it in favor of LXDE.

Overall, I'm pretty disappointed in the resources for figuring out this issue with 12.10 and Unity on this server.  I miss the default Ubuntu desktop (which runs great on my aging I5 laptop!) but just can't tolerate it gobbling up 50% of my 8-cores all the time -- makes benchmarking my web-services software really, really hard...

so, if you're having similar issue with the performance of Unity desktop under 12.10, consider switching over to LXDE -- you'll reclaim your cpu. Hope this helps someone else...

---

### Post by mörgæs on 2013-02-19
Thanks for posting. Please mark the thread 'solved'.

You shouldn't be disappointed with Ubuntu. but with AMD and their support policy.

There might be a better solution for your card, but I can't give more advice. I don't have much experience with Radeon in general. Should be plenty of threads dealing with this card.

---

