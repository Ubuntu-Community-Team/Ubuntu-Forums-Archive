---
title: "HDMI not responding, NVIDIA, Ubuntu 18.04.3 fresh install"
date: 2019-11-24
forum: Desktop Environments
---

### Post by Midnight_Sun on 2019-11-24
Dear All,

I am in deep trouble.

Context:

New laptop, fresh install Ubuntu 18.04.3.

Attaching external display via HDMI, no signal, no dmesg message, no display detected.


Machine:

```

   description: Notebook
    product: HP Pavilion Laptop 14-ce3xxx (8BW75EA#AKC)
    vendor: HP
    version: Type1ProductConfigId
    serial: 5CD9363GC3
    width: 64 bits
    capabilities: smbios-3.2 dmi-3.2 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=103C_5335KV HP Pavilion sku=8BW75EA#AKC uuid=35434439-3336-3347-4333-F8B46AB6FE18
  *-core
       description: Motherboard
       product: 86E1
       vendor: HP
       physical id: 0
       version: 95.15
       serial: PJLXA028JCO02M
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.02
          date: 07/31/2019
          size: 128KiB
          capacity: 11MiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-1065G7 CPU @ 1.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-1065G7 CPU @ 1.30GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 3617MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz

     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 16GiB
        *-bank
             description: SODIMM DDR4 Synchronous 2667 MHz (0.4 ns)
             product: M471A2K43DB1-CTD
             vendor: Samsung
             physical id: 0
             serial: 41E32D7E
             slot: Bottom
             size: 16GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: iomemory:600-5ff iomemory:400-3ff memory:6016000000-6016ffffff memory:4000000000-400fffffff ioport:8000(size=64) memory:c0000-dffff



        *-pci:1
             description: PCI bridge
             product: Ice Lake-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:6000(size=4096) memory:54000000-54ffffff ioport:6000000000(size=301989888)
           *-display
                description: 3D controller
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:600-5ff iomemory:600-5ff irq:16 memory:54000000-54ffffff memory:6000000000-600fffffff memory:6010000000-6011ffffff ioport:6000(size=128)


$ uname -r
5.0.0-36-generic

$ nvidia-smi
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 435.21       Driver Version: 435.21       CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce MX250       Off  | 00000000:06:00.0 Off |                  N/A |
| N/A   48C    P0    N/A /  N/A |      0MiB /  4042MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+


$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080     77.00* 

```

dmesg only shows ACPI related errors, nothing else.

At original install I had to add nomodeset to grub, else the machine did not boot.

Tried:
- Secure boot disable
- prime-select intel / nvidia
- gdm3 and lightdm
- Legacy mode
- nvidia-xconfig (and with / without modeset=0 also)

For legacy mode, things get crawlingly slow, huge tearing on display refresh. (Under gdm3 and lightdm as well), but still no luck.

For nvidia-xconfig if there is a xorg.conf present, then boot is stuck.

Since I earn my living from presenting stuff, I im kinda desperate.

Please, anyone has a good clue?

Much appreciated!

---

### Post by mörgæs on 2019-11-24
Hardware this new should run the newest software, that is 19.10.

If you like Snap then Ubuntu is an option, if you prefer without I suggest Xubuntu.

---

