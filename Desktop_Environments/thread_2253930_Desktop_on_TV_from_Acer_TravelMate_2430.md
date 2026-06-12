---
title: "Desktop on TV from Acer TravelMate 2430"
date: 2014-11-23
forum: Desktop Environments
---

### Post by Fabzil on 2014-11-23
Hello everyone !

I recently made a clean install of Lubuntu on a laptop Acer TravelMate 2430 and I'm almost done regarding its new role, except I can't get the dual screen to work.
My goal is to **use my TV as a screen** (so having ONLY the TV as screen is also OK)


Current situation is : 
- If I boot the computer **without** the TV plugged in, and then I plug it, **it doesn't work**. On my TV menu, the HDMI4/DVI PC slot is grayed out and if I click on it, it says : "This source is not connected. Please check connexion". If I hit the Fn+F5 to change the current screen, my laptop screen is black but the TV still doesn't detect the computer. I installed ARandR and it doesn't detect the TV screen :(

- If I boot the computer **WITH** the TV plugged in, then the screen is detected. I can choose between having the desktop only on the TV, or on both screens. Problem is : **the text is REALLY small**. The resolution seems to be the same but the "system text" is ridiculously small :( !
(screenshot added)
[[img]http://s27.postimg.org/hu00s1yin/2014_11_23_205842_1280x800_scrot.jpg[/img]](http://postimg.org/image/hu00s1yin/)

=====

The TV is a Samsung Smart TV. I'm connected to the computer with a VGA2HDMI adapter which has been used with other computer and worked.

The console is helping us out : 
fabzil-TravelMate-2430:~$ lspci
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

fabzil-TravelMate-2430:~$ sudo lshw -C video
[sudo] password for fabzil: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:e2100000-e211ffff ioport:9000(size=128)


=====

Please help me to have my TV as a normal screen :)

Have a nice day!

---

### Post by Fabzil on 2014-11-27
Up

Anyone Please?

---

### Post by Fabzil on 2014-12-02
Up :(

If you can't help me, maybe you know another forum where people could help me?
If so, please tell me !

---

### Post by gordintoronto on 2014-12-03
What is the model of the TV? It doesn't have a VGA port? Any time there's an adapter, there's great potential for things to go wrong.

When the TV is used, what is its resolution?

SIS graphics adapters have no support in Linux, other than as generic video. How old is the laptop?

---

