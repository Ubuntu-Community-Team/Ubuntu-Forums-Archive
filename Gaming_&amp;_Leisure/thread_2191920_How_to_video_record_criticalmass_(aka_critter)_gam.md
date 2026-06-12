---
title: "How to video record criticalmass (aka critter) game?"
date: 2013-12-05
forum: Gaming &amp; Leisure
---

### Post by goodbye-windows(tm) on 2013-12-05
Hi all,

I like to play criticalmass (aka critter).....it's awesome, but cannot record the game play using video capture tools such as 'recordmydesktop'. 

When I try to record a game session, I get the wrong screen size when viewing the video, and/or very choppy video display of the game while the recording is being made.

I am running Xubuntu 13.10 and have a 6 core processor, using the stock on board video driver hardware.

The game plays fine when played, but goes to HELL as soon as the video recording is started.

Is it possible to buy a video card and use it instead of the built in motherboard video hardware? Or, is it possible to dedicate one of my processors to exclusively capture video?

Would appreciate any info.

TIA

Art

PS:where do those who enjoy playing criticalmass gather...mailing list, forum etc

---

### Post by dannyboy79 on 2013-12-05
what graphics card is built into your CPU? if it's an AMD, are you using the amd proprietary drivers? i have only a quad core machine and I can play games AND record 1280x720 just fine BUT then again i do have an HD7770 Black Edition so that's definitely helps. There's an awesome app called simplescreenrecorder, i use that exclusively for doing screencasting (recording your desktop) OR live streaming to twitch.tv. first you should make sure you're using the best driver you can for your graphics card, then we'll start looking at recording your game. so which graphics card do you have? issue this command and report back the output
```
sudo lshw -C display
```

---

### Post by goodbye-windows(tm) on 2013-12-07
Hi Danny, thanks for replying.

Here's the info on the video.

```
artie@xub13point04-System-Product-Name:~$ sudo lshw -C display
[sudo] password for artie: 
  *-display               
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:febe0000-febeffff memory:fea00000-feafffff
artie@xub13point04-System-Product-Name:~$ 

```

It's the stock video supplied with my ASUS motherboard.

Thanks,

Art

---

