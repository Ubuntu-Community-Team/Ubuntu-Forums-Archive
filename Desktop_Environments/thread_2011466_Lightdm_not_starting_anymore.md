---
title: "Lightdm not starting anymore"
date: 2012-06-27
forum: Desktop Environments
---

### Post by nevixa on 2012-06-27
Hi,

I'm on ubuntu 12.04 and I have a problem with the gui/unity/lightdm not showing up anymore.

On purposely I changed the grub setting from 'quiet splash' to 'text' to boot in Ubuntu console/terminal only, without any GUI. Normally I would run 'sudo lightdm start' to get into the Ubuntu GUI.

Strangely enough xterm wouldn't start when no monitor was connected. So I wanted to make the system headless by changing the xorg.conf to enable Remote Desktop when running xterm with a graphical program, without any actual monitor.  

After that I was not able to get the GUI and also xterm wouldn't start even when a monitor is connected. I tried installing nvidia drivers again, I restored the xorg.conf and I restored grub to quiet splash, I tried reconfigure and reinstalling lightdm, but non of them would work. 

How to get in the Ubuntu GUI again? 

Thank you

---

### Post by nevixa on 2012-06-27
I was able to finally get the GUI back by doing this:
[COLOR=red][COLOR=black]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

Now, how can I get the headless computer to boot xterm without an actual monitor? 

I tried changing my xorg.conf to:
[/COLOR][/COLOR]```
Section "Device"         Identifier      "Onboard Intel Graphics"         Driver          "vesa" EndSection  Section "Monitor"         Identifier      "Generic Monitor"         HorizSync       31-101         VertRefresh     60-160 EndSection  Section "Screen"         Identifier      "Basic Screen"         Monitor         "Generic Monitor"         Device          "Onboard Intel Graphics"         SubSection "Display"             Modes		"1024x768"         EndSubSection EndSection
```

Changing the xorg.conf made failed startx with the error: no screens

Any ideas how to make Ubuntu 12.04 headless and make startx/xterm work?
[COLOR=red][COLOR=black] Thank you
[/COLOR][/COLOR]

---

