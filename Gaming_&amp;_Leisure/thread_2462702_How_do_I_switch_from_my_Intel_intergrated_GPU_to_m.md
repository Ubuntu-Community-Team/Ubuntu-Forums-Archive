---
title: "How do I switch from my Intel intergrated GPU to my AMD dedicated one?"
date: 2021-05-26
forum: Gaming &amp; Leisure
---

### Post by buiphuc on 2021-05-26
Question in title, also I tried to use switcheroo, but it keeps saying "Access denied", and when I switched to root, there's nothing when I entered the commands. Help?

---

### Post by Frogs Hair on 2021-05-26
Are there drivers available or installed for the AMD GPU? This can be checked in additional drivers. I am unfamiliar with switcheroo.

---

### Post by buiphuc on 2021-05-26
> **Frogs Hair said:**
> Are there drivers available or installed for the AMD GPU? This can be checked in additional drivers. I am unfamiliar with switcheroo.
I don't think so. Additional Drivers claims there's no drivers for the GPU. Also, my AMD dedicated GPU model is AMD Radeon R7 M260, and I tried to install the driver for it, but it doesn't work.

---

### Post by ajgreeny on 2021-05-26
I think that graphic card should be supported by the amdgpu driver which also should be installed and used by default in 20.04 and newer versions of Ubuntu.

Let's see what we're dealing with; please show us the outout of terminal command ```
izxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by Frogs Hair on 2021-05-26
The last available proprietary  driver I find for that card was for the 14.04 release.  Wait for an AMD user to address your post. AFIK there are AMD open source driver/s. Bump your post as needed every 12 hours.

---

### Post by buiphuc on 2021-05-26
> **Frogs Hair said:**
> The last available proprietary  driver I find for that card was for the 14.04 release.  Wait for an AMD user to address your post. AFIK there are AMD open source driver/s. Bump your post as needed every 12 hours.
what do you mean by "bump"?

---

### Post by buiphuc on 2021-05-26
> **ajgreeny said:**
> I think that graphic card should be supported by the amdgpu driver which also should be installed and used by default in 20.04 and newer versions of Ubuntu.

Let's see what we're dealing with; please show us the outout of terminal command ```
izxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**
Wait, I tried that and it said command not found

---

### Post by buiphuc on 2021-05-26
> **ajgreeny said:**
> I think that graphic card should be supported by the amdgpu driver which also should be installed and used by default in 20.04 and newer versions of Ubuntu.

Let's see what we're dealing with; please show us the outout of terminal command ```
izxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**
Also I think it's inxi -Fzx, cause when I type izxi -Fzx there's nothing, but if I type inxi -Fzx, then there's this:
```

