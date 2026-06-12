---
title: "Xorg High CPU, Destroying Performance"
date: 2009-03-13
forum: General Help
---

### Post by SupaRice on 2009-03-13
I'm running Intrepid, and my machine gets very slow just out of the blue.  There doesn't seem to be any consistent thing I do to cause it.  And the strange thing is it's just started to do this, I've been using it without issue on the current load of Intrepid for about 3 months.  Although when it happens, and I do top in a shell I see that Xorg (mostly) and FireFox are taking turns raping my CPU.  I can still use the machine because each only seems to grab one core and run with it, so there are two left but it sure makes it slow.

I tried this:
[http://ubuntuforums.org/showpost.php?p=6110069&postcount=4](http://ubuntuforums.org/showpost.php?p=6110069&postcount=4)

That I found in this thread:
[http://ubuntuforums.org/showthread.php?t=966629&highlight=xorg+cpu+intrepid](http://ubuntuforums.org/showthread.php?t=966629&highlight=xorg+cpu+intrepid)

But it didn't work.


Looks like others are having the same issue, but I've not found any posts that offer a solution.

[http://ubuntuforums.org/showthread.php?t=1085650&highlight=xorg+cpu+intrepid](http://ubuntuforums.org/showthread.php?t=1085650&highlight=xorg+cpu+intrepid)


I've found a few other threads, but nothing in them to suggest what the issue might be for me.

I've got a Dell Inspiron 530, with a Quad core processor, 3 gig of RAM.  and Nvidia video card.  And pretty much all I do is browse the internet, listen to music, and run a Winblows XP VM with VirtualBox.  However, it will still do this even when the VM isn't active.

I've included below what info I know how to gather, any suggestions?  I'd really rather not reload my machine again to get around this.

```
$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4787.94
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4787.98
clflush size	: 64
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4788.01
clflush size	: 64
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4788.00
clflush size	: 64
power management:

```

```
$ cat /proc/meminfo 
MemTotal:      3110688 kB
MemFree:       2392120 kB
Buffers:         20688 kB
Cached:         255316 kB
SwapCached:          0 kB
Active:         439184 kB
Inactive:       169920 kB
HighTotal:     2226752 kB
HighFree:      1619192 kB
LowTotal:       883936 kB
LowFree:        772928 kB
SwapTotal:     3903752 kB
SwapFree:      3903752 kB
Dirty:             196 kB
Writeback:           0 kB
AnonPages:      333136 kB
Mapped:          88976 kB
Slab:            34900 kB
SReclaimable:    18632 kB
SUnreclaim:      16268 kB
PageTables:       2808 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   5459096 kB
Committed_AS:   852460 kB
VmallocTotal:   110584 kB
VmallocUsed:     56036 kB
VmallocChunk:    50676 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     4096 kB
DirectMap4k:    339968 kB
DirectMap4M:    577536 kB

```

```
$ uname -r
2.6.27-11-generic

```

```
t# lshw -C Video
  *-display               
       description: VGA compatible controller
       product: GeForce 8300 GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

---

### Post by SupaRice on 2009-03-20
Bump...

Anyone?  I've completely reloaded my system, and it's still doing it!  I'm not even running any VM's, I only have FireFox and Open Office open.

[IMG]http://i6.photobucket.com/albums/y213/suparice/xorg1.png[/IMG]

[IMG]http://i6.photobucket.com/albums/y213/suparice/xorg.png[/IMG]

Any help would be appreciated...

---

### Post by Wayne_V on 2009-03-20
I've seen this when the flash plugin wigs out.   Next time it happens run top and see if there is anything else eating cpu.   Try closing browser windows one at a time to see if
that stops it.

---

### Post by SupaRice on 2009-03-20
That makes sense, as the sites I use most in Firefox are flash intesive... and MS Outlook Web Access.

---

### Post by SupaRice on 2009-03-30
So it appears that it is only when there flash is active in Firefox.  Is there anything that I can do about it?  I have a quad core so it's not that bad of a performance hit on this machine but it makes me very scared to upgrade from 8.04 to 8.10 on my other machines that aren't multi-core and don't have this issue.

---

### Post by philinux on 2009-03-30
Have you got 32 or 64 bit install?

---

### Post by SupaRice on 2009-03-31
32 Bit install.

I noticed today that System monitor set it off too though, so it must not just be Flash.

---

### Post by SupaRice on 2009-04-02
Anyone have any ideas?  I mean this really sucks....

---

### Post by Aflack on 2009-04-02
happened to me, 2 weeks and no one could tell me how to fix and i didnt know how... so i switched to linux mint and its works like a dream. but im getting normal ubuntu onces 9.04 comes out. I hate this bug so much...

---

### Post by manemannen on 2009-04-03
I have same problem with Xorg. "top" indicates that Xorg takes ~30% of the cpu. My problem does not seem to be flash/firefox related since the cpu load stays on the same level after firefox has been closed.

Newly installed Kubuntu 8.10 on a Compaq 6910p.

Any suggestions on how to proceed with this one?

---

### Post by Wayne_V on 2009-04-03
which flash plugin are you using?

# dpkg --list | grep flash

If you are using adobe-flashplugin try switching to flashplugin-nonfree or swfdec-mozilla

I'm using flashplugin-nonfree with no problems now.

---

### Post by thyams on 2009-04-03
I heard of this happening with Compiz enabled without 3D acceleration drivers or incorrect drivers for your display adapter installed.

I personally have high CPU% with top without any good display drivers running no matter what my settings.  Instead of my CPU performance going to pure applications it also has to generate the generic desktop image.

To fix this I installed the latest Beta 180.44 from nVidia.  I am not sure what you could do for ATi users, but I am sure instructions are out there.  Intel also has linux drivers you might be able to download.

---

### Post by SupaRice on 2009-04-05
> **Wayne_V said:**
> which flash plugin are you using?

# dpkg --list | grep flash

If you are using adobe-flashplugin try switching to flashplugin-nonfree or swfdec-mozilla

I'm using flashplugin-nonfree with no problems now.

```

$ dpkg --list | grep flash
ii  flashplugin-nonfree                        10.0.22.87ubuntu1~intrepid1             Adobe Flash Player plugin installer

```

But it happens even when I'm not using flash, like I posted earlier it will sometimes happen just when I've got VirtualBox and System Monitor up.

---

### Post by AllenGG on 2009-04-05
Why would you  not use the 64 bit version ?
Try the "Super Ubuntu" live CD version, that requires a download and burn, to see if there's a marked improvement.  (64 bit or multi-processor)
Definitely a factor missing.

---

### Post by mtm_king on 2009-04-05
Try the Flashblock add-on for Firefox.  It reduced the CPU usage by at least 50% for me.

---

### Post by Wayne_V on 2009-04-06
> **SupaRice said:**
> ```

$ dpkg --list | grep flash
ii  flashplugin-nonfree                        10.0.22.87ubuntu1~intrepid1             Adobe Flash Player plugin installer

```But it happens even when I'm not using flash, like I posted earlier it will sometimes happen just when I've got VirtualBox and System Monitor up.

I haven't used VirtualBox - but I have seen issues in the past with vmware and high cpu usage by Xorg.   Have you check the VirtualBox forums for any know issues or tweaks?

---

### Post by SupaRice on 2009-04-07
> **Wayne_V said:**
> I haven't used VirtualBox - but I have seen issues in the past with vmware and high cpu usage by Xorg.   Have you check the VirtualBox forums for any know issues or tweaks?

It happens when I'm not VirtualBox.  It happens sometimes just by FireFox w/ Flash, sometimes when I'm just listening to music.  It's got to be a problem with Xorg or something else.  The strange thing is this is a fairly new machine, and I had 8.04 on it a few months back and it was fine.  It's only since I upgraded to 8.10.

---

### Post by SupaRice on 2009-04-07
> **AllenGG said:**
> Why would you  not use the 64 bit version ?
Try the "Super Ubuntu" live CD version, that requires a download and burn, to see if there's a marked improvement.  (64 bit or multi-processor)
Definitely a factor missing.

Should I?  What are the drawbacks?

```
$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4787.97
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4788.01
clflush size	: 64
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4788.03
clflush size	: 64
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4788.00
clflush size	: 64
power management:

```

---

### Post by SupaRice on 2009-04-16
*bump* Anybody?

---

### Post by CavanMan on 2009-04-17
I believe I am experiencing this same problem. I have just installed 8.10 32-bit (from download) on the following machine: 

HP ML115 G5 Opteron 1352 (2.1 GHz, 2MB) Quad Core 1x1GB Non Hot Plug SATA 160GB DVD

I have done nothing further than install all updates as indicated by the update manager, hence I believe Flash etc. is not yet installed.

The main symptom I see is 100% cpu usage when using system monitor and have clicked on the "resources" tab. When off this tab Xorg is still displaying high CPU usage when viewed via "top".

When just using Firefox, Xorg indicates higher CPU usage than I would expect but the effect are no so noticeable except flicker when dragging a window.

I intended to use this machine to host virtual machines for an old Windows 2000 box I have in addition to others. However I would now be reluctant to proceed. 

Does 8.04 have this issue?

---

### Post by fjpos on 2009-05-04
Hi,


I had a similar problem after upgrading to 9.04 Jaunty and eventaully found by shutting down or removing the 
"vino-server" which is part of the gnome remote desktop connection everthing went back to norm CPU usage 1%-4% from a constant 35% 


sudo apt-get remove vino-server

or you can just stop it without removing


Good luck

---

