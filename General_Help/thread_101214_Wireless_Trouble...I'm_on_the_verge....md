---
title: "Wireless Trouble...I'm on the verge..."
date: 2005-12-09
forum: General Help
---

### Post by blue_thunder on 2005-12-09
Hi. I'm having some real trouble activating my wireless connection. I have installed the driver "bcmwl5a.inf" and when I run "sudo ndiswrapper -l" it recognizes the driver and the hardware that's present. I'm trying to follow a tutorial that got me this far, but the last steps are:

"This should enable you to see and configure your wireless card in System->Administration->Networking
You will need to go to that window to tell Linux how you connect to your router, as well as "Activate" the connection by clicking Activate after choosing "wlan0"."

In any case, when I go to Networking I only see "Ethernet Connection" and "Modem Connection" I don't see "Wireless Connection" and I don't see any "Add" button either. Also, I don't know what he means when he says "You will need to go to that window to tell Linux how you connect to your router." How exactly do I tell Linux how to connect to my router?

Thanks for any help you can give. I also apologize for being so new to Linux.

---

### Post by carlosqueso on 2005-12-09
did you "sudo modprobe ndiswrapper"?  Does it do anything?

---

### Post by Chris Tucker on 2005-12-09
depending on your system you might need to do more.. for instance on an Acer Aspire series laptop you have to do this: [http://ubuntuforums.org/showthread.php?t=60484&page=8](http://ubuntuforums.org/showthread.php?t=60484&page=8)

---

### Post by blue_thunder on 2005-12-09
Doesn't do anything visible unfortunately. One weird thing is that it says the "Ethernet Connection" is active, and it has said that since the start. I don't know if that means anything.

---

### Post by carlosqueso on 2005-12-09
Is your card lighting up?  Also, can you post the output of ```
lspci
```  That'll allow people who actually know what they're doing (read: people not like me ;)) a chance to help you.

---

### Post by blue_thunder on 2005-12-09
Chris: It's a Dell Inspiron 600m.

Carlos: The card's internal, so I don't see any lights.

The output of "lspci" is:

> 0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 01)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)


---

### Post by carlosqueso on 2005-12-09
weird....it sees your card, and knows what it is, but doesn't want to do anything with it........what does ```
iwconfig
``` give you?

---

### Post by blue_thunder on 2005-12-09
"iwconfig" puts out the following: 

```
lo       no wireless extensions
eth0     no wireless extensions
sit0     no wireless extensions
```

---

### Post by carlosqueso on 2005-12-09
grrr....I had the same problem with my old wireless card.....but found a better driver.  I'd search around on the internet for another driver.  I've had no luck so far, but if I turn up something I'll let you know

---

### Post by blue_thunder on 2005-12-09
What kind of driver do I need?

---

### Post by carlosqueso on 2005-12-09
The one you're using should work with ndiswrapper....by the way... is there a .sys file in the same folder as the .inf file?  It's a shot in the dark, as I'm not really sure what's goin on with that weirdness.  If it is, try modprobing ndiswrapper again, and then type ```
dmesg
``` and post the last few lines of output.  I'm not that much more experienced than you, but if I can't help you get this working, I can at least get the info that others may be able to use, and I know a couple more things to try...

---

### Post by blue_thunder on 2005-12-09
OK. There is a .sys file, but it's "bcmwl5.sys" whereas the .inf file is "bcmwl5a.inf". I don't know if that makes a difference. 

The last few lines of output from the "dmesg" is as follows:

```
[4297149.506000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4297149.535000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1792);  check system log for messages from 'loadndisdriver'
[4297181.146000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4297181.174000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1792);  check system log for messages from 'loadndisdriver'
[4297640.449000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4341821.860000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4341821.924000] ISOFS: changing to secondary root
[4342399.442000] eth0: no IPv6 routers present
[4346998.282000] cdrom: This disc doesn't have any tracks I recognize!
[4347025.528000] scsi: unknown opcode 0x01

