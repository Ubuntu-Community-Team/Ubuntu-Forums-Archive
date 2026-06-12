---
title: "Steam Civilization 5 segfaults if CPU is hyperthreaded"
date: 2017-01-15
forum: Gaming &amp; Leisure
---

### Post by DuckHook on 2017-01-15
I installed steam from the repos two days ago and it has been an ordeal. Running Ubuntu Xenial with close to a default install. Fortunately, my Google-fu was working, so I found answers to most of the problems. However one big one remains: Civilization 5 keeps segfaulting a few minutes into the game. dmesg/syslog shows:```
Civ5XP[3263]: segfault at 14 ip 000000000885bd5f sp 00000000858ff0d0 error 4 in Civ5XP[8048000+22a7000]
```or```
Civ5XP[14125]: segfault at 0 ip 0000000008cd8534 sp 0000000088afe030 error 4 in Civ5XP[8048000+22a7000]
```
Through an obscure reference found [here]("https://steamcommunity.com/app/8930/discussions/1/38596747621681086/#c154641879453271487"), I am successfully working around this problem by disabling CPU hyperthreading in my BIOS. But giving up hyperthreading is an awfully high price to pay just to run one silly game.

Has anyone else run into this? If so, did you find a better solution?

I should also mention the following:

[list=1]
[*]In order to get both steam and the various games to run at all, I had to use the LD_PRELOAD trick&#8213;specifically:```
export LD_PRELOAD='./libcxxrt.so:/usr/$LIB/libstdc++.so.6:/usr/$LIB/libgcc_s.so.1:/usr/$LIB/libxcb.so.1'
```
[*]I tried installing *intel-microcode*. Didn't help.
[/list]
It's a self-built system but relevant specs are:```
duckhook@Zeus:~$ sudo lshw -c system -c processor -c display -c bus -sanitize
computer                  
    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=[REMOVED]
  *-core
       description: Motherboard
       product: P9X79
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
       serial: [REMOVED]
       slot: To be filled by O.E.M.
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-3930K CPU @ 3.20GHz
          serial: [REMOVED]
          slot: LGA2011
          size: 1586MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=6 enabledcores=6 threads=6
  *-display
       description: VGA compatible controller
       product: Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:d0000000-dfffffff memory:fbe00000-fbe3ffff ioport:e000(size=256) memory:fbe40000-fbe5ffff
```
The only kernel option I have is setting mtrr because system doesn't optimize memory mapping automatically (below). I tried running without this kernel setting and, after updating GRUB and rebooting, it makes no difference. Still those segfaults.
```
duckhook@Zeus:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash enable_mtrr_cleanup mtrr_spare_reg_nr=1 mtrr_gran_size=128M mtrr_chunk_size=128M"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by DuckHook on 2017-01-22
Bump.

---

### Post by oldrocker99 on 2017-01-23
This is a new one on me. Did you repo9rt this on the CIV V Steam forums?

---

### Post by DuckHook on 2017-01-23
> **oldrocker99 said:**
> Did you repo9rt this on the CIV V Steam forums?Not yet, but will do, oldrocker99

In the meantime, I will re-enable hyperthreading and stop wasting so much time on Civ 5. ;)

---

### Post by DuckHook on 2017-01-25
:confused: An update…

Re-enabled hyperthreading. Played 3 solid hours last night without a segfault, whereas it was segfaulting no more than 3 minutes into the game previously. There was a steam update prior to launch, so perhaps it's now fixed. Dunno. Anyhows… if I get another 3 hrs out of it today, I will mark this thread solved.

:confused: I must admit to feeling rather incomplete, though. The problem wasn't really "solved" so much as it just went away. :shrug: Oh well. Best not to look a gift horse in the mouth.

---

### Post by oldrocker99 on 2017-01-25
At least your problem appears to have been solved. Tyranny hard crashes on me every time I play; trouble ticket has been submitted. I've tried it on 16.04, 16.10, and 17.04 and the same result.](*,)

---

### Post by DuckHook on 2017-01-26
:sigh:

Still segfaulting, but I get 3-4 hrs of play.

---

