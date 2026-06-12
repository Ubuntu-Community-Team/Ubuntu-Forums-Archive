---
title: "Inspiron 1520 and Hardy 8.04"
date: 2008-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LeoSolaris on 2008-04-27
[FONT=Century Gothic][SIZE=2]Over the weekend I did a distro upgrade to 8.04. So far everything is working flawlessly on my Dell Inspiron 1520.
[/SIZE][/FONT]
[LIST]
[*][FONT=Century Gothic][SIZE=2]PulseAudio's control of the HD soundcard Dell sticks in the 1520 is a lot more fine tuned. 
[/SIZE][/FONT]
[*][FONT=Century Gothic][SIZE=2]After an update, and possibility the removal of 'motion' with a restart, the webcam works. It is smoother than it was in 7.10. 
[/SIZE][/FONT]
[*][FONT=Century Gothic][SIZE=2]USB's work just fine with my wireless mouse, and my kitten still likes the random floating fish. 
[/SIZE][/FONT]
[*][FONT=Century Gothic][SIZE=2]The SD card read works just fine, as does TrueCrypt, though I made the mistake of removing my keyfile before upgrading, so I had to reformat an encrypted SD. 
[/SIZE][/FONT]
[*][FONT=Century Gothic][SIZE=2]My hotkeys work perfectly.[/SIZE][/FONT]
[*][FONT=Century Gothic][SIZE=2]The Intel wireless N is working much better under Hardy than it did under Gutsy. The new drivers are much better, I now get an actual reading of signal strength, rather than one that maxes out are 85%.[/SIZE][/FONT]
[*][FONT=Century Gothic][SIZE=2]I stopped getting artifacts from Compiz that I had with Gutsy. I did get the little yellow halo for a little while, but it is tied to the shadow made by windows Decorations. I adjusted the shadow so it stopped showing.[/SIZE][/FONT]
[*][FONT=Century Gothic][SIZE=2]Ubuntu's Firefox 3 Beta 5 renders faster than Swiftfox Beta 5, so I removed Swiftfox.[/SIZE][/FONT]
[/LIST]

It was a fairly smooth and painless procedure. It looks and feels just like my customized 7.10. It fixed minor annoyances, and made improvements. Nothing broke, other than the webcam, and now it is running smooth. 

Leo

P.S. As I was writing this, I decided to turn on my radio, and discovered that my sound stopped working after that update!  Great, fixed my cam, broke my sound! Well, PulseAudio was working just fine...

After going to terminal, I discovered that the PCM setting was at 0, so I turned it up and it worked just fine. I have tunes back.

---

### Post by bobbydaddy on 2008-05-28
Was this the 32 or 64 bit version and could you provide a hardware list?

---

### Post by notwen on 2008-05-28
Glad to hear your upgrade went w/o only minuscule bugs that were easily correctable.  I'm hoping the majority of the N-Series models will sooner be fully functional after normal vanilla installs of Ubuntu.  I've played w/ the Hardy LiveCD and the Inspiron1 420n has a few minor issues, I myself am still waiting for Dell to release their custom Hardy images for the N-Series.  I wish I had more time to tinker with Linux but I don't and am stuck waiting for the custom images.  =p

---

### Post by LeoSolaris on 2008-05-28
Initially it was an upgrade in 32-bit. 


here is an lspci. It was all I had time for today.

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

```

Graphics card is an nVidia 8600GS if memory serves.

It's a nice little computer, I jsut wish it had a slightly better resolution for the screen, and bluetooth.

Leo

P.S. I did discover recently that suspend/hibernate work perfectly out of the box with 8.04 64-bit on this laptop. I never really used it that much before.

---

### Post by LeoSolaris on 2008-06-06
Alright! I just got off the phone with Dell. I called Dell's Ubuntu line for a hardware issue (My 1520 did not originally come with Ubuntu obviously)

The issue was the overcharge to the touchpad from the AC cord was causing my mouse to jump around like a cat on a hot tin roof. (Talk about your mixed metaphors!)

They came up with a solution...   ship me a new power cord.  Apparently this is a known issue with the four pronged power cords and the 1520.

I will get back with you guys to tell you if the new adapter worked out or not. It should be here by the end of the week.

Update on the 1520/64-bit experience: So far everything has been running nearly perfect. A couple of issues though:

Hibernate did something funky last time I used it, so I am leery of switching over to hibernate, but suspend works like a charm. I reconfigured my power management to suspend when I close the lid. First time I've set Ubuntu to do that since I started fiddling with it.

The sound is acting weird. VLC puts the sound out at normal volume, as does BMPx, but Totem is quieter. That's even on the same DVD.

I did have to mess with the integrated mic to get it to work. It took adjusting alsamixer in terminal, making sure it was set to digital in, and a little playing with the volume controls. (Tip: add all of the volume controls and it will let you mess with the mic levels.) I had to do that in 7.10, and it was the same steps.

Everything else has been as smooth as silk. Way to go Ubuntu team!

Leo

Update #2: I received my power cord today. (Three day ship for a warranty part replacement and no questions asked, not even to return the defective part)

So far it is working. I have not had any trouble yet, but then I have not powered down all day since I am torrenting something fairly sizable. Right now, I would call the mouse jumping issue "fixed." If it jumps again, I will post back to let y'all know about it.

---