```

---

### Post by carlosqueso on 2005-12-09
hmmm...doesn't look like ndiswrapper is loading properly...I'm not really sure where to go from here....

---

### Post by blue_thunder on 2005-12-09
Is there anyway around ndiswrapper?

---

### Post by carlosqueso on 2005-12-09
Hmm...it seems as if ndiswrapper isn't working properly.  This is crazy, but may somehow work.  Try typing ```
sudo ifup wlan0
``` and seeing what happens.  I don't expect it to work, but who knows?   If that doesn't work, I'd try these threads next cause you've exhausted my limited knowledge, and I have a HP with an external card.

[http://www.ubuntuforums.org/showthread.php?t=15780&highlight=BCM4309](http://www.ubuntuforums.org/showthread.php?t=15780&highlight=BCM4309)
[http://www.ubuntuforums.org/showthread.php?t=92829&highlight=BCM4309](http://www.ubuntuforums.org/showthread.php?t=92829&highlight=BCM4309)

---

### Post by blue_thunder on 2005-12-09
No luck with that command. It said "Ignoring unknown interface wlan0=wlan0". Is there anyone I can e-mail about this or anything? I am totally lost, and I'm beginning to feel like I should just reinstall Windows, as awful as it sounds. If I could, I'd partition, but I don't know how to do that either.

---

### Post by carlosqueso on 2005-12-09
[QUOTE=blue_thunder]Is there anyway around ndiswrapper?[/QUOTE]

If you have a wireless card with native linux drivers, you can use them.  Unfortunately, your built-in one doesn't have linux drivers that I can find.  Since you don't have access to native linux drivers, this may help [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/) but you should note that it is NOT free.

---

### Post by blue_thunder on 2005-12-09
I GOT IT!!!!!! SORT OF. Ok. So it finally show me the option of having a wireless connection and it shows that the belkin54g is there...all I need is a WEP Key. What is that? Where do I get it?

---

### Post by carlosqueso on 2005-12-09
[QUOTE=blue_thunder]No luck with that command. It said "Ignoring unknown interface wlan0=wlan0". [/QUOTE] I didn't really think it'd work, but it was worth a try.  [QUOTE=blue_thunder]Is there anyone I can e-mail about this or anything?[/QUOTE]You could try e-mailing the folks at Broadcom, but I'm not sure how much good it'll do.  [QUOTE=blue_thunder] I am totally lost, and I'm beginning to feel like I should just reinstall Windows, as awful as it sounds. If I could, I'd partition, but I don't know how to do that either.[/QUOTE] I'd ask in the forums.   I used Mandriva (formerly Mandrake)'s partition tool, which took care of all the hard partitioning issues, and installed Ubuntu on the partitions that Mandrake was on.   It's what I would reccomend doing, but here's a thread with a couple more options:

[http://www.ubuntuforums.org/showthread.php?p=454151#post454151](http://www.ubuntuforums.org/showthread.php?p=454151#post454151)

By the way, I'm off to lunch, and have some work stuff to do afterwards, so I may not get back to you for a couple hours if you reply, so don't take it personally.  I'll be back on later tonight...

---

### Post by carlosqueso on 2005-12-09
[QUOTE=blue_thunder]I GOT IT!!!!!! SORT OF. Ok. So it finally show me the option of having a wireless connection and it shows that the belkin54g is there...all I need is a WEP Key. What is that? Where do I get it?[/QUOTE]
Sweet! We should be in business.  If you set up WEP encryption for your wireless network, it's the key that you set.  If you didn't, then you should be able to just leave that blank.  Anyway...off to lunch.....

---

### Post by blue_thunder on 2005-12-09
Carlos. It works. I love you.

---

### Post by carlosqueso on 2005-12-09
Great! :-D Welcome to the Ubuntu community!

---

### Post by Mr. Electric Wizard on 2005-12-09
Awesome.
I had to use that same driver, and had to NdisWrapper it too...
Next thing you need to do is go to the bottom of the main Forum and find the GTKWifi forum.
That program will help you immensely with wifi.
It's a .deb, so you'll have to dpkg it.
Welcome to the boards!

---

