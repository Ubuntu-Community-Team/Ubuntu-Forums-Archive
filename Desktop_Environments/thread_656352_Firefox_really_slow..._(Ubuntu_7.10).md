---
title: "Firefox really slow... (Ubuntu 7.10)"
date: 2008-01-02
forum: Desktop Environments
---

### Post by Borbus on 2008-01-02
I'm using Ubuntu 7.10 x86_64 on a core 2 duo with 2GB of RAM. I'm using compiz-fusion.

When I say Firefox is slow I don't mean slow to resolve URLs or slow to download web pages. It is just very unresponsive. For example, opening a new tab, the screen will go blank, then the tab bar will appear, there is a very noticeable delay with this. Closing a tab is the same, page changes, then a significant time later the tab bar updates. Also the title bar changes very slowly while browsing and switching tabs.

I have tried several things to try and speed it up, one is turning off compiz-fusion. I have come to the conclusion that the Ubuntu Firefox is slow, and using compiz makes it even slower (I assume compiz is not updating the GUI quick enough, for example the title bar).

Swiftweasel without compiz is fast, swftweasel with compiz is quite slow, Firefox without compiz is slower, Firefox with compiz is even slower.

Note that I am comparing the speed of Firefox to running on Windows mainly because that is what I have used most. However, I have never noticed Firefox being any slower than Windows on other Linux distributions.

So, anyone know what the problem could be? I'm pretty sure I haven't created this problem, it is like it by default in Ubuntu 7.10. It's quite important that the main browser performs well I think.

edit: I forgot to say that I have already tried wiping my Firefox profile, this made it very slightly more responsive but that is expected because my profile includes quite a few plugins.

---

### Post by p_quarles on 2008-01-02
The default settings in Ubuntu's Firefox are kinda . . . bad. Here's a guide to speeding it up a bit (also works with Swiftweasel):
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

But you're correct: it is a Compiz problem. On some machines, Compiz will slow down or freeze Firefox occasionally.

---