[FONT=monospace][COLOR=#5454FF]**System:**[/COLOR]
  [COLOR=#5454FF]**Kernel:**[/COLOR][COLOR=#000000] 5.11.0-17-generic x86_64 [/COLOR][COLOR=#5454FF]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454FF]**compiler:**[/COLOR][COLOR=#000000] gcc [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 10.2.1  [/COLOR]
  [COLOR=#5454FF]**Desktop:**[/COLOR][COLOR=#000000] KDE Plasma 5.21.4 [/COLOR][COLOR=#5454FF]**Distro:**[/COLOR][COLOR=#000000] Ubuntu 21.04 (Hirsute Hippo)  [/COLOR]
[COLOR=#5454FF]**Machine:**[/COLOR]
  [COLOR=#5454FF]**Type:**[/COLOR][COLOR=#000000] Portable [/COLOR][COLOR=#5454FF]**System:**[/COLOR][COLOR=#000000] Dell [/COLOR][COLOR=#5454FF]**product:**[/COLOR][COLOR=#000000] Inspiron 5448 [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] A07  [/COLOR]
  [COLOR=#5454FF]**serial:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
  [COLOR=#5454FF]**Mobo:**[/COLOR][COLOR=#000000] Dell [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] 03KM5N [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] A00 [/COLOR][COLOR=#5454FF]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#5454FF]**UEFI:**[/COLOR][COLOR=#000000] Dell [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] A07  [/COLOR]
  [COLOR=#5454FF]**date:**[/COLOR][COLOR=#000000] 06/23/2016  [/COLOR]
[COLOR=#5454FF]**Battery:**[/COLOR]
  [COLOR=#5454FF]**ID-1:**[/COLOR][COLOR=#000000] BAT1 [/COLOR][COLOR=#5454FF]**charge:**[/COLOR][COLOR=#000000] 0.6 Wh [/COLOR][COLOR=#5454FF]**condition:**[/COLOR][COLOR=#000000] 0.6/44.5 Wh (1%)  [/COLOR]
  [COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] SDI DELL VVMKC5BF [/COLOR][COLOR=#5454FF]**status:**[/COLOR][COLOR=#000000] Full  [/COLOR]
[COLOR=#5454FF]**CPU:**[/COLOR]
  [COLOR=#5454FF]**Info:**[/COLOR][COLOR=#000000] Dual Core [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] Intel Core i3-5005U [/COLOR][COLOR=#5454FF]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] MT MCP  [/COLOR]
  [COLOR=#5454FF]**arch:**[/COLOR][COLOR=#000000] Broadwell [/COLOR][COLOR=#5454FF]**rev:**[/COLOR][COLOR=#000000] 4 [/COLOR][COLOR=#5454FF]**L2 cache:**[/COLOR][COLOR=#000000] 3 MiB  [/COLOR]
  [COLOR=#5454FF]**flags:**[/COLOR][COLOR=#000000] avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx  [/COLOR]
  [COLOR=#5454FF]**bogomips:**[/COLOR][COLOR=#000000] 15963  [/COLOR]
  [COLOR=#5454FF]**Speed:**[/COLOR][COLOR=#000000] 798 MHz [/COLOR][COLOR=#5454FF]**min/max:**[/COLOR][COLOR=#000000] 500/1900 MHz [/COLOR][COLOR=#5454FF]**Core speeds (MHz):**[/COLOR][COLOR=#5454FF]**1:**[/COLOR][COLOR=#000000] 798 [/COLOR][COLOR=#5454FF]**2:**[/COLOR][COLOR=#000000] 798  [/COLOR]
  [COLOR=#5454FF]**3:**[/COLOR][COLOR=#000000] 798 [/COLOR][COLOR=#5454FF]**4:**[/COLOR][COLOR=#000000] 798  [/COLOR]
[COLOR=#5454FF]**Graphics:**[/COLOR]
  [COLOR=#5454FF]**Device-1:**[/COLOR][COLOR=#000000] Intel HD Graphics 5500 [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] Dell [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] i915 [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
  [COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 00:02.0  [/COLOR]
  [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] Sunplus Innovation Integrated_Webcam_HD [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] USB  [/COLOR]
  [COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] uvcvideo [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 2-8:5  [/COLOR]
  [COLOR=#5454FF]**Display:**[/COLOR][COLOR=#000000] x11 [/COLOR][COLOR=#5454FF]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.11 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR]
  [COLOR=#5454FF]**loaded:**[/COLOR][COLOR=#000000] amdgpu,ati,modesetting [/COLOR][COLOR=#5454FF]**unloaded:**[/COLOR][COLOR=#000000] fbdev,vesa  [/COLOR]
  [COLOR=#5454FF]**resolution:**[/COLOR][COLOR=#000000] 1366x768~60Hz  [/COLOR]
  [COLOR=#5454FF]**OpenGL:**[/COLOR][COLOR=#5454FF]**renderer:**[/COLOR][COLOR=#000000] Mesa Intel HD Graphics 5500 (BDW GT2)  [/COLOR]
  [COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 4.6 Mesa 21.0.1 [/COLOR][COLOR=#5454FF]**direct render:**[/COLOR][COLOR=#000000] Yes  [/COLOR]
[COLOR=#5454FF]**Audio:**[/COLOR]
  [COLOR=#5454FF]**Device-1:**[/COLOR][COLOR=#000000] Intel Broadwell-U Audio [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] Dell [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel  [/COLOR]
  [COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 00:03.0  [/COLOR]
  [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] Intel Wildcat Point-LP High Definition Audio [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] Dell  [/COLOR]
  [COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 00:1b.0  [/COLOR]
  [COLOR=#5454FF]**Sound Server:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] k5.11.0-17-generic  [/COLOR]
[COLOR=#5454FF]**Network:**[/COLOR]
  [COLOR=#5454FF]**Device-1:**[/COLOR][COLOR=#000000] Realtek RTL810xE PCI Express Fast Ethernet [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] Dell  [/COLOR]
  [COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] r8169 [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**port:**[/COLOR][COLOR=#000000] 4000 [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 02:00.0  [/COLOR]
  [COLOR=#5454FF]**IF:**[/COLOR][COLOR=#000000] enp2s0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#000000] down [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
  [COLOR=#5454FF]**Device-2:**[/COLOR][COLOR=#000000] Intel Wireless 3160 [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] iwlwifi [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454FF]**port:**[/COLOR][COLOR=#000000] 4000  [/COLOR]
  [COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 03:00.0  [/COLOR]
  [COLOR=#5454FF]**IF:**[/COLOR][COLOR=#000000] wlp3s0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#5454FF]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
[COLOR=#5454FF]**Bluetooth:**[/COLOR]
  [COLOR=#5454FF]**Device-1:**[/COLOR][COLOR=#000000] Intel Bluetooth wireless interface [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#5454FF]**driver:**[/COLOR][COLOR=#000000] btusb  [/COLOR]
  [COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 0.8 [/COLOR][COLOR=#5454FF]**bus ID:**[/COLOR][COLOR=#000000] 2-5:3  [/COLOR]
  [COLOR=#5454FF]**Report:**[/COLOR][COLOR=#5454FF]**ID:**[/COLOR][COLOR=#000000] hci0 [/COLOR][COLOR=#5454FF]**state:**[/COLOR][COLOR=#000000] down [/COLOR][COLOR=#5454FF]**address:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
[COLOR=#5454FF]**Drives:**[/COLOR]
  [COLOR=#5454FF]**Local Storage:**[/COLOR][COLOR=#5454FF]**total:**[/COLOR][COLOR=#000000] 223.57 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 10.61 GiB (4.7%)  [/COLOR]
  [COLOR=#5454FF]**ID-1:**[/COLOR][COLOR=#000000] /dev/sda [/COLOR][COLOR=#5454FF]**vendor:**[/COLOR][COLOR=#000000] Western Digital [/COLOR][COLOR=#5454FF]**model:**[/COLOR][COLOR=#000000] WDS240G2G0A-00JH30  [/COLOR]
  [COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 223.57 GiB [/COLOR][COLOR=#5454FF]**temp:**[/COLOR][COLOR=#000000] 30 C  [/COLOR]
[COLOR=#5454FF]**Partition:**[/COLOR]
  [COLOR=#5454FF]**ID-1:**[/COLOR][COLOR=#000000] / [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 218.57 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 10.61 GiB (4.9%) [/COLOR][COLOR=#5454FF]**fs:**[/COLOR][COLOR=#000000] ext4  [/COLOR]
  [COLOR=#5454FF]**dev:**[/COLOR][COLOR=#000000] /dev/sda3  [/COLOR]
  [COLOR=#5454FF]**ID-2:**[/COLOR][COLOR=#000000] /boot/efi [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 512 MiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 5.2 MiB (1.0%) [/COLOR][COLOR=#5454FF]**fs:**[/COLOR][COLOR=#000000] vfat  [/COLOR]
  [COLOR=#5454FF]**dev:**[/COLOR][COLOR=#000000] /dev/sda2  [/COLOR]
[COLOR=#5454FF]**Swap:**[/COLOR]
  [COLOR=#5454FF]**ID-1:**[/COLOR][COLOR=#000000] swap-1 [/COLOR][COLOR=#5454FF]**type:**[/COLOR][COLOR=#000000] file [/COLOR][COLOR=#5454FF]**size:**[/COLOR][COLOR=#000000] 2 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 0 KiB (0.0%) [/COLOR][COLOR=#5454FF]**file:**[/COLOR][COLOR=#000000] /swapfile  [/COLOR]
[COLOR=#5454FF]**Sensors:**[/COLOR]
  [COLOR=#5454FF]**System Temperatures:**[/COLOR][COLOR=#5454FF]**cpu:**[/COLOR][COLOR=#000000] 44.0 C [/COLOR][COLOR=#5454FF]**mobo:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#5454FF]**gpu:**[/COLOR][COLOR=#000000] amdgpu [/COLOR][COLOR=#5454FF]**temp:**[/COLOR][COLOR=#000000] 42.0 C  [/COLOR]
  [COLOR=#5454FF]**Fan Speeds (RPM):**[/COLOR][COLOR=#5454FF]**cpu:**[/COLOR][COLOR=#000000] 0  [/COLOR]
[COLOR=#5454FF]**Info:**[/COLOR]
  [COLOR=#5454FF]**Processes:**[/COLOR][COLOR=#000000] 214 [/COLOR][COLOR=#5454FF]**Uptime:**[/COLOR][COLOR=#000000] 4m [/COLOR][COLOR=#5454FF]**Memory:**[/COLOR][COLOR=#000000] 3.75 GiB [/COLOR][COLOR=#5454FF]**used:**[/COLOR][COLOR=#000000] 1.49 GiB (39.8%)  [/COLOR]
  [COLOR=#5454FF]**Init:**[/COLOR][COLOR=#000000] systemd [/COLOR][COLOR=#5454FF]**runlevel:**[/COLOR][COLOR=#000000] 5 [/COLOR][COLOR=#5454FF]**Compilers:**[/COLOR][COLOR=#5454FF]**gcc:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#5454FF]**Packages:**[/COLOR][COLOR=#000000] 2034  [/COLOR]
  [COLOR=#5454FF]**Shell:**[/COLOR][COLOR=#000000] Bash [/COLOR][COLOR=#5454FF]**v:**[/COLOR][COLOR=#000000] 5.1.4 [/COLOR][COLOR=#5454FF]**inxi:**[/COLOR][COLOR=#000000] 3.3.01 
[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
Notice the second graphics device, it's somehow my webcam, but if I type [/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]lspci -k | grep -EA3 'VGA|3D|Display' [/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000] then it shows up this:
[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]00:02.0 [/COLOR][COLOR=#FF5454]**VGA**[/COLOR][COLOR=#000000] compatible controller: Intel Corporation HD Graphics 5500 (rev 0[/COLOR]
9)
        Subsystem: Dell HD Graphics 5500
        Kernel driver in use: i915
        Kernel modules: i915
[COLOR=#18B2B2]--[/COLOR]
04:00.0 [COLOR=#FF5454]**Display**[/COLOR][COLOR=#000000] controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [/COLOR]
[Radeon R7 M260/M265 / M340/M360 / M440/M445 / 530/535 / 620/625 Mobile]
        Kernel driver in use: amdgpu
        Kernel modules: amdgpu [/FONT]
```[FONT=monospace]
So yeah I really do wonder[/FONT]

---

### Post by ajgreeny on 2021-05-27
Apologies for my typo.

I was using android on my phone which is too small ànd leads to typos far too easily!

---

### Post by mastablasta on 2021-05-27
you should use prime ([COLOR=#242729][FONT=-apple-system]DRI_PRIME=1 )[/FONT][/COLOR]

[https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04](https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04)

for example: > DRI_PRIME=1 steam

---

### Post by buiphuc on 2021-05-27
> **mastablasta said:**
> you should use prime ([COLOR=#242729][FONT=-apple-system]DRI_PRIME=1 )[/FONT][/COLOR]

[https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04](https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04)

for example:
nope, there's no DRI_PRIME=1 (the terminal said that =1 is not a vaild identifier), and I tried "DRI_PRIME=1 steam", but the terminal said that there's no "steam" command too

---

### Post by buiphuc on 2021-05-27
> **buiphuc said:**
> nope, there's no DRI_PRIME=1 (the terminal said that =1 is not a vaild identifier), and I tried "DRI_PRIME=1 steam", but the terminal said that there's no "steam" command too
Oh wait, so "steam" is Steam, right? But what I wanted to do is to set my AMD GPU to be my default GPU, not just for one application

---

### Post by buiphuc on 2021-05-27
> **mastablasta said:**
> you should use prime ([COLOR=#242729][FONT=-apple-system]DRI_PRIME=1 )[/FONT][/COLOR]

[https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04](https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04)

for example:
But I wanted to set my AMD GPU as default, not to use it for just one application...

---

### Post by buiphuc on 2021-05-27
> **ajgreeny said:**
> Apologies for my typo.

I was using android on my phone which is too small ànd leads to typos far too easily!
Then double-checking what you're typing haha, I also do make quite a lot of typos when I type on my phone, but with autocorrect and double-checking a lot, I don't have many typos as before

---

### Post by buiphuc on 2021-05-27
> **mastablasta said:**
> you should use prime ([COLOR=#242729][FONT=-apple-system]DRI_PRIME=1 )[/FONT][/COLOR]

[https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04](https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04)

for example:
Ok, I'm back. I decided to do ```
DRI_PRIME=1
``` and follow this guide ([https://wiki.gentoo.org/wiki/AMDGPU#Test.2C_if_a_discrete_graphics_card_is_in_use](https://wiki.gentoo.org/wiki/AMDGPU#Test.2C_if_a_discrete_graphics_card_is_in_use)). Guess what I found out after I followed the guide (save "/etc/environment" file with ```
DRI_PRIME=1
``` inside it, and ```
export DRI_PRIME=1
``` inside /home/myusername/.bashrc too.)

---

### Post by buiphuc on 2021-05-27
My log-in screen is glitched, and I can't close apps properly. I'm able to use my AMD GPU as default however, so.... Mission failed successfully???

---

### Post by sergi009 on 2021-10-01
yea

---

### Post by buiphuc on 2021-10-02
It actually worked at that time, with no glitches (I decided to install Windows after problems with the laptop overheating). I restarted my laptop, and it's able to be used normally

---

