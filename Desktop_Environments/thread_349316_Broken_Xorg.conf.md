---
title: "Broken Xorg.conf"
date: 2007-01-30
forum: Desktop Environments
---

### Post by linuxpimp on 2007-01-30
Hi 

I installed Beryl and ran it, WOW!

But, i cannot see or eneter any text into a terminal-gnome-terminal or xterm,

WHat is missing from my xorg.conf?

I am now logged in to a gnome-session using compiz, but compiz is fubared so i have no window borders or buttons. I cannot type in a terminal to start beryl so i'm stuck.

Thoughts?

lp

---

### Post by linuxpimp on 2007-01-30
Ok, i figured out that the windows were simply too high.so i "enter" 'd until i saw command line and ran beryl manager, however i still cannot move windows or see the decorations/buttons...


lp

---

### Post by nkkromhof on 2007-01-30
If you right-click the Beryl icon in the system tray, can you hit "Reload Window Decorator"?

Oh and make sure that Emerald is selected there...

Also I would suggest running beryl-manager through ALT-F2, because this way if you close the terminal you'll lose beryl-manager again...

---

### Post by pmshirey on 2007-01-30
Yay you broke Xorg.conf For me i would be happy, then re-install linux again

---

### Post by linuxpimp on 2007-01-30
> **nkkromhof said:**
> If you right-click the Beryl icon in the system tray, can you hit "Reload Window Decorator"?

Oh and make sure that Emerald is selected there...

Also I would suggest running beryl-manager through ALT-F2, because this way if you close the terminal you'll lose beryl-manager again...

Hi, no icon there :-(

lp

---

### Post by highneko on 2007-01-30
Attach your xorg.conf? Give us some details about your graphics card and computer?

Paste the output into a code tag:
cat /etc/X11/xorg.conf
lspci

---

### Post by linuxpimp on 2007-01-30
> **highneko said:**
> Attach your xorg.conf? Give us some details about your graphics card and computer?

Paste the output into a code tag:
cat /etc/X11/xorg.conf
lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0163 (rev a1)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)


```

I can't get the xorg.conf as i can't resize my terminal window or right click :-(, but it's stock standard save for the nvidia driver and the following:
  
      In Device section
Option "XAANoOffscreenPixmaps" "true"

and at the very end:
Section "Extensions"
Option "Composite" "true"
EndSection


Thanks

lp

---

### Post by Waappu on 2007-01-30
> **linuxpimp said:**
> WHat is missing from my xorg.conf?
Could you post xorg.conf file and guide you followed to install beryl?

> **linuxpimp said:**
> I am now logged in to a gnome-session using compiz
Maybe I misunderstand but I think it's not good idea to try run beryl and compiz same time.
If you login to gnome session and not start compiz do you still have problem with beryl?
Should you uninstall compiz ?

---

### Post by linuxpimp on 2007-01-30
> **Waappu said:**
> Could you post xorg.conf file and guide you followed to install beryl?


Maybe I misunderstand but I think it's not good idea to try run beryl and compiz same time.
If you login to gnome session and not start compiz do you still have problem with beryl?
Should you uninstall compiz ?

Yup, compiz was before beryl, once i had that fixed i installed beryl according to:
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

Thanks

lp

---

### Post by Waappu on 2007-01-30
> **linuxpimp said:**
> 
I can't get the xorg.conf as i can't resize my terminal window or right click :-(, but it's stock standard save for the nvidia driver and the following:
  
      In Device section
Option "XAANoOffscreenPixmaps" "true"

and at the very end:
Section "Extensions"
Option "Composite" "true"
EndSection
If you can some how post your xorg.conf file it might help.
I don't have Nvidia card and thats why maybe can't help much. =(
But I think guide you post not say anything about those xorg.conf setups for Nvidia

---