### Post by Midnight_Sun on 2019-11-25
Thanks for the tip. I have upgraded to 19.10. Nothing changed, still no joy. :-(

Any more tips maybe?

---

### Post by CatKiller on 2019-11-25
> **Midnight_Sun said:**
> Attaching external display via HDMI, no signal, no dmesg message, no display detected.

Optimus setups, like that one, are a complete pain. 

You need to install the proprietary driver for the nvidia half to work, which you seem to have done, but you also need to know which device the monitor is actually attached to. Different manufacturers make different choices about that, so sometimes you'd need to use Prime, and sometimes you'd need to use Reverse Prime, and sometimes you'd need to sacrifice a goat.

There are [other options](https://wiki.archlinux.org/index.php/PRIME) that you don't seem to have tried, and some of the options that you *have* tried are perfectly capable of making a working setup not work. Most importantly, GPU offloading is a work in progress and the driver version that's intended to help with it isn't currently available in any user-friendly way.

---

### Post by Midnight_Sun on 2019-11-26
Tried around, installed nvidia 440 by hand, tried prime-select intel - it stuck by boot, so went back to nvidia. The only thing I could achieve with this new Ubuntu version and nvidia driver is to be able to get rid of nomodeset in grub, and still be able to boot. But external display still dead, and I have no goats to sacrifice. Any thoughts? - Much appreciated!

---

### Post by Midnight_Sun on 2019-11-26
Ok, update, there **is hope**. I have installed manually kernel 5.4, and thing started to work. I have hdmi output, I could install again nvidia driver manually, I could do prime-select. All good...

Except...

The screen has ugly stripes and flickering. Investigating further. This is tougher than I thought! (Again, feedback would be appreciated!)

---

### Post by Midnight_Sun on 2019-11-26
So to say, I am circling in to the solution: If you set nomodeset in grub, then flickering goes away, all is shiny.

Except...

There is no HDMI again! :-D

---

### Post by CatKiller on 2019-11-26
> **Midnight_Sun said:**
> The screen has ugly stripes and flickering. Investigating further. This is tougher than I thought! (Again, feedback would be appreciated!)

Being able to set display timings independently is *also* a work in progress. For quite a while rendering to a display has carried some implicit assumptions - there is one device driving the display, all displays will run at the same refresh rate, 60 Hz is standard, and so on - that are challenged by modern hardware like Optimus or variable refresh rate displays. Work is being done to fix up those issues, but it's hampered by the transition from X11 to Wayland and Nvidia doing their own thing.

Sometime next year (probably) you'd find this all a lot easier than doing it now. There *is* work in progress on how best to handle multiple display devices, and variable refresh rates, and getting Wayland to work with Nvidia hardware, and backporting the Wayland design decisions to X11; it's just not there yet, and all of the parties are somewhat antagonistic to each other.

---

### Post by Midnight_Sun on 2019-12-06
Well, it is nice, that there is hope, but till then, I simply can not use this machine for work. Sad story and 1k EUR wasted. :-(

I have tried newer kernel versions, 5.4.1 stays the same, 5.4.2 is even funnier, since it is completely upside down. (I mean it, I have a screen that is looking downwards, directions exchanged, etc. unbelievable! :-(

---

### Post by mörgæs on 2019-12-06
Nothing is wasted.

I was not able to find this exact Pavilion model but I saw that HP has released BIOS updates for closely related computers. Have you considered upgrading?

---

### Post by Midnight_Sun on 2019-12-06
Intresting idea!

I will research it!

I will need a windows for that, I guess :(

Any workaround ideas?

---

### Post by mörgæs on 2019-12-07
Some vendors make BIOS releases which only runs in Windows, some are able to run from a live boot of Freedos. I don't know what's the case for this HP.

---

### Post by CatKiller on 2019-12-07
I haven't seen a BIOS upgrade that needed anything other than the new file in a decade; bung it on a USB drive, boot into BIOS, hit the upgrade button.

---

### Post by Midnight_Sun on 2019-12-08
Well, well. It WAS a decent struggle. HP BIOS update is rude and unstable. I did need another Win machine. 

Anyhow: BIOS updated, most recent version.

Problem still persists. 
No HDMI with nomodeset, stripes without.

Any further ideas, please?

---

### Post by mörgæs on 2019-12-09
You have tested a number of different kernels which is great.
Have you also tried a clean install of the [daily build]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/") of 20.04?

---

### Post by Midnight_Sun on 2019-12-10
Due to a rather unfortunate happenstance, this machine will be more or less than one I have to live with for now, so I am a bit reluctant to upgrade it to a daily build if it is unstable. (Better to not being able to present then not being able to write the presentation / code at all ;-)

Anyhow, if you could point me to a way where I can squeeze out more useful debug info, I would be happy to. Maybe it is even input for devs / kernel devs, stc.

Any ideas on that, please?

---

### Post by mörgæs on 2019-12-11
The developers are going to ask you to test the development version in a clean install, that is 20.04.

On the other hand, they don't have an opinion on what you install after the 20.04 test is over.

---

### Post by Midnight_Sun on 2019-12-11
Sadly I am not in the position to try a clean install now. I guess then I'll wait for new kernels and see if they help further. Thanks anyhow!

---

### Post by mörgæs on 2019-12-11
It might be pointless waiting. Hardware support is defined by many other components than the kernel.
Anyway, good luck.

---

### Post by Midnight_Sun on 2019-12-11
Then again, I'll have to wait for 20.04 to bereleased and upgradeable. Thanks.

---

### Post by CatKiller on 2019-12-11
It's probably worth trying KDE if you're using Gnome (or Gnome if you're using KDE).

You may have hit the limits of the underlying framework, with X, KMS, Optimus being a nightmare, and so on, but it's possible that your flickering is only exposing a weakness in the desktop environment layer. Gnome and KDE have independent ways of handling that. 

It's something to do while you wait, anyway.

---

### Post by Midnight_Sun on 2019-12-11
Cool advice! Will look into it. Thx

---

### Post by Midnight_Sun on 2019-12-12
Heureka! (??)

I am afraid to say for sure, since now I feel, nothing is for sure anymore, but:
It seems to work now.

I installed KDE, removed nomodeset. It kinda worked, some screen tearing, but was way better than before.
But the breakthrough is: Login with Ubuntu - Wayland option!

Now that did the trick. I have HDMI, and super occasionally rare tearing, minimal effect.

Thanks for all the input Gents, appreciated!

So final setting: 
Kernel: 5.4.2-050402-generic
Ubuntu 19.10
removed nomodeset from grub
And: Wayland!

---

