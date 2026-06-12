---
title: "[SOLVED] Please help with a nvidia driver problem!"
date: 2008-12-07
forum: General Help
---

### Post by FokkerCharlie on 2008-12-07
Hi all

Well, I have made a bit of a mess here.  I saw this thread:

[http://ubuntuforums.org/showthread.php?p=6326809#post6326809]("http://ubuntuforums.org/showthread.php?p=6326809#post6326809")

Which promised improved performance on my laptop with a 8600M GS card.  I installed the 180.06 beta driver using the nvidia installer, and all seemed well.  Unfortunately, I found that my laptop would not resume from standby.  So, I also tried the 180.11 version from the jaunty repo, by temporarily enabling this repository.  (OK, I think that this was where I went really daft.  Sorry).

Still unable to restart, I attempted to revert back to the 173 driver that I had been using.  So, I uninstalled the 180 (jaunty) driver, and tried with Envy to go for 173.  That failed.  So I tried installing nvidia-glx-173 from terminal, (and synaptic with the same result) (the proprietary drivers manager showed me a blank space), but the following was the result:

```
sudo apt-get install -f nvidia-glx-173
[sudo] password for charlie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  nvidia-glx-173
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/7695kB of archives.
After this operation, 23.0MB of additional disk space will be used.
(Reading database ... 212214 files and directories currently installed.)
Unpacking nvidia-glx-173 (from .../nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/xorg/modules/extensions/libglx.so', which is also in package xserver-xorg-core
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So that didn't work out.  It looks to me like:
/usr/lib/xorg/modules/extensions/libglx.so does not exist, so I'm completedly stumped by that error.

I can't even install from the beta or stable binaries from the nvidia site, returning:

ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

Here's the full output from the log file:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Dec  7 22:03:19 2008
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-9-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-9-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-9-generi
   c/build SYSOUT=/lib/modules/2.6.27-9-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-9-generic/build SUBDIRS=
   /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tmp_ve
   rsions ; rm -f /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.
   tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz24610/NVIDIA-Linux-x86-173.14.
   12-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.nv
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNE
   L__  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -
   include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fu
   nction-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -W
   no-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 
   -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-fra
   me-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wn
   o-pointer-sign -I/tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qua
   l -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" 
   -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=K
   BUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz24610
   /NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tmp_nv.o /tmp/
   selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:19,
                    from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/asm/bitops.h: In function ‘set_bit’:
   include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arith
   metic
   include/asm/bitops.h: In function ‘clear_bit’:
   include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:19,
                    from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:19,
                    from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1971: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:86,
                    from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:107:2
   7: error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:109,
                    from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h: In f
   unction ‘nv_execute_on_all_cpus’:
   /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:674: 
   error: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c: In functio
   n ‘nv_kern_cpu_callback’:
   /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1299: error
   : too many arguments to function ‘smp_call_function’
   /tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1306: error
   : too many arguments to function ‘smp_call_function’
   make[3]: *** [/tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv
   .o] Error 1
   make[2]: *** [_module_/tmp/selfgz24610/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

So I think that I have done something stupid with the kernel or something...

Please help, this is driving me nuts!

Charlie

---

### Post by kubug on 2008-12-07
Hey Charlie,

yeah, something went wrong there. I also have the 180.11 Beta running, and just like the 180.06, it doesn't come out of suspend. I am living with it right now, but will be going back to 177 soon, unless they come out with a fix soon.

Have you tried the uninstall option in Envy. Envy does a whole lot of little "moves" that you need to undo before you can (should) install another nvidia driver.

Try that and see if you can get the drivers from the ubuntu repo installed again. 

If you get the error again about `/usr/lib/xorg/modules/extensions/libglx.so', try deleting the file by hand with 
```
sudo rm /usr/lib/xorg/modules/extensions/libglx.so 
```

It's a little dirty, but might get you over that hurtle. I had to do something similar on mine to get to install the 180 beta drivers.

---

### Post by phidia on 2008-12-07
What does > lsmod output particularly about nvidia?
Sometimes you will have old lingering drivers from a manual install.
You probably need to search for nvidia and delete the old kernel modules.
There are more detailed explanations on how to do that in the forums.

---

### Post by FokkerCharlie on 2008-12-07
Thanks for the input, chaps.

I actually found this:

sudo dpkg --force-overwrite -i /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb

that worked out.  I now have the driver activated in the restricted drivers manager, and my screen resolution back to its former glory!

However:

```
~$ glxinfo |grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

Here's the lsmod output:

```
~$ lsmod
Module                  Size  Used by
binfmt_misc            16904  1 
af_packet              25728  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,sco,rfcomm,l2cap
vboxdrv                71576  0 
nfsd                  230640  13 
lockd                  71976  1 nfsd
nfs_acl                11264  1 nfsd
auth_rpcgss            42528  1 nfsd
sunrpc                196960  11 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs               12544  1 nfsd
ppdev                  15620  0 
ipv6                  263972  18 
acpi_cpufreq           15500  1 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
container              11520  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
uinput                 15744  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
acer_wmi               18880  0 
snd_hda_intel         381488  4 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
iwl3945                98804  0 
snd_seq_midi           14336  0 
iTCO_wdt               18596  0 
rfkill                 17176  2 iwl3945
sdhci_pci              15360  0 
uvcvideo               62728  0 
mac80211              216820  1 iwl3945
sdhci                  23940  1 sdhci_pci
snd_rawmidi            29824  1 snd_seq_midi
iTCO_vendor_support    11652  1 iTCO_wdt
led_class              12164  2 acer_wmi,iwl3945
evdev                  17696  20 
psmouse                45200  0 
compat_ioctl32          9344  1 uvcvideo
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
mmc_core               58268  1 sdhci
serio_raw              13444  0 
snd_timer              29960  2 snd_pcm,snd_seq
videodev               41344  1 uvcvideo
ricoh_mmc              11904  0 
cfg80211               32392  2 iwl3945,mac80211
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7103300  0 
v4l1_compat            22404  2 uvcvideo,videodev
i2c_core               31892  1 nvidia
snd                    63268  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
wmi                    14504  1 acer_wmi
ac                     12292  0 
battery                18436  0 
button                 14224  0 
iptable_nat            13448  0 
nf_nat                 25368  1 iptable_nat
nf_conntrack_ipv4      21900  3 iptable_nat,nf_nat
nf_conntrack           72032  3 iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle         10880  0 
iptable_filter         10752  0 
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22916  2 iptable_nat,ip_tables
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
pata_acpi              12160  0 
ata_generic            12932  0 
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ahci                   37132  2 
ata_piix               24580  0 
tg3                   129924  0 
libphy                 27392  1 tg3
ohci1394               37936  0 
libata                177312  4 pata_acpi,ata_generic,ahci,ata_piix
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fuse                   60828  3 
vesafb                 13828  1 
fbcon                  47648  73 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```


Looks like an nvidia module (I think!) is loaded?

Thanks again- if you can help me with a fix for this, I'd be grateful (again!!)

Charlie

---

### Post by kubug on 2008-12-07
That error would be from the libglx.so that you couldn't overwrite before. Something didn't install properly again. You won't have any 3D acceleration right now.

I would get rid of all installed nvidia drivers and install the 177's.

```
sudo apt-get remove nvidia*
```

```
sudo apt-get install nvidia-glx-177
```

See, if that helps any.

---

### Post by FokkerCharlie on 2008-12-07
Thanks, Kubug.

Unfortunately, that didn't seem to help any.  Still in the same position after trying with both 173 and 177 drivers.  All the installing and uninstalling happens without any errors that I can see., but it still doesn't look like I have any 3D accel.

Hmmmmmmmmm.

Any more ideas?

Charlie

EDIT:  Just tried installing from the nvidia .run package, and I got the 'ERROR: Unable to build the NVIDIA kernel module' message again.  Something is properly wrong here.

Charlie

---

### Post by kubug on 2008-12-07
Like mentioned by phidia, you most likely still have an old nvidia module in there somewhere.

Have you tried the uninstall feature from envy?? That may fix something that is wrong.

(if you already uninstalled envy)
```
sudo apt-get install envyng-core
```

```
sudo envyng -t
```

and select the "uninstall nvidia" option. Try that first. See if it does anything.

---

### Post by FokkerCharlie on 2008-12-07
OK, I did the envy uninstall, which worked OK.  Rebooted, re-enabled the Nvidia driver, rebooted, and we're as we were- no 3D.

Hmmmm.  Am I looking at a fresh install?

Very grateful for your input on this.

Charlie

---

### Post by kubug on 2008-12-07
No, I don't think a reinstall is necessary. I went through this not too long ago when the 173 driver didn't want to completely uninstall after using envy. 
I have to admit, I haven't touched envy since then.
I just have to get my synapses working together to remember what I did to fix it... hold on ...

---

### Post by kubug on 2008-12-07
Just a quick try ...

```
sudo nvidia-xconfig
```

See if that resets your xorg.conf. I am wondering if "nv" is being loaded instead of "nvidia".

If you can, post your /etc/X11/xorg.conf.

---

### Post by FokkerCharlie on 2008-12-07
Here's my xorg.conf before the command:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed Oct  1 15:09:35 PDT 2008
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier     "Configured Monitor"
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Option	"NoLogo"	"True"
	Driver	"nvidia"
EndSection
```

And after:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed Oct  1 15:09:35 PDT 2008
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier     "Configured Monitor"
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Option	"NoLogo"	"True"
	Driver	"nvidia"
EndSection
```

So it looks like all's OK there.

---

### Post by kubug on 2008-12-07
Yeah, it does seem to match. 

Can you open the nvidia-settings? If you can, at least you are using the nvidia driver.

---

### Post by FokkerCharlie on 2008-12-07
Yes, nvidia-settings opens fine, and reports the correct driver version.

It's bedtime over here in the UK- thanks very much for your input so far- if you have any more ideas, please do let me know!  I'll return to this issue in the morning.

Cheerio!
Charlie

---

### Post by kubug on 2008-12-07
Do you still have the binary driver from nvidia.com, the beta drivers you previously used?

If so, go to the directory you saved it to and type this:

```
sudo sh NVIDIA<tab> --uninstall 
```

<tab> stands for hitting the TAB key. It should auto-complete the file name. If you have more than one nvidia driver in your directory, it will auto-complete until the point where the two files differ in name. At which point you will have to complete some more of the filename, and hit TAB again to let it autocomplete.

If the last paragraph made no sense, read [this.]("http://www.linux.com/articles/54005")

This should then uninstall the driver you previously installed. Hopefully we are cleaning things out right. You already cleaned it with apt-get and envyng. This should be last possible point where you'd have something installed we'd need to get rid of.

You may have to re-install the 177 driver after. Just for good measure.

---

### Post by FokkerCharlie on 2008-12-07
Yep, have done that- both driver installers (uninstalling!) report that there is no nvidia driver installed.  That's after I have uninstalled using envy.

Really is beditme now!

Thanks again

Charlie

---

### Post by kubug on 2008-12-07
Good night.

I suppose, since you went down that road before, you may want to try installing your nvidia driver again via envyng. 

It might just fix it then. Sheesh. I am so out of ideas right now.

---

### Post by FokkerCharlie on 2008-12-08
Well, I seem to have it back again.

Followed some instructions here that I found here:

[http://www.sammyliu.com/index.php/2008/11/another-day-another-broken-intrepid-ibex/](http://www.sammyliu.com/index.php/2008/11/another-day-another-broken-intrepid-ibex/)

Which broke everything, had to re-install xserver-xorg-core and things, but back up and running now.

I certainly wouldn't recommend anyone try installing on Intrepid from the Jaunty repo now!

Many thanks for your help- to be honest, I am not completely sure what went wrong/how I fixed it.  But it's now fixed, so that's OK!

Charlie

---

### Post by kubug on 2008-12-08
> **FokkerCharlie said:**
>  But it's not fixed, so that's OK!

I assume you meant "now" instead of "not". Great! At least you are back up and running. Sorry I couldn't be more "knowledgeable" in fixing it.

Take care.

---

### Post by FokkerCharlie on 2008-12-09
Yes, that's exactly what I meant- vmt for your input again, most helpful.

Editing the post above so that I don't look *quite* such an idiot.

Cheerio!
Charlie

---

### Post by kubug on 2008-12-13
Well guess what... I managed to get the same error message as you did.

What I did:

I installed the BETA drivers, while still having the 177 drivers installed via apt-get (forgot to uninstall first). I tried uninstalling the 177 drivers with apt-get and got an error. I realized I messed up, and tried uninstalling the BETA drivers, and things got worse from here.

What I did to get back up and running was install the 177 and then uninstalled it. Installed the BETA and then uninstalled it, until I had nothing left to uninstall. 

I still got the error you got and remembered that you had to reinstall the xserver-xorg-core.

I didn't do that yet, I simply reinstalled the BETA drivers and I was back up and running. 

--------------

As a side note, the 180.16 BETA drivers still don't work with suspend, so you may not want to use them.

---

### Post by FokkerCharlie on 2008-12-14
Yeah- you're right, I think that my mistake was actually installing the beta driver over the top of the apt-get installed driver.  Glad you've got it sorted out your end- same problem observed with standby here on 180.16 as well.

Cheerio!

Charlie

---

### Post by kubug on 2008-12-14
So the way I finally fixed it was this:

```

sudo apt-get install --reinstall xserver-xorg-core
sudo apt-get install --reinstall libgl1-mesa-glx
sudo apt-get install nvidia-glx-177

```

Of course you'd previously uninstall the BETA driver you downloaded. 

Just as a note for next time we monkey-up our nvidia driver.

---

