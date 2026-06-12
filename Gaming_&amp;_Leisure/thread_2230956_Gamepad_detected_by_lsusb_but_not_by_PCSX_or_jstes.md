---
title: "Gamepad detected by lsusb but not by PCSX or jstest-gtk in Ubuntu 14.04"
date: 2014-06-22
forum: Gaming &amp; Leisure
---

### Post by Pablo_San_Martn on 2014-06-22
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"][/TD]
[/TR]
[/TABLE]
I had been using a PS3 gamepad on [PCSX]("https://apps.ubuntu.com/cat/applications/pcsxr/") for a while on Ubuntu 14.04, but realized it stopped working a feew weeks ago.

  The controller is detected by lsusb on Terminal, but it does not appear in **PCSX** or [jstest-gtk]("https://apps.ubuntu.com/cat/applications/jstest-gtk/"). My out put is:

  Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 10f1:1a43 Importek 
Bus 001 Device 007: ID 0930:0219 Toshiba Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
[B]Bus 003 Device 012: ID 054c:0268 Sony Corp. Batoh Device / PlayStation 3 Controller
[/B]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
I think this is a problem specific to trusty, since I  tried to  use the controller in a laptop with precise and it worked  correctly.

Any ideas as to how to fix this?

---

### Post by MikeCyber on 2014-06-24
udev is broken.- Probably the autor got money from M$ or alike for bugs. Maybe adding a udev rule might help (if you're lucky). Have a look at the x-plane forum linux help section.

---

### Post by Demirelle on 2014-06-24
> **Pablo_San_Martn said:**
> [TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"][/TD]
[/TR]
[/TABLE]
I had been using a PS3 gamepad on [PCSX]("http://hackerbot.net/mmo/plus/164-clash-of-clans-coc") for a while on Ubuntu 14.04, but realized it stopped working a feew weeks ago.

  The controller is detected by lsusb on Terminal, but it does not appear in **PCSX** or [jstest-gtk]("http://hackerbot.net/pc/minecraft-mc"). My out put is:

  Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 10f1:1a43 Importek 
Bus 001 Device 007: ID 0930:0219 Toshiba Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
[B]Bus 003 Device 012: ID 054c:0268 Sony Corp. Batoh Device / PlayStation 3 Controller
[/B]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
I think this is a problem specific to trusty, since I  tried to  use the controller in a laptop with precise and it worked  correctly.

Any ideas as to how to fix this?

reinstalling IsUSB? I would probably go with that. I mean if it worked before, then my best guess is that the software making is work is bugged.

---

### Post by Pablo_San_Martn on 2014-06-26
Thanks for your replies.

@MikeCyber: Could you please post the link to that thread, as I somehow can't find it? 

@Demirelle: Just tried doing that but it didn't work. Anyway other USB devices (mouse, phone, etc.) have been working fine all the time.

---

### Post by MikeCyber on 2014-06-26
[http://forums.x-plane.org/index.php?showtopic=71300](http://forums.x-plane.org/index.php?showtopic=71300)

I'd start to look through from the last postings. Maybe setting acl or a udev rule helps. Don't forget to file a bug report.

---

### Post by Pablo_San_Martn on 2014-06-28
Thanks again, MikeCyber.

I tried following this tutorial: [http://forums.x-plane.org/index.php?showtopic=72733](http://forums.x-plane.org/index.php?showtopic=72733), but it was too difficult for me and the command "udevadm info --attribute-walk" did not produce any output on my device. I also tried copying the suggested rule for pedals with my device's name but that did not work for me.

I will file a bug report now. Have you already filed one I can say I am also affected by it?

---

### Post by Pablo_San_Martn on 2014-06-28
Just added a comment to this report: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1176565](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1176565)

---

### Post by Pablo_San_Martn on 2014-10-04
This problem has been solved in the latest update for **udev** in trusty, so just run the **Software Updater** or open a **Terminal** and enter
  sudo apt-get update 
sudo apt-get upgrade

---

