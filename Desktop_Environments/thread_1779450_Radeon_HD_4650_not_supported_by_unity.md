---
title: "Radeon HD 4650 not supported by unity?"
date: 2011-06-10
forum: Desktop Environments
---

### Post by oryan_dunn on 2011-06-10
Pretty simple.  I've got a machine with an HD 4650 and the natty live cd ends up not in unity.  I've got an even older machine with a radeon xpress 200 and unity works just fine from the live cd on it.  Any ideas?  I didn't want to install it; I've currently got lucid installed on it.

---

### Post by sikander3786 on 2011-06-10
Did you check under System > Administration > Additional Drivers if any proprietary drivers are available. There must be and after installation, you might see Unity. That is the default behavior for the cards that don't support open source drivers.

If it still doesn't work, please post the outputs of these commands from your Terminal to let us dig further.

```
lshw -c video
/usr/lib/nux/unity_support_test -p
```

---

### Post by oryan_dunn on 2011-06-10
> **sikander3786 said:**
> Did you check under System > Administration > Additional Drivers if any proprietary drivers are available. There must be and after installation, you might see Unity. That is the default behavior for the cards that don't support open source drivers.

If it still doesn't work, please post the outputs of these commands from your Terminal to let us dig further.

```
lshw -c video
/usr/lib/nux/unity_support_test -p
```

I'll take a look at the output of those commands when I get home tonight.  I'm pretty sure I'd be able to install the fglrx driver, but right now, I'm just running from the live CD.  I guess I thought that the [opensource radeon]("https://help.ubuntu.com/community/RadeonDriver") driver would support the HD4650 (it should as it supports through the HD5xxx cards), but maybe it doesn't.

---

### Post by sikander3786 on 2011-06-10
From the Live CD too, you can test the drivers as well. Install the drivers and when it asks for a reboot, press Ctrl + Alt + F1 and type 'ubuntu' as username and blank password. Then run the command:

```
sudo service gdm restart
```

Choose Unity at the login screen under sessions options and see if that helps.

---

### Post by oryan_dunn on 2011-06-10
> **sikander3786 said:**
> From the Live CD too, you can test the drivers as well. Install the drivers and when it asks for a reboot, press Ctrl + Alt + F1 and type 'ubuntu' as username and blank password. Then run the command:

```
sudo service gdm restart
```

Choose Unity at the login screen under sessions options and see if that helps.

Thanks for the tip, I'll give that a shot as well.  Is it a known issue that the opensource driver doesn't work well with unity?  I'm still curious why it wouldn't work on my machine.

---

### Post by sikander3786 on 2011-06-10
Not a known issue. I don't have HD 4650 so can't comment. I had an older X300 ATI chip though and Unity worked fine with the open source Radeon driver.

This page states that 3D acceleration on HD 4650 is supported by Radeon driver. Not sure what is causing the problem then. We'll need to see the outputs of the commands mentioned above to diagnose that.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by 3Miro on 2011-06-10
I used Radoen 4250 and it worked fine with Unity and the FOSS driver. 4650 is the same generation hence it should work fine too.

If the 4650 machine a laptop, there may be an issue with the laptop model?

---

### Post by oryan_dunn on 2011-06-10
> **3Miro said:**
> I used Radoen 4250 and it worked fine with Unity and the FOSS driver. 4650 is the same generation hence it should work fine too.

If the 4650 machine a laptop, there may be an issue with the laptop model?


No, it's a desktop.  Kinda ashamed to admit this, but it's my main desktop and is an Athlon XP 2900+.  The card is an HIS HD 4650 AGP card connected via VGA to an old 19" 1440x900 LCD.

---

### Post by 3Miro on 2011-06-10
> **oryan_dunn said:**
> No, it's a desktop.  Kinda ashamed to admit this, but it's my main desktop and is an Athlon XP 2900+.  The card is an HIS HD 4650 AGP card connected via VGA to an old 19" 1440x900 LCD.

That's not bad.

My laptop is Pentium Dual Core 2.4Ghz with Intel Video (which is AGP) and it runs Unity fine. When I tested Unity on 4250 (integrated, PCI-E) I used Phenom II x4.

It is possible that the CPU is slowing Unity, but it is somewhat unlikely. Have you tried Ubuntu Classic to see if that works fine. Classic with effects uses compiz (same as Unity), but is somewhat lighter.

---

### Post by bcschmerker on 2011-06-11
Any luck with the open-source RadeonHD drivers (package: **xserver-xorg-radeonhd**)?  I have been using the Radeon HD X-server on my hybrid Everex® mid-tower with 500W Athena® upgrade PSU and Gigabyte® MA78GM-S2HP upgrade mobo (Advance Micro Devices® Athlon X2 5600+, AMD® 760G chipset, ATI® Radeon™ HD 3200 IGP) under 10.04.2-LTS Lucid and have not encountered any video problems with VGA or DVI.  RadeonHD should be able to support the HD 4000 series (possibly the HD 5000 Series, as of June 2011); AMD® Catalyst™ (package **fglrx-amdcccle**) is a forced move for the HD 6000 due to its bleeding-edge nature.

---