### Post by Borbus on 2008-01-02
Well those setting helped a bit but it is still generally slow. Javascript animations on pages are painfully slow and things that Firefox is always slow at (ie. scrolling on a page which uses fixed positioning, example: [http://www.w3.org/TR/xhtml1/](http://www.w3.org/TR/xhtml1/)) is really slow...

---

### Post by lamnk on 2008-01-15
I'm feeling sorry to say this, but FF on linux sucks. It's sooo unresponsive. I tried swiftweasel too, but it only improves a bit. Hope FF3 would have better integration with linux and more optimized.

---

### Post by shae on 2008-01-16
> **lamnk said:**
> I'm feeling sorry to say this, but FF on linux sucks. It's sooo unresponsive. I tried swiftweasel too, but it only improves a bit. Hope FF3 would have better integration with linux and more optimized.

I must disagree.  It is not perfect, but with the exception of starting slightly slower than on windows and not working swell with desktop effects, firefox works just like it does in windows for me.  Are you sure you are not having some other problem?

---

### Post by LeDechaine on 2008-01-18
Hmm, firefox is better in linux (Ubuntu 7.10) than in windows (XP) for me. I had 48 tabs (forum) open yesterday, and firefox didn't even "freezed" (black and white). And i could easily look at all the pages, with little or no lag. And i'm on a P3 866 with 320 megs of ram.

Firefox + Compiz = Mess, but Firefox in linux, without compiz, is perfect or near perfect. :)

---

### Post by motin on 2008-02-04
Try disabling flash "softly" by installing the [FlashBlock]("http://addons.mozilla.org/firefox/addon/433") extension - Flash is probably the reason your firefox is so slow.

---

### Post by nymlord on 2008-02-10
Flashblock did actually improve it, but im still disapointed, because its not lag during loading pages, its just stupid lag, like switching from tab to tab take 2-3 sec :S

---

### Post by benerivo on 2008-02-10
Have you tried the Firefox 3 (beta 3) from the repositories? It is stable and is faster then 2.x.

---

### Post by brikenobi7r on 2008-02-10
Use Opera, downloadable at opera.com unfortunatly you may have to use internet to get there though. Also here is a awesome black theme for opera - lix1_5

---

### Post by andrewabc on 2008-02-12
I remember other threads saying to disable IPv6 in about:config and you should see an improvement in speed.
Google it.

---

### Post by y-lee on 2008-02-12
See [How to speed up Firefox]("http://ubuntuforums.org/showthread.php?t=179540"), these tweaks made a big difference for me.

Also I switched to [swiftweasel]("http://swiftweasel.tuxfamily.org/") which is an [optimized for speed build of firefox]("http://en.wikipedia.org/wiki/Swiftweasel"). If firefox is installed swiftweasel imports your firefox profile including the about:config, add ons and plugins. The tweaks above also apply to swiftweasel.

---

### Post by johnsmithepoch on 2008-02-20
Dell Dimension E521
Athlon 64 x2 4400+
GeForce 7100 GS @ 1920x1200
2GB RAM
Gutsy

At last I find someone who is experiencing the same problem I am. If I open a tab in Firefox or Opera, there is a noticeable lag where it draws the window. This happens whether I use gnome with all the eye-candy or basebones fluxbox. In general, 2D performance seems lackluster, but it's most obvious in browsers for some reason. One other place I consistently notice it is the ubuntu gdm (login screen) where I can actually see the screen being painted. Switching to 16-bit mode in my xorg.conf gives a only marginal speed boost.

If I understand correctly, none of the comments thus far (e.g. ipv6, firefox 2 being crappy) explain what is going on, at least not in my case because the exact same thing happens to me in both Firefox 2.0.0.12 and Opera 9.24 on Gutsy. On the exact same machine under windows (still at 1920x1200) both Firefox and Opera open new tabs instantaneously and in all other respects behave exactly as expected. In general, windows seems a lot peppier ("snappy") in terms of 2D graphics performance.

I've spent a lot of time researching this and haven't gleaned much, but at this point it is my strong suspicion that it is related to the 2D graphics performance which is a function of your video card/driver.

Do you have an nVidia card by any chance? I have a 7100 GS and even after updating to the beta drivers (169.04) the problem persists. Some tools you might like to play with if you suspect 2D performance is suffering:

x11perf, gtkperf, [http://launchpadlibrarian.net/1585880/test.html](http://launchpadlibrarian.net/1585880/test.html)

When I run these tests, I don't see anything immediately obvious that tells me what's lacking about my setup. However, they do give a good sense of the relative performance of your own machine in different configurations (e.g. I got a slight speedup after updating to the beta video driver).

AFAICT, nVidia cards just aren't as well supported under linux as ATI cards are. I don't have much to back this up, it's just based on an unrelated collection of observations, e.g. that the nVidia driver is closed-source and the fact that ATI cards, but not nVidia cards, have optimized AcceleratedX drivers available.

I'm going to test an ATI card in my machine ASAP and see if that makes a difference. If the problem persists, I'm going to be seriously disappointed because it means I'll be totally out of options.

---

### Post by fmc6338 on 2008-02-22
firefox slowandunresponsive.   did not seem to have the problem with ubuntu 6.06

---

### Post by johnsmithepoch on 2008-02-22
This evening my friend brought his computer over and I got the chance to try his ATI x1950 Pro in my machine (for specs see my post above). Unfortunately, I had some driver issues and there wasn't enough time to resolve the problem. Instead, I tried my GeForce 7100 GS in his machine, the specs of which are:

Gigabyte mainboard w/ Intel chipset (sorry, I didn't note the exact model).
E6600 FSB @ 356 MHz
2GB RAM @ 1066 MHz
Gutsy

Using my card in his machine, the problem totally went away. His x1950 in his machine worked fine too. So I have to nix my theory that it was the graphics card/driver. Maybe poor support for my NForce 430 chipset. Hmm...

---

### Post by johnsmithepoch on 2008-02-24
Got my hands on another machine to test:

Dell Dimension 8300
Dual core Intel P4 @ 3Ghz
1 GB DDR SDRAM @ 400MHz
GeForce FX 5200 (onboard)
Intel 875P chipset

Installed Gutsy on this machine and the problems with Opera/Firefox were nonexistent, regardless of whether I used the "nv" or "nvidia" driver. So, this strengthens my suspicion that the problem is either due to Ubuntu's poor support for the nVidia southbridge or the AMD northbridge.

lspci from Dell 8300 (Intel 875P chipset):

```

00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```

pspci from problematic Dell E521 (nForce 430 chipset):

```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem

```

One final test I conducted was to remove the 7100 GS from the Dell E521 and just use its onboard GeForce 6150, but the results were the same, i.e. Opera and Firefox still slow.

Looking at:

[http://en.wikipedia.org/wiki/Image:Motherboard_diagram.png](http://en.wikipedia.org/wiki/Image:Motherboard_diagram.png)

I find it interesting that the 7100 GS connects via the northbridge (by virtue of being PCI-E) whereas the onboard 6150 connects via the southbridge (by virtue of being onboard). Unless there's such a thing as onboard PCI-E...but assuming there isn't, this seems to say that the problem isn't even limited to just the northbridge or southbridge. I suppose since access to the southbrige also passes through the northbridge it might just indicate that the northbridge is the problem...

Sorry for all the speculation; I don't know much about this subject. Surely somebody out there well versed in such things could shed some light on this...?

---

### Post by johnsmithepoch on 2008-02-24
Forgot to mention this in my last post:

[http://www.nvnews.net/vbulletin/showthread.php?t=108214](http://www.nvnews.net/vbulletin/showthread.php?t=108214)

This may provide some insight into the problem. It appears that readback may be a critical part of the problem I'm experiencing.

Sadly, I still don't have any idea how to fix the problem. I think the answer is that I can't. So, pending further information, my the next time I buy a machine, it will have an Intel CPU and chipset (with nVidia video card since it didn't turn out to be the problem).

---

### Post by ellalan on 2008-03-01
Hi p_quarles
Thanks for the link, it sped up my sluggish FF.

---

