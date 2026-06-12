---
title: "Brightness issue with HP Pavillion Laptop"
date: 2020-02-24
forum: Desktop Environments
---

### Post by dbee on 2020-02-24
So i'm having a brightness issue with ubuntu 19.10 on a hp pavillion laptop. I want to get the laptop brighter.

I can't seem to find any brightness slider. It's not in the dropdown in the bar on the top-right corner. 

I've adjusted grub with GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" and updated grub/rebooted to get ubuntu to use the vendor drivers instead of default but no luck.

I also found a solution on the internet using xrandr and the terminal but it's for ubuntu 18.x and xrandr is installed by default.

Anyone have any ideas ?

---

### Post by thehipho on 2020-02-25
You can try this link to Enable automatic brightness: 
[https://help.ubuntu.com/stable/ubuntu-help/power-autobrightness.html.en](https://help.ubuntu.com/stable/ubuntu-help/power-autobrightness.html.en)

---

### Post by dbee on 2020-02-26
I see 'blank screen', 'wifi' and 'bluetooth' in the Power Saving section of the power application.

I don't see any automatic brightness ...

The brightness on windows on the same computer (dual-boot) is fine :-( 

I'm beginning to think that i can't adjust my brightness on this computer

Is there any package in the repo that contains xrandr ? so i can install and try adjusting from the command line ...

---

### Post by thehipho on 2020-02-26
Screenlets had brightness widget prior to 19.04, and so did cairo-dock!
```
sudo apt-get install screenlets-pack-all
sudo apt install cairo-dock-core

```

You could try installing Brightness Controller from here: [https://github.com/lordamit/Brightness](https://github.com/lordamit/Brightness)

---

### Post by dbee on 2020-02-29
brightness controller opened once then crashes. 

This is what i get from dmesg | tail maybe i'm looking at the wrong logs ?

```

[31143.333000] IPMI message handler: version 39.2
[31143.333799] ipmi device interface
[31143.488524] Lockdown: modprobe: Loading of module with unavailable key is restricted; see man kernel_lockdown.7

```

```

dara@dara-HP-Pavilion-Notebook-15-bc5xxx:~$ sudo apt-get install screenlets-pack-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package screenlets-pack-all

```

---

### Post by dbee on 2020-03-01
nvm. it got fixed. I'm not sure how though. 

The brightness controller might have worked afterall ...

I can see a brightness slider in my settings menu and it's alterable ...

Thanks,

---