### Post by dancer_69 on 2011-06-11
I have 2 hd4650 cards and I've tested both the ubuntu fglrx and downloaded from ati driver. Unity and 3d effects work and I can enable crossfire also.

---

### Post by oryan_dunn on 2011-06-11
So it seems the first time I booted, it didn't end up in unity, but now, every time I boot, it does.  But, it still doesn't work.
[[IMG]http://img821.imageshack.us/img821/9660/img00009201106111203.th.jpg[/IMG]](http://imageshack.us/photo/my-images/821/img00009201106111203.jpg/)
You can see that unity is running, but there are all kinds of weird problems, and I can't really click anything.  If I didn't have other OSes installed, I'd immediately think it's a hardware problem, but Windows XP, Windows 7 aero, and Lucid with compiz all work just fine on the machine.  I've been unable to open a terminal to run the command to check unity compatability.

I know this isn't related to unity per-say, but I've also tried Fedora 15 and it also has problems booting into Gnome Shell.  Basically, it shows the desktop background, but every 10s or so, the screen flashes to black, and no icons or panels ever load.  I'd really like to try out the latest distros, but for some reason, they seem to not like my hardware.

---

### Post by VOT Productions on 2011-06-11
**ALT+F2** then **unity --replace**

---

### Post by oryan_dunn on 2011-06-13
> **VOT Productions said:**
> **ALT+F2** then **unity --replace**

Gave that a shot, unity shutdown, but then the PC locked up.  Also, after the reboot, tried to run gnome-terminal, but the PC locked up.  Looks like I shouldn't break my rule of only using LTS releases.

Another note, both F15 and Natty work fine on a similar vintage PC with ATI graphics.

---

### Post by oryan_dunn on 2011-07-02
Finally got around to installing Natty on a spare drive.  Even after installed, it has the same behavior.  I was able to see a bit more what was going on.  The screen would flicker off and on once every 15-30s or so.  The live version of Fedora 15 did the same thing.  In both cases dmesg reported the same error.  Here's a snipped of the error from Fedora 15 (didn't know where ubuntu saved the dmesg log)
```
Jul  2 07:04:58 localhost kernel: [  189.942032] radeon 0000:01:00.0: GPU lockup CP stall for more than 10020msec
Jul  2 07:04:58 localhost kernel: [  189.942290] ------------[ cut here ]------------
Jul  2 07:04:58 localhost kernel: [  189.942374] WARNING: at drivers/gpu/drm/radeon/radeon_fence.c:248 radeon_fence_wait+0x248/0x2bb [radeon]()
Jul  2 07:04:58 localhost kernel: [  189.942378] Hardware name:  
Jul  2 07:04:58 localhost kernel: [  189.942381] GPU lockup (waiting for 0x0000004A last fence id 0x00000046)
Jul  2 07:04:58 localhost kernel: [  189.942384] Modules linked in: fuse 8021q garp stp llc ip6t_REJECT nf_conntrack_ipv6 nf_defrag_ipv6 ip6table_filter ip6_tables snd_hda_codec_hdmi snd_intel8x0 snd_hda_intel snd_hda_codec snd_ac97_codec snd_hwdep ac97_bus snd_seq snd_seq_device snd_pcm snd_timer ppdev snd parport_pc sis900 soundcore snd_page_alloc parport mii serio_raw microcode ipv6 squashfs ata_generic pata_acpi pata_sis radeon ttm drm_kms_helper drm i2c_algo_bit i2c_core [last unloaded: mperf]
Jul  2 07:04:58 localhost kernel: [  189.942423] Pid: 1092, comm: Xorg Tainted: G        W   2.6.38.6-26.rc1.fc15.i686 #1
Jul  2 07:04:58 localhost kernel: [  189.942427] Call Trace:
Jul  2 07:04:58 localhost kernel: [  189.942438]  [<c043aa69>] warn_slowpath_common+0x7c/0x91
Jul  2 07:04:58 localhost kernel: [  189.942477]  [<f79daa3f>] ? radeon_fence_wait+0x248/0x2bb [radeon]
Jul  2 07:04:58 localhost kernel: [  189.942514]  [<f79daa3f>] ? radeon_fence_wait+0x248/0x2bb [radeon]
Jul  2 07:04:58 localhost kernel: [  189.942519]  [<c043ab09>] warn_slowpath_fmt+0x33/0x35
Jul  2 07:04:58 localhost kernel: [  189.942557]  [<f79daa3f>] radeon_fence_wait+0x248/0x2bb [radeon]
Jul  2 07:04:58 localhost kernel: [  189.942564]  [<c04515f5>] ? autoremove_wake_function+0x0/0x39
Jul  2 07:04:58 localhost kernel: [  189.942602]  [<f79db028>] radeon_sync_obj_wait+0x11/0x13 [radeon]
Jul  2 07:04:58 localhost kernel: [  189.942617]  [<f78e4461>] ttm_bo_wait+0xae/0x151 [ttm]
Jul  2 07:04:58 localhost kernel: [  189.942660]  [<f79ea232>] radeon_bo_wait+0x6e/0x8d [radeon]
Jul  2 07:04:58 localhost kernel: [  189.942701]  [<f79ea771>] radeon_gem_wait_idle_ioctl+0x2f/0x59 [radeon]
Jul  2 07:04:58 localhost kernel: [  189.942734]  [<f78883bb>] drm_ioctl+0x2a4/0x38a [drm]
Jul  2 07:04:58 localhost kernel: [  189.942776]  [<f79ea742>] ? radeon_gem_wait_idle_ioctl+0x0/0x59 [radeon]
Jul  2 07:04:58 localhost kernel: [  189.942784]  [<c0409bcb>] ? restore_i387_fxsave+0x70/0x7d
Jul  2 07:04:58 localhost kernel: [  189.942792]  [<c0593bf4>] ? file_has_perm+0x9a/0xb3
Jul  2 07:04:58 localhost kernel: [  189.942810]  [<f7888117>] ? drm_ioctl+0x0/0x38a [drm]
Jul  2 07:04:58 localhost kernel: [  189.942816]  [<c04f09ed>] do_vfs_ioctl+0x451/0x482
Jul  2 07:04:58 localhost kernel: [  189.942821]  [<c0593e65>] ? selinux_file_ioctl+0x39/0x3c
Jul  2 07:04:58 localhost kernel: [  189.942826]  [<c04f0a66>] sys_ioctl+0x48/0x6a
Jul  2 07:04:58 localhost kernel: [  189.942834]  [<c07d66b4>] syscall_call+0x7/0xb
Jul  2 07:04:58 localhost kernel: [  189.942837] ---[ end trace 7a441d446ecbec78 ]---
Jul  2 07:04:58 localhost kernel: [  189.942850] [drm] Disabling audio support
Jul  2 07:04:58 localhost kernel: [  189.958894] radeon 0000:01:00.0: f6936400 unpin not necessary
Jul  2 07:04:58 localhost kernel: [  189.958901] radeon 0000:01:00.0: GPU softreset 
Jul  2 07:04:58 localhost kernel: [  189.958905] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xF5703028
Jul  2 07:04:58 localhost kernel: [  189.958909] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00110102
Jul  2 07:04:58 localhost kernel: [  189.958913] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200038C0
Jul  2 07:04:58 localhost kernel: [  189.958925] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
Jul  2 07:04:58 localhost kernel: [  189.973931] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
Jul  2 07:04:58 localhost kernel: [  189.989938] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
Jul  2 07:04:58 localhost kernel: [  189.989942] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
Jul  2 07:04:58 localhost kernel: [  189.989946] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
Jul  2 07:04:58 localhost kernel: [  189.990951] radeon 0000:01:00.0: GPU reset succeed
Jul  2 07:04:58 localhost kernel: [  189.990961] HDMI hot plug event: Pin=3 Presence_Detect=0 ELD_Valid=0
Jul  2 07:04:58 localhost kernel: [  190.010020] radeon 0000:01:00.0: WB disabled
Jul  2 07:04:58 localhost kernel: [  190.056476] [drm] ring test succeeded in 1 usecs
Jul  2 07:04:58 localhost kernel: [  190.056488] [drm] ib test succeeded in 1 usecs
Jul  2 07:04:58 localhost kernel: [  190.056492] [drm] Enabling audio support
Jul  2 07:04:58 localhost kernel: [  190.056931] HDMI hot plug event: Pin=3 Presence_Detect=0 ELD_Valid=0
```

