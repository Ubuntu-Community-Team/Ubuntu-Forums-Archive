---
title: "No visual effects with nvidia-96 driver in Lucid"
date: 2010-06-16
forum: Desktop Environments
---

### Post by jlanthripp on 2010-06-16
I cannot enable any visual effects in Ubuntu 10.04 LTS on my system. Here's what I tried:

System -> Preferences -> Appearance - click "Visual Effects" tab. "None" is selected. I select either "Normal" or "Extra" and my screen flashes a few times, then goes back to normal but with the "Appearances Preferences" dialog box greyed out. After a while, it flashes some more, then everything comes back but the "Normal" radio button is selected again. No error message dialog appears.

Jockey reports that nvidia-96 driver is enabled and in use.

My system has an Nvidia GeForce4 Ti 4400 video card installed, with 2 identical CRT monitors attached. TwinView is working as expected (windows maximize to one screen, non-maximized windows can be dragged from one monitor to the other, my panels appear on only one monitor the way I like, etc.)

Here is the relevant portion of my xorg.conf:

```
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC VistaScan7000"
    HorizSync       30.0 - 69.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection

# Section "Module"
#     Load           "glx"
# EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1024x768_70 +1024+0, CRT-1: 1024x768_70 +0+0; CRT-0: NULL, CRT-1 1024x768_70 +0+0"
    SubSection     "Display"
        Depth       16
    EndSubSection
EndSection

```I have tried the nvidia driver release from the nvidia website (version 96, which supports my video card). It resulted in gdm freezing up immediately after selecting a user for login. I removed that driver and installed nvidia-96 using apt-get.

compiz-check outputs the following:

```
$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```Does anyone know what it is that I'm doing wrong?
TIA!

---

### Post by warfacegod on 2010-06-16
Try disabling one of the monitors.

---

### Post by jlanthripp on 2010-06-16
> **warfacegod said:**
> Try disabling one of the monitors.
Just tried it, rebooted, no dice. Same symptoms as before.

---

### Post by warfacegod on 2010-06-16
Does your processor support SSE? To check, go to: Applications> Accessories> Terminal:

```
sudo lshw
```

Scroll back up to the top. It should look something like this:

```
  *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: NWD
          size: 2800MHz
          capacity: 3200MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr ***[SIZE="3"]sse[/SIZE]*** sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0

```

*(The emphasis is mine.)*

---

### Post by jlanthripp on 2010-06-16
> **warfacegod said:**
> Does your processor support SSE?

Yes to SSE, no to SSE2. It is an AMD Athlon XP (Barton core) 2500+

Here is the relevant output from lshw:

```
*-cpu
          description: CPU
          product: AMD Athlon(TM) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: SOCKET A
          size: 1833MHz
          capacity: 2250MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
```

---

### Post by jlanthripp on 2010-06-16
If it helps, I went into a terminal window and attempted to run Compiz from there. I got the following in that terminal:

```
compiz (core) - Warn: No GLXFBConfig for depth 32

Launching fallback window manager
Window manager warning: Treating resize request of legacy application 0x36000a1 (The Great ) as a fullscreen request
```

---

### Post by warfacegod on 2010-06-16
I'm not sure if sse2 is required or not but I think it is. In any event, I found this: [http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

Seems like a great way to find out if you can even run Compiz.

---

### Post by jlanthripp on 2010-06-16
> **warfacegod said:**
> I'm not sure if sse2 is required or not but I think it is. In any event, I found this: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Seems like a great way to find out if you can even run Compiz.

Yeah, I've run it already and everything checks out okay, like I said in my original post ;-)

---

### Post by warfacegod on 2010-06-16
I didn't even realize they were the same thing.

Okay, I'm stumped.

Only thing else I can recommend is making sure your up to date and have restricted extras and all that installed.

---

### Post by warfacegod on 2010-06-16
> After a while, it flashes some more, then everything comes back but the "Normal" radio button is selected again. No error message dialog appears.

Before this happens, hit Enter.

---

### Post by jlanthripp on 2010-06-16
> **warfacegod said:**
> Before this happens, hit Enter.

That makes it come back to "normal" (Appearance Preferences window not greyed-out) a little quicker, that's all.

---

### Post by warfacegod on 2010-06-16
> **jlanthripp said:**
> That makes it come back to "normal" (Appearance Preferences window not greyed-out) a little quicker, that's all.

I think that means the "Keep Settings" dialog box isn't displaying. Try hitting left or right and then Enter.

Another option is Compiz Switch. Google it.

---

### Post by jlanthripp on 2010-06-16
> **warfacegod said:**
> I think that means the "Keep Settings" dialog box isn't displaying. Try hitting left or right and then Enter.

Another option is Compiz Switch. Google it.

Well, now I see a dialog that says "Visual Effects could not be enabled." I'm not sure what changed to make it start displaying that.

I just installed Compiz-Switch, ran the "fix" the author mentioned on his site to make it work with Lucid Lynx, and with it I have the same results as before, only with a single click :-P

---

### Post by jlanthripp on 2010-06-17
Bah, after messing with it for an entire day, I've reverted to Karmic. Everything works as it should now. Not really a fix, but I'll wait a few months before trying Lucid again...

---

### Post by warfacegod on 2010-06-17
Better than nothing.

---

### Post by gadolinio on 2010-06-17
Same thing happened to me with Jaunty in an Asus Eeepc 1201n, but when trying to set visual effects to normal: the screen flashed with the appearance window greyed out, as if it was applying some change... and then it was still in "none" and the message saying that changes could not be applied appeared (what happened to you after pressing an arrow key and enter).
I solved the problem installing the exact driver for my video card, NVIDIA ION. I post this because the sympthoms are very similar... and that makes me wonder if your problem could be drivers-related too.
Good luck!

---

### Post by james_xxx on 2010-06-21
Would love to find a solution for this as well.

I just did a 9.04 -> 9.10 -> 10.04 incremental upgrade on a machine, and now have no compiz. It throws no errors when I select the desktop effects options, and asks whether or not I want to stay with the new settings, but no compiz desktop effects are working. 

Kind of a bummer.

Compiz had worked great in Jaunty, and appeared to work while the box briefly ran Karmic, too.

Surely there is a fix for this.

---

### Post by warfacegod on 2010-06-21
Both machines that I've briefly had Lucid on had no issues with Compiz. Both had nVidia cards. I'm guessing that this is an Upgrade issue.

---

### Post by ishkabob on 2010-06-22
I was actually able to solve this after much wailing and gnashing of teeth by running the command I found in a post here:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/327056]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/327056")

The command is

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite

```

It just adds a glx config to your xorg.conf.  Fixed it for me

---

### Post by johnzollo on 2010-06-26
> **ishkabob said:**
> I was actually able to solve this after much wailing and gnashing of teeth...

The command is

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite

```

It just adds a glx config to your xorg.conf.  Fixed it for me

Amazing!!!  This worked for me too.  Way to go.  I didn't have the same problem as the bug in launchpad -- I had the same issue as the poster of this thread, but it worked none the less.

Thanks!
-John:guitar:

---

