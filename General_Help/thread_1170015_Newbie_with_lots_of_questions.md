---
title: "Newbie with lots of questions"
date: 2009-05-25
forum: General Help
---

### Post by legopilot on 2009-05-25
Hi everyone:     After years of peer pressure to install linux I did. Ubuntu 9.02 is now an impressive linux distro, with ALL the tools necessary to live online along with windows.     Beyond all the praise I have problems I still have not figured out or can't find the answers to. Can anyone shed light on these?  --------------------------------------------------------------    - Nvidia X server       Will not save to X configuration file without invoking sudo--   Default crt-* output swaps out when going from default nvidia driver to 180.44 driver.   image sharpening option will not save for Nvidia card (Gforce 6800GT AGP)         image sharpening setting will not engage until Nvidia X server menu is brought up with the corresponding CRT-* selection window.    - Alsa sound system refuses to play out system sound effects ----      system using       Via onboard sound (deactivated in bios)      C-media CMI8738 PCI card       Audigy 2 ZS PCI card     Only way to enable this feature was a complicated installation of pulse audio (apparently used in previous versions)   Even with this fix, youtube audio was still broken.      That was until installing  flashplugin-nonfree-extrasound and     uninstalling flashplugin-nongree    - No tool to remove application icons from dropdown menus      (example is two google earth icons)     where is SMEG?   - Wireless WPA 1 password is not saving reliably.    often have to type in while checking off see password.    It is still a hit and miss.   - Can not get bluetooth headset to work with teamspeak for     example.     Goal is to use the bluetooth excusively with audio     conferencing (sound playback and sound capture).        Where is the ALSA interpretation for the plantronics       headset? (It does interrogate and connect though)   - vncviewer is not installing by default or can not be invoked in terminal.       Modification of installed items in synaptic package manager      was required.    - Can not read extended Fat 32 partitions.     Example is a logical drive in the 230 gig range.     letter e in windows.     - shutdown is often giving failure messages although successfull.    - hibernation is crashing upon rebooting from the event.    - VNC viewer does not allow desktop switching if running fullscreen. keybard commands anyone?    - Ok Finally, I tried to modify grub to make my default Boot os Windows recently. I had not luck changing the number as depicted in   "http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/" target="_blank">[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)    Ok that is all my wining, I would appreciate any response in advance and Thank you:    Maurice

---

### Post by michy99 on 2009-05-25
Just a suggestion: You might get better response if you break these issues into separate posts.

---

### Post by legopilot on 2009-05-25
Ok I can do that. Was trying to save myself work.

---

### Post by VCoolio on 2009-05-25
The permissions for nvidia settings is no error, you need to be root to modify xorg.conf.

For the menu: right click on it and edit.

---

### Post by raymondh on 2009-05-25
> **legopilot said:**
> Hi everyone:     After years of peer pressure to install linux I did. Ubuntu 9.02 is now an impressive linux distro, with ALL the tools necessary to live online along with windows.     Beyond all the praise I have problems I still have not figured out or can't find the answers to. Can anyone shed light on these?  --------------------------------------------------------------  - Nvidia X server       Will not save to X configuration file without invoking sudo--          Default crt-* output swaps out when going from default nvidia driver      to 180.44 driver.        image sharpening option will not save for Nvidia card (Gforce 6800GT AGP)      image sharpening setting will not engage until Nvidia X server menu      is brought up with the corresponding CRT-* selection window.  - Alsa sound system refuses to play out system sound effects ----      system using Via onboard sound (deactivated in bios)     C-media CMI8738 PCI card     Audigy 2 ZS PCI card      Only way to enable this feature was a complicated installation of      pulse audio (apparently used in previous versions)      Even with this fix, youtube audio was still broken.      That was until installing  flashplugin-nonfree-extrasound and     uninstalling flashplugin-nongree  - No tool to remove application icons from dropdown menus      (example is two google earth icons)     where is SMEG?  - Wireless WPA 1 password is not saving reliably. often have to type in      while checking off see password. It is still a hit and miss.  - Can not get bluetooth headset to work with teamspeak for example.       Goal is to use the bluetooth excusively with audio conferencing (sound playback and sound capture).       Where is the ALSA interpretation for the plantronics  headset? (It does interrogate and connect though)   - vncviewer is not installing by default or can not be invoked in terminal.      Modification of installed items in synaptic package manager       was required.  - Can not read extended Fat 32 partitions. example is a logical drive in       the 230 gig range. letter e in windows.   - shutdown is often giving failure messages although successfull.  - hibernation is crashing upon rebooting from the event.  - VNC viewer does not allow desktop switching if running fullscreen. keybard commands anyone?  - Ok Finally, I tried to modify grub to make my default Boot os Windows recently. I had not luck changing the number as depicted in [http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)  Ok that is all my wining, I will appreciate any response in advance and Thanks:  Maurice

Hello Maurice,

Whew ... that's a lot...so let me try to help backwards (from the end)

You can set up GRUB to boot windows first.  In synaptic search for and install startup manager. 

Once done, go to system > administration > startup manager (you'll be asked your passowrd) > boot options .... and change default to the OS of your choice.  

You can also modify the time it takes to decide a boot or even the number of kernels to show in the boot page. 

On your shutdown woes, can you open a terminal and type (or copy & paste ) this command and tell me what happens?

```
sudo shutdown -P 0
``` 

also, what is the error message you mentioned in shutdown?

Let's go from there.

Regards,

---