And, here is the output of lshw -c video on my working lucid install.
```
  *-display               
       description: VGA compatible controller
       product: RV730 Pro AGP [Radeon HD 4600 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list rom
       configuration: driver=fglrx_pci latency=32 mingnt=8
       resources: irq:16 memory:d0000000-dfffffff(prefetchable) ioport:d000(size=256) memory:e0020000-e002ffff memory:e0000000-e001ffff(prefetchable)

```

---

### Post by biker3 on 2011-09-28
I think this chip is very troublesome because in Debian it has also its problems. E.g. [with IRQs]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=628080").

---

### Post by mag88 on 2011-10-13
I have the same video card, but it is PCIe.

When I run:
```
lshw -c video
```I get this output:

```
*-display               
       description: VGA compatible controller
       product: RV730 PRO [Radeon HD 4650]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:66 memory:c0000000-cfffffff memory:dfee0000-dfeeffff ioport:cc00(size=256) memory:dfec0000-dfedffff

```and with 
```
 /usr/lib/nux/unity_support_test -p 
```I get this:
```

OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV730
OpenGL version string:  2.1 Mesa 7.12-devel

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

```I log off and Unity 3D doesn't start at all. I see only the wallpaper. The only thing that has effect under my 3D Unity is CTRL+ALT+DEL. I log off and switch back to Unity 2D.

I have to mention that I tried the driver via jockey aka restricted drivers and tried to install the driver that I downloaded from AMD. I ended up using the open source driver which is claimed to work better, but Unity 3D doesn't start.

My system:
Intel P4 @ 3.06GHz
1024MB of RAM
Seagate 80GB HDD SATA II
Audio, LAN: on board 
MB: ASUS P5VD2-MX
OS: Ubuntu 11.10

---

