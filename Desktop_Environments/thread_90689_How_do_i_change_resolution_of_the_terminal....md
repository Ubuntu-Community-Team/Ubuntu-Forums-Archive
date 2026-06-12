---
title: "How do i change resolution of the terminal..."
date: 2005-11-15
forum: Desktop Environments
---

### Post by muted on 2005-11-15
... when X and gnome is not loaded... or if i press ctrl+alt+F1... I would like a higher resolution in there.... how is it done?

---

### Post by muted on 2005-11-15
It would make it much nicer working with...'


Oh, and colors and such perhaps also? Is there a terminal configuration file somewhere?

---

### Post by Joe_lurker on 2005-11-15
You need to enable the console with a Framebuffer: 
Install the package "hwinfo" and "gbase".  'sudo apt-get install hwinfo gbase' or use Synaptic.  hwinfo is used to find the modes your graphics device and gbase is used to conver hex to decimal.

Find out what modes you graphics device supports.  Run the command in a terminal:
```
sudo hwinfo --framebuffer
```
Make sure to note the hex mode "0x****" for the mode you would like.
Convert the hex mode to decimal:
```
gbase -h <hex mode>
```
replacing <hex mode> with the hex code for the mode you want to use.  Do not include the leading 0x.  Make a note of the decimal value.

Now we test.  Assuming you are using GRUB reboot the computer.  When the GRUB menu appear press the 'e' key.  This will enter us into edit mode.  Use the arrow keys to navigate to the line that starts with 'kernel' and press the 'e' key once again.  This should put you at the end of the kernel parameters string.  Type 'vga=<dec mode>' where <dec mode> is the decimal mode number noted from above.  Press enter then the 'b' key to boot.  Once you have booted check the console and see if the mode worked.

To make the change permanent you need to modify the '/biit/grub/menu.lst' file.  Open the file with your favorite editor using sudo.  Locate the line labeled 
# kopt=root...
Append to this line vga=<dec mode> using the values from above.  In a terminal or from your fancy new hi-res console enter the command:
```
sudo update-grub
```
This will regenerate the /boot/grub/menu.lst file for GRUB.  Once again reboot and see it all is well.

-Joe

---

### Post by muted on 2005-11-15
Thanks man!

This hex mode number and dec mode number... where do iget that again...? Is that the resolution i want??

Could you perhaps give an example?!

---

### Post by Joe_lurker on 2005-11-15
When you run the command hwinfo --framebuffer you will see output similar to this:
```
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+3072), 24 bits
  Mode 0x0323: 1024x768 (+4096), 32 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0319: 1280x1024 (+2560), 15 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+3840), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 32 bits
  Mode 0x0372: 1600x1200 (+1600), 8 bits
  Mode 0x0373: 1600x1200 (+3200), 15 bits
  Mode 0x0374: 1600x1200 (+3200), 16 bits
  Mode 0x0375: 1600x1200 (+4800), 24 bits
  Mode 0x0376: 1600x1200 (+6400), 32 bits

```
The hex mode is the number right after the Mode keyword.  For example the last line above we need the number 0376 to feed into gbase.  This will set the mode to 1600x1200 with 32 bit color.  (You probable only need 16 bit color.)

Use gbase to convert the hex number to a decimal number.  The kernel takes a decimal number as an argument to vga=.  Use the command 'gbase -h 0376' (using our example from above.)  In this case you would see output like this:
```
Dec: 886
Hex: 376
Oct: 1566
Bin: 1101110110
```
We want the value labeled Dec:.  In this case 886.  This is the decimal vga mode we pass to the kernel with vga= (in this case vga=886.)

Up to this point we are just gathering information.  The only thing that affects the console (at lease what we are looking for) is the vga=886 boot parameter.

Hope this helps
-Joe

---

### Post by muted on 2005-11-15
thanks again, but writing "hwinfo --framebuffer" does nothing, I get no output:

```
#sudo hwinfo --framebuffer
#
```

any suggestions?

---

### Post by Joe_lurker on 2005-11-15
Run it as sudo in a terminal:
```
sudo hwinfo --framebuffer
```
-Joe

---

### Post by muted on 2005-11-15
[QUOTE=Joe_lurker]Run it as sudo in a terminal:
```
sudo hwinfo --framebuffer
```
-Joe[/QUOTE]
i did... just edited my last post, probably while you were answering...

---

### Post by muted on 2005-11-15
hwinfo works for a couple of other devices i just tried, but it gives me no output for --framebuffer

---

### Post by Joe_lurker on 2005-11-15
It's posible that your graphics hardware isn't supported with a framebuffer.  What graphics card do you have?

-Joe

---

### Post by muted on 2005-11-15
nvidia geforce 6600 GT

---

### Post by muted on 2005-11-15
Is this it? I guess not?! ```
jacob@ubuntu:~$ sudo hwinfo --gfxcard
32: PCI 500.0: 0300 VGA compatible controller (VGA)
  [Created at pci.244]
  Unique ID: Ddhb.Elww4ja2GX9
  Parent ID: vuMS.wxFwtL2jas4
  SysFS ID: /devices/pci0000:00/0000:00:0e.0/0000:05:00.0
  SysFS BusID: 0000:05:00.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0140
  SubVendor: pci 0x196d
  SubDevice: pci 0x0000
  Revision: 0xa2
  Driver: "nvidia"
  Memory Range: 0xf4000000-0xf7ffffff (rw,non-prefetchable)
  Memory Range: 0xd8000000-0xdfffffff (rw,prefetchable)
  Memory Range: 0xfa000000-0xfaffffff (rw,non-prefetchable)
  Memory Range: 0x00000000-0x0001ffff (ro,prefetchable,disabled)
  IRQ: 18 (906915 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Driver Info #0:
    Driver Status: nvidia is active
    Driver Activation Cmd: "modprobe nvidia"
  Driver Info #1:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

Primary display adapter: #32
jacob@ubuntu:~$
```

---

### Post by Joe_lurker on 2005-11-15
I don't know much about the nVidia cards.  I guess there are some problems with the drivers.  It looks like your framebuffer isn't loaded though.  Try the command:
```
modprobe nvidiafb
```
and see what happens.  If it succeeds add a line to your /etc/modules file:
```
nvidiafb
```
and reboot.  Then try again.

-Joe

---

### Post by muted on 2005-11-15
alright i did what you said and the output is still the same... none:
```
jacob@ubuntu:~$ sudo hwinfo --framebuffer
Password:
jacob@ubuntu:~$

```
any suggestions?

---

### Post by Joe_lurker on 2005-11-15
There are alternative drivers available for the nVidia I believe.  Maybe go along that route?  Since I don't have similar hardware I cannot do any testing - sorry.  Maybe someone else with the same hardware will come forward.

-Joe

---

### Post by muted on 2005-11-15
Alright Joe, thankyou very muck for your help! :D

---

