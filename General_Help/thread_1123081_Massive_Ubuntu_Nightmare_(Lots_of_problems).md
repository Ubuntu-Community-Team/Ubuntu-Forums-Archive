---
title: "Massive Ubuntu Nightmare (Lots of problems)"
date: 2009-04-11
forum: General Help
---

### Post by Mike_IronFist on 2009-04-11
My Ubuntu problems have only inflated over time and it's become a horrible nightmare for me. I need HELP. Lots of it. I don't know why Ubuntu is so cruel to me, but right now it's becoming a very easy-to-hate operating system.

1. VERY Random Crashes
"Ubuntu is built on the Debian kernel, known for its legendary stability." Well, it SHOULD be stable. Instead my entire desktop has locked up SEVERAL TIMES, including: when installing new GDM themes, when Firefox shows the "do you want to save this session" dialogue (because tabs are open), and when trying to open a text file while I have an partially-incompatible theme installed. Everything locks up and I can only hope that I can drop to command line so I can restart the display manager or just reboot.

2. Blank windows opening up when trying to open text files (the dialog that normally prompts the user as to whether or not they want to display a text file or run it as a shell script) when I have a semi-incompatible theme installed. Also blank windows when running the Simple Backup gui, regardless of theme, in addition to other small dialogues that appear blank regardless of what theme I am using. 

3. No sound in a ton of my games (downloaded using "Add/Remove" app). No music in Freedoom, or in any games with Midi sound for that matter.

4. After trying out the Ndis Wrapper gui (Windows Wireless Drivers) Ubuntu no longer detects my wireless card that is BUILT IN to my laptop. I can't get online now unless I'm in Windows because my Ubuntu installation thinks I don't have a wireless card.

This is my FIFTH fresh install of Ubuntu, and the only time I've had this LAUNDRY LIST of problems, though some persisted on other installs.

As a side note, I always install the Ubuntu Studio audio, video, and graphics program packages, which includes a LOT of stuff. But I don't know if installing a massive amount of programs has anything to do with it.

Should I just get the Ubuntu Studio Installation DVD instead?

Please help me.

---

### Post by albinootje on 2009-04-11
Is this Hardy, Intrepid or Jaunty ?

And can you post the output of this command in a terminal :
```

lspci

```

Did this computer run without *any* problems with some other OS before ?
In case there were problems, did you run a memtest86 and did you check possible CPU cooling problems ?

---

### Post by Mike_IronFist on 2009-04-11
> **albinootje said:**
> Is this Hardy, Intrepid or Jaunty ?

And can you post the output of this command in a terminal :
```

lspci

```

Did this computer run without *any* problems with some other OS before ?
In case there were problems, did you run a memtest86 and did you check possible CPU cooling problems ?
It's Intrepid.
I said before that I've used Ubuntu before without these problems and this is only recently. I'll report  back with that lspci output though as soon as I can.

---

### Post by lovinglinux on 2009-04-11
I would like to ask you not to post such large images in the forums.It is kind of annoying, because it mess with the page size. I'm not sure, but I think it is also against the forum rules.

You could use a service like [ImageShack](http://imageshack.us/), which has nice little thumbnails for forum posts like the one below, which you can click to view the big image:

[[IMG]http://img22.imageshack.us/img22/5338/screenshotfoxmediacentes.th.png[/IMG]](http://img22.imageshack.us/img22/5338/screenshotfoxmediacentes.png)

---

### Post by cariboo on 2009-04-11
Except for the wireless problem, it looks like most of your problem is due to the graphics driver. What video chipset does your laptop have?

Jim

---

### Post by Mike_IronFist on 2009-04-17
Sorry about the large image, I was half-asleep with the first post. I'm usually a lot more concious about something so stupid.

> **cariboo907 said:**
> Except for the wireless problem, it looks like most of your problem is due to the graphics driver. What video chipset does your laptop have?

Jim

Well, I switched to the Jaunty RC (doing a fresh install). Now the only thing that causes any freezes is when I try to edit my Cairo-Dock.

If it's any clue, the lockups are PURELY graphical. Most of the time I can move the mouse, and once it locked up when I was burning a disc. However when my disc drive stopped moments later, I found my disc successfully burned. From this I assume the system is still functioning, despite the gui freezing up entirely.

Here's the output from the lspci command.

```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200M G (rev a2)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

---

