---
title: "During boot ubuntu 7.10 says &quot;Video mode not supported&quot;"
date: 2008-04-08
forum: Desktop Environments
---

### Post by lotakoka on 2008-04-08
Hi
I have installed UBUNTU 7.10 on my desk top which has HYUNDAI L70N monitor in DUAL boot option with windows xp.
                    After installation it display "Video mode not supported" if select normal boot. Then tried to boot in recovery mode and got prompt. After existing from prompt i get desktop working and everything looks ok.
              Question why UBUNTU works in recovery mode but not in normal mode. Is there any setting to change to refelect above LCD monitor ?

 Thx

---

### Post by hessiess on 2008-04-08
system specs plz

---

### Post by lotakoka on 2008-04-08
I am sorry 
I am very new to UBUNTU. How do i get system spec ?

THX

---

### Post by hessiess on 2008-04-08
find your computers documentation, if you can also post the output of.

```
lspci
```

that would also help

it sounds like you are trying to use an incorrect resolution and or refresh rate.

have you installed a driver for your gfx card?


you would get more replys if this was in biginers talk or general help

---

### Post by hariprs on 2008-04-08
Hi,

I am also facing the same problem. No display during normal boot. Display comes back once the login screen is loaded.

My configuration:

CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
GPU: Nvidia GeForce 7100 GS
RAM: 1GB
Monitor: Samsung Samtron 56V

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)

---

### Post by hessiess on 2008-04-08
hve you installed the restricted driver for the graphics card?

sudo apt-get install nvidia-glx

---

### Post by hariprs on 2008-04-08
> **hessiess said:**
> hve you installed the restricted driver for the graphics card?

sudo apt-get install nvidia-glx

Yes, I have installed this driver, but still no use.

---

### Post by warp99 on 2008-04-09
> **lotakoka said:**
> Hi
I have installed UBUNTU 7.10 on my desk top which has HYUNDAI L70N monitor in DUAL boot option with windows xp.
                    After installation it display "Video mode not supported" if select normal boot. Then tried to boot in recovery mode and got prompt. After existing from prompt i get desktop working and everything looks ok.
              Question why UBUNTU works in recovery mode but not in normal mode. Is there any setting to change to refelect above LCD monitor ?

 Thx

Do you see the splash screen and/or get to a login screen in normal user mode?

---

### Post by warp99 on 2008-04-09
> **hariprs said:**
> Hi,

I am also facing the same problem. No display during normal boot. Display comes back once the login screen is loaded.

Easy to fix, here's how:

Boot normally, when you get to a login screen don't login, instead press ctrl+alt+F2 to get to a console, login then enter the following:

```
sudo nano /etc/usplash.conf
```
if nano is not installed then:
```
sudo apt-get install nano
```
edit the file to match **YOUR** resolution. Here's an example:

I want a resolution of 1680x1050:
```
# Usplash configuration file
xres=1680
yres=1050

```
save the file, crtl-o, then exit, crtl-x, then enter:
```
sudo dpkg-reconfigure usplash
```
this will create a new initrd.img file with the correct resolution for your monitor, then
```
sudo reboot
```

---

### Post by suoh on 2008-04-09
I'm having a similar problem except that my problem was caused by my own stupidity.  When I boot to the GUI, I have changed the screen resolution  and shouldn't have.  I can still access the command line interface, but how do I change the screen resolution for the GUI through the shell so that I can see it again? (all I get is half a screen of pixelated lines).  Thanks in advance.

Dell E1505
Dual Core Intel Centrino 1.66 GHz
1Gb RAM
ATI Mobility Radeon X1300 GPU

EDIT:  Sorry, The post above answered my question, and I was still posting when it appeared.....

---

### Post by lotakoka on 2008-04-09
Hi
removing quiet splash from the end of the kernel line in my /boot/grub/menu.lst file worked trick for me. But during boot process i see lots of text rollowing over screen . How can i avoid that ?

---

### Post by warp99 on 2008-04-09
Did you edit usplash and reconfigure? If your still have this problem add the 'vga=xxx' at the end of your kernel line. Here's a resolution chart to use:

[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

Set it to match you resolution, or if it's not listed reset the usplash resolution then set 'vga=xxx' to match.

Edit:
Start with the 256 color palette line since usplash doesn't need anything higher.

---

### Post by hariprs on 2008-04-10
> **warp99 said:**
> Easy to fix, here's how:

Boot normally, when you get to a login screen don't login, instead press ctrl+alt+F2 to get to a console, login then enter the following:

```
sudo nano /etc/usplash.conf
```
if nano is not installed then:
```
sudo apt-get install nano
```
edit the file to match **YOUR** resolution. Here's an example:

I want a resolution of 1680x1050:
```
# Usplash configuration file
xres=1680
yres=1050

```
save the file, crtl-o, then exit, crtl-x, then enter:
```
sudo dpkg-reconfigure usplash
```
this will create a new initrd.img file with the correct resolution for your monitor, then
```
sudo reboot
```


Thanks a lot, it worked for me..

---

