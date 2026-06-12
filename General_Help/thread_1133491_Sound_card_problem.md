---
title: "Sound card problem"
date: 2009-04-23
forum: General Help
---

### Post by thermobee on 2009-04-23
Ok so here is the problem im having, i guess you can say its more of an inconvenience :lolflag: Running dual boot with XP and XP recognizes and runs sound out of the external sound card that i have. Ubuntu on the other hand uses the sound card that comes with the mother board ( which i think is called on-board card). Anyway, how can i get ubuntu to switch to the external sound card, since going to the back of my pc and switching them everytime I want to hear something on the opposite OS is kidna incovenient.

Thanks for the help in advance.

---

### Post by thermobee on 2009-04-23
Please help

---

### Post by Nepherte on 2009-04-23
How about disabling your on board in bios?

---

### Post by khelben1979 on 2009-04-23
What external soundcard are you using?

---

### Post by thermobee on 2009-04-29
> **khelben1979 said:**
> What external soundcard are you using?

I am not sure how do I check?

---

### Post by thermobee on 2009-04-29
> **Nepherte said:**
> How about disabling your on board in bios?

Not sure how. If you can advice and you are sure that will fix and ubuntu will recognize the other one than ill do it right away.

---

### Post by khelben1979 on 2009-04-29
> **thermobee said:**
> I am not sure how do I check?

```
sudo lsusb
```

---

### Post by thermobee on 2009-04-30
> **khelben1979 said:**
> ```
sudo lsusb
```

Weird I dont see it. Im not sure it even recognizes it.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c309 Logitech, Inc. Internet Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by DeMus on 2009-04-30
> **thermobee said:**
> Weird I dont see it. Im not sure it even recognizes it.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c309 Logitech, Inc. Internet Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Try ```
lspci
```. It looks to me to be an extra soundcard which is not connected externally, but still in the computer.

---

### Post by thermobee on 2009-04-30
> **DeMus said:**
> Try ```
lspci
```. It looks to me to be an extra soundcard which is not connected externally, but still in the computer.

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
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
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT]
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT] (Secondary)
02:02.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
02:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:07.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)

---

### Post by thermobee on 2009-04-30
Can someone please help me understand the problem and how to solve it.

---

### Post by thermobee on 2009-04-30
bump

---

### Post by thermobee on 2009-04-30
bump

---

### Post by khelben1979 on 2009-04-30
02:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

There's your soundcard, anyway. You can try google search for linux drivers for that soundcard. Also: LinuxQuestions.org usually have discussions about these sort of things too.

---

### Post by thermobee on 2009-04-30
> **khelben1979 said:**
> 02:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

There's your soundcard, anyway. You can try google search for linux drivers for that soundcard. Also: LinuxQuestions.org usually have discussions about these sort of things too.

Thanks bro

---

### Post by khelben1979 on 2009-05-01
One more thing, the alsaconf program allows you to change what soundcard/chip that should be used by the system.

I'm not sure if Ubuntu delivers the Alsaconf program by default, but it certainly get's into your system if you would compile it up by source code, but this really should not be necessary (I've done it myself on Ubuntu Hardy and Intrepid Ibex).

Try
```
sudo apt-get install alsaconf
```
to see what happens.

If it installs correctly:
```
sudo alsaconf
```
And from there you should be able to choose C-Media Electronics Inc CM8738 as your primary sound device used by Ubuntu.

---

### Post by thermobee on 2009-05-02
> **khelben1979 said:**
> One more thing, the alsaconf program allows you to change what soundcard/chip that should be used by the system.

I'm not sure if Ubuntu delivers the Alsaconf program by default, but it certainly get's into your system if you would compile it up by source code, but this really should not be necessary (I've done it myself on Ubuntu Hardy and Intrepid Ibex).

Try
```
sudo apt-get install alsaconf
```
to see what happens.

If it installs correctly:
```
sudo alsaconf
```
And from there you should be able to choose C-Media Electronics Inc CM8738 as your primary sound device used by Ubuntu.
E: Couldn't find package alsaconf

---

### Post by khelben1979 on 2009-05-02
Then it seems it's not part of Ubuntu Jaunty. Go for the source code instead if you really want this working.

Please check out [this thread]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+script").

---

