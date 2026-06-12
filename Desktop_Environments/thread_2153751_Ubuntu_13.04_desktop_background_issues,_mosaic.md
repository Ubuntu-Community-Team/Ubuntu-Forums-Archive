---
title: "Ubuntu 13.04 desktop background issues, mosaic"
date: 2013-06-12
forum: Desktop Environments
---

### Post by juranich on 2013-06-12
I have a problem with my desktop background after last update. 
  My Desktop wall paper looks like mosaic and when I open any window, the background keeps the trail of it. 
  I've tried running in fail safe graphics more, no fix. I've tried installing ubuntu-desktop and unity, no fix.
  Please help.

[ATTACH=CONFIG]243758[/ATTACH][ATTACH=CONFIG]243759[/ATTACH]

---

### Post by fivebee on 2013-06-13
I have exactly the same problem. With a program open, though, Unity works fine - no trails or other graphical glitching. Minimise a full open window and try and use Unity over the desktop background and it quickly becomes a ghost trail mess. 

[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]cpu:0
[/TD]
[/TR]
           [TR]
[TD="class: first"]description: [/TD]
[TD="class: second"]CPU[/TD]
[/TR]
          [TR]
[TD="class: first"]product: [/TD]
[TD="class: second"]Intel(R) Pentium(R) 4 CPU 3.00GHz[/TD]
[/TR]
          [TR]
[TD="class: first"]vendor: [/TD]
[TD="class: second"]Intel Corp.[/TD]
[/TR]
          [TR]
[TD="class: first"]physical id: [/TD]
[TD="class: second"]400
[/TD]
[/TR]
          [TR]
[TD="class: first"]bus info: [/TD]
[TD="class: second"]cpu@0
[/TD]
[/TR]
          [TR]
[TD="class: first"]version: [/TD]
[TD="class: second"]15.4.3[/TD]
[/TR]
          [TR]
[TD="class: first"]serial: [/TD]
[TD="class: second"]0000-0F43-0000-0000-0000-0000[/TD]
[/TR]
          [TR]
[TD="class: first"]slot: [/TD]
[TD="class: second"]Microprocessor[/TD]
[/TR]
          [TR]
[TD="class: first"]size: [/TD]
[TD="class: second"]3GHz[/TD]
[/TR]
          [TR]
[TD="class: first"]capacity: [/TD]
[TD="class: second"]4GHz[/TD]
[/TR]
          [TR]
[TD="class: first"]width: [/TD]
[TD="class: second"]64 bits[/TD]
[/TR]
          [TR]
[TD="class: first"]clock: [/TD]
[TD="class: second"]800MHz[/TD]
[/TR]
          [TR]
[TD="class: first"]capabilities: [/TD]
[TD="class: second"]boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr [/TD]
[/TR]
          [TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] id[/TD]
[TD]=[/TD]
[TD]0 
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]display:0
[/TD]
[/TR]
                 [TR]
[TD="class: first"]description: [/TD]
[TD="class: second"]VGA compatible controller[/TD]
[/TR]
                [TR]
[TD="class: first"]product: [/TD]
[TD="class: second"]RV370 [Radeon X600/X600 SE][/TD]
[/TR]
                [TR]
[TD="class: first"]vendor: [/TD]
[TD="class: second"]Advanced Micro Devices [AMD] nee ATI[/TD]
[/TR]
                [TR]
[TD="class: first"]physical id: [/TD]
[TD="class: second"]0
[/TD]
[/TR]
                [TR]
[TD="class: first"]bus info: [/TD]
[TD="class: second"]pci@0000:01:00.0
[/TD]
[/TR]
                [TR]
[TD="class: first"]version: [/TD]
[TD="class: second"]00[/TD]
[/TR]
                [TR]
[TD="class: first"]width: [/TD]
[TD="class: second"]64 bits[/TD]
[/TR]
                [TR]
[TD="class: first"]clock: [/TD]
[TD="class: second"]33MHz[/TD]
[/TR]
                [TR]
[TD="class: first"]capabilities: [/TD]
[TD="class: second"]pm pciexpress msi vga_controller bus_master cap_list rom [/TD]
[/TR]
                [TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] driver[/TD]
[TD]=[/TD]
[TD]radeon[/TD]
[/TR]
[TR]
[TD="class: sub-first"] latency[/TD]
[TD]=[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
                [TR]
[TD="class: first"]resources:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] irq[/TD]
[TD]:[/TD]
[TD]42[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]e0000000-e7ffffff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]efde0000-efdeffff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] ioport[/TD]
[TD]:[/TD]
[TD]dc00(size=256)[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]efe00000-efe1ffff[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by stinkeye on 2013-06-13
> **juranich said:**
> I have a problem with my desktop background after last update. 
  My Desktop wall paper looks like mosaic and when I open any window, the background keeps the trail of it. 
  I've tried running in fail safe graphics more, no fix. I've tried installing ubuntu-desktop and unity, no fix.
  Please help.

[ATTACH=CONFIG]243758[/ATTACH][ATTACH=CONFIG]243759[/ATTACH]
Check to see what driver your using...
```
/usr/lib/nux/unity_support_test -p
```

Eg I'm using the **nouveau** driver
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   **nouveau**
OpenGL renderer string: Gallium 0.4 on NVCF
OpenGL version string:  3.0 Mesa 9.1.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

Also try different settings in
**ccsm > ubuntu unity plugin**
for opacity, backround color and dash blur.

ccsm is **compizconfig-settings-manager** and is not in the default install.
To install...
```
sudo apt-get install compizconfig-settings-manager
```

To run enter **ccsm** in the dash or a terminal.

---

### Post by fivebee on 2013-06-15
Thanks for your suggestions, stinkeye. Changing the compiz settings doesn't solve the problem.

OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV370
OpenGL version string:  2.1 Mesa 9.1.1


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes

---

### Post by NOTAL on 2013-06-19
I am having similar issue. Wallpaper and graphics are fine on login screen and in any application, but leave "window trails" when anything is over the desktop. Killing Nautulis stops the trails. 
It seems that the following solves the problem (I'm not sure if the fix is persistent upon reboot):
```
killall nautilus
nautilus --no-desktop
```

Although now I don't have my desktop icons, so it's not an ideal fix.

---

### Post by NOTAL on 2013-06-29
What I found for me is that what I posted above only works until you log out. When I logged out or restarted, nautulis would startup without the "--no-desktop" option, and the problem would be back. To permanently fix the problem, I had to purge nautulis, and re-install it.

```
sudo apt-get purge nautilus
sudo apt-get install nautilus
```

---

### Post by stinkeye on 2013-06-29
> **NOTAL said:**
> What I found for me is that what I posted above only works until you log out. When I logged out or restarted, nautulis would startup without the "--no-desktop" option, and the problem would be back. To permanently fix the problem, I had to purge nautulis, and re-install it.

```
sudo apt-get purge nautilus
sudo apt-get install nautilus
```
If you kill nautilus it no longer draws icons on the desktop until you either restart the session 
or simply open your home folder, thereby restarting nautilus without the "--no-desktop" option.
Don't think purging and re-installing nautilus will fix.

If killing nautilus fixes your problem, set nautilus not to manage the desktop....in terminal...
```
gsettings set org.gnome.desktop.background show-desktop-icons false 
```
You will no longer have desktop icons or a right click menu on the desktop.

To allow nautilus to manage the desktop again, run...
```
gsettings reset org.gnome.desktop.background show-desktop-icons
```

---

### Post by manisabri on 2013-10-18
Same thing happend to me on 13.04 x64 after today updates. The things mentioned here had no effect on it though.

---

