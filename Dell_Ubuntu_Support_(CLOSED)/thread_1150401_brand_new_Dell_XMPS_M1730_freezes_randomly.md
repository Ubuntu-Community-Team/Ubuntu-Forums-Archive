---
title: "brand new Dell XMPS M1730 freezes randomly"
date: 2009-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Irishpolyglot on 2009-05-06
Hey guys, I have a brand new Dell XPS M1730 and the first thing I did was format it to get rid of Windows, and install Ubuntu 9.04. I installed lots of programs that I like and accepted the recommended video hardware driver (NVIDIA v180) and have Compiz graphics enabled.

But ever since that first boot up my computer keeps randomly crashing! Sometimes not for several hours, sometimes a minute or two after logging in, sometimes when I have a lot of programs running and sometimes when I just have one running. I have had it for a week and I can see that there is no pattern other than the fact that eventually it most likely WILL crash. The screen freezes and sometimes the Caps lock and number lock keys flash. Ctrl+Alt+any function keys or Delete, or pressing ANY key doesn't do anything and my only option is to force a restart.

This is obviously making me lose information, despite auto-saves etc. and it's extremely annoying! I'd appreciate any help someone may provide!

Here is the log just before the most recent crash (just after I initiated a Shut down):
```
May  5 23:43:35 benny-laptop kernel: [51671.446927] Restarting tasks ... done.
May  5 23:43:35 benny-laptop kernel: [51671.964197] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  5 23:43:36 benny-laptop kernel: [51672.181635] Registered led device: iwl-phy0:radio
May  5 23:43:36 benny-laptop kernel: [51672.181653] Registered led device: iwl-phy0:assoc
May  5 23:43:36 benny-laptop kernel: [51672.181666] Registered led device: iwl-phy0:RX
May  5 23:43:36 benny-laptop kernel: [51672.181677] Registered led device: iwl-phy0:TX
May  5 23:43:36 benny-laptop kernel: [51672.219910] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 23:43:36 benny-laptop kernel: [51672.328952] iwlagn: TX Power requested while scanning!
May  5 23:43:36 benny-laptop kernel: [51672.330889] eth1: link down
May  5 23:43:36 benny-laptop kernel: [51672.332885] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  5 23:44:03 benny-laptop kernel: [51699.951858] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  5 23:44:08 benny-laptop kernel: [51704.997943] CPU 0 
May  5 23:44:08 benny-laptop kernel: [51704.997944] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat isofs udf crc_itu_t binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv input_polldev lp parport joydev arc4 ecb snd_hda_intel snd_usb_audio iwlagn iwlcore snd_pcm_oss snd_mixer_oss snd_pcm snd_usb_lib snd_seq_dummy snd_seq_oss led_class mac80211 snd_seq_midi snd_rawmidi snd_seq_midi_event uvcvideo snd_hwdep snd_seq compat_ioctl32 psmouse snd_timer snd_seq_device asix videodev video usbnet iTCO_wdt snd snd_page_alloc cfg80211 nvidia(P) usbhid ricoh_mmc sdhci_pci sdhci v4l1_compat serio_raw pcspkr soundcore iTCO_vendor_support output mii dcdbas intel_agp btusb usb_storage ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
May  5 23:44:08 benny-laptop kernel: [51704.997979] Pid: 3961, comm: compiz.real Tainted: P      D    2.6.28-11-generic #42-Ubuntu
May  5 23:44:08 benny-laptop kernel: [51704.997981] RIP: 0010:[<ffffffffa055b762>]  [<ffffffffa055b762>] nv_vm_free_pages+0x52/0x1c0 [nvidia]
May  5 23:44:08 benny-laptop kernel: [51704.998120] RSP: 0018:ffff880130893c68  EFLAGS: 00010246
May  5 23:44:08 benny-laptop kernel: [51704.998121] RAX: ffff88013d0c3998 RBX: ffff8801314a9d80 RCX: 0000000000000000
May  5 23:44:08 benny-laptop kernel: [51704.998123] RDX: 0000000000000000 RSI: ffffffffa060e258 RDI: ffff880000000000
May  5 23:44:08 benny-laptop kernel: [51704.998124] RBP: ffff880130893c98 R08: 0000000000000001 R09: 0000000000000001
May  5 23:44:08 benny-laptop kernel: [51704.998126] R10: 00007f6b47e5ba58 R11: 0000000000000246 R12: 75096ac34bb150e4
May  5 23:44:08 benny-laptop kernel: [51704.998127] R13: 0000000000000000 R14: ffffffffa08dac80 R15: ffffe20000000000
May  5 23:44:08 benny-laptop kernel: [51704.998129] FS:  00007f6b45399780(0000) GS:ffffffff80aa3000(0000) knlGS:0000000000000000
May  5 23:44:08 benny-laptop kernel: [51704.998130] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
May  5 23:44:08 benny-laptop kernel: [51704.998132] CR2: 00000000021d7058 CR3: 000000012cd28000 CR4: 00000000000006a0
May  5 23:44:08 benny-laptop kernel: [51704.998133] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May  5 23:44:08 benny-laptop kernel: [51704.998135] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May  5 23:44:08 benny-laptop kernel: [51704.998137] Process compiz.real (pid: 3961, threadinfo ffff880130892000, task ffff88013cd91660)
May  5 23:44:08 benny-laptop kernel: [51704.998139]  0000000000000282 0000000000000000 0000000000000001 ffff8801314a9d80
May  5 23:44:08 benny-laptop kernel: [51704.999374]  RSP <ffff880130893c68>
May  5 23:44:08 benny-laptop kernel: [51704.999442] ---[ end trace 45e754f71bd61990 ]---
May  5 23:44:18 benny-laptop kernel: [51714.376038] ------------[ cut here ]------------
May  5 23:44:18 benny-laptop kernel: [51714.376046] WARNING: at /build/buildd/linux-2.6.28/fs/sysfs/group.c:138 sysfs_remove_group+0xd9/0xe0()
May  5 23:44:18 benny-laptop kernel: [51714.376064] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat isofs udf crc_itu_t binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv input_polldev lp parport joydev arc4 ecb snd_hda_intel snd_usb_audio iwlagn iwlcore snd_pcm_oss snd_mixer_oss snd_pcm snd_usb_lib snd_seq_dummy snd_seq_oss led_class mac80211 snd_seq_midi snd_rawmidi snd_seq_midi_event uvcvideo snd_hwdep snd_seq compat_ioctl32 psmouse snd_timer snd_seq_device asix videodev video usbnet iTCO_wdt snd snd_page_alloc cfg80211 nvidia(P) usbhid ricoh_mmc sdhci_pci sdhci v4l1_compat serio_raw pcspkr soundcore iTCO_vendor_support output mii dcdbas intel_agp btusb usb_storage ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
May  5 23:44:18 benny-laptop kernel: [51714.376194] Pid: 726, comm: umount Tainted: P      D    2.6.28-11-generic #42-Ubuntu
May  5 23:44:18 benny-laptop kernel: [51714.376198] Call Trace:
May  5 23:44:18 benny-laptop kernel: [51714.376209]  [<ffffffff80250927>] warn_slowpath+0xb7/0xf0
May  5 23:44:18 benny-laptop kernel: [51714.376218]  [<ffffffff802b0da2>] ? find_lock_page+0x32/0x70
May  5 23:44:18 benny-laptop kernel: [51714.376226]  [<ffffffff802b1de3>] ? filemap_fault+0x1a3/0x430
May  5 23:44:18 benny-laptop kernel: [51714.376234]  [<ffffffff802c60c7>] ? __do_fault+0x277/0x4f0
May  5 23:44:18 benny-laptop kernel: [51714.376243]  [<ffffffff8069e569>] ? _spin_lock+0x9/0x10
May  5 23:44:18 benny-laptop kernel: [51714.376250]  [<ffffffff802fcb6f>] ? destroy_inode+0x4f/0x60
May  5 23:44:18 benny-laptop kernel: [51714.376257]  [<ffffffff802fcb6f>] ? destroy_inode+0x4f/0x60
May  5 23:44:18 benny-laptop kernel: [51714.376264]  [<ffffffff802fd815>] ? generic_delete_inode+0x125/0x1a0
May  5 23:44:18 benny-laptop kernel: [51714.376271]  [<ffffffff8034821d>] ? sysfs_find_dirent+0x2d/0x40
May  5 23:44:18 benny-laptop kernel: [51714.376278]  [<ffffffff80349e29>] sysfs_remove_group+0xd9/0xe0
May  5 23:44:18 benny-laptop kernel: [51714.376287]  [<ffffffff804bd367>] dpm_sysfs_remove+0x17/0x20
May  5 23:44:18 benny-laptop kernel: [51714.376296]  [<ffffffff804b6d92>] device_del+0x22/0x1d0
May  5 23:44:18 benny-laptop kernel: [51714.376303]  [<ffffffff804b6f51>] device_unregister+0x11/0x20
May  5 23:44:18 benny-laptop kernel: [51714.376310]  [<ffffffff802c0f7a>] bdi_unregister+0x3a/0x50
May  5 23:44:18 benny-laptop kernel: [51714.376316]  [<ffffffff802c0fa1>] bdi_destroy+0x11/0x40
May  5 23:44:18 benny-laptop kernel: [51714.376323]  [<ffffffff803be8a1>] fuse_put_super+0x121/0x130
May  5 23:44:18 benny-laptop kernel: [51714.376330]  [<ffffffff802e9c7a>] generic_shutdown_super+0x6a/0x120
May  5 23:44:18 benny-laptop kernel: [51714.376336]  [<ffffffff802e9d91>] kill_anon_super+0x11/0x50
May  5 23:44:18 benny-laptop kernel: [51714.376343]  [<ffffffff802ea0b5>] deactivate_super+0x75/0x90
May  5 23:44:18 benny-laptop kernel: [51714.376350]  [<ffffffff80301090>] mntput_no_expire+0xe0/0x150
May  5 23:44:18 benny-laptop kernel: [51714.376357]  [<ffffffff803017b3>] sys_umount+0x53/0xb0
May  5 23:44:18 benny-laptop kernel: [51714.376364]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
May  5 23:44:18 benny-laptop kernel: [51714.376369] ---[ end trace 45e754f71bd61990 ]---
May  6 07:14:44 benny-laptop syslogd 1.5.0#5ubuntu3: restart.
```

---

### Post by Irishpolyglot on 2009-05-06
I don't think the log is going to help. It just crashed again (this time during normal use) and nothing was logged before the boot up sequence (I booted it up immediately after the crash and you can see the 14 minute gap)

```
May  6 12:33:20 benny-laptop kernel: [14205.397731] gdl_indexer[23555]: segfault at ffffffdc0201b978 ip 00007f64f4c61229 sp 000000000201ccf0 error 4 in ld-2.9.so[7f64f4c52000+20000]
May  6 12:47:04 benny-laptop syslogd 1.5.0#5ubuntu3: restart.
```

Is there some other way I can find out what is causing this crash? I have tried disabling programs systematically but it still freezes :(

---

### Post by Irishpolyglot on 2009-05-06
Here's another log; this time it was slightly different to before. Normally when I'm listening to music the sound goes and repeats in a half a second loop at the same time as the rest of the system crashes. This time the sound problem occurred about 5 seconds before the system crashed. Here's the log:
```
May  6 14:47:04 benny-laptop -- MARK --
May  6 14:53:55 benny-laptop kernel: [ 7626.506785] PGD 131d5a067 PUD 13248d067 PMD 0 
May  6 14:53:55 benny-laptop kernel: [ 7626.506807] Dumping ftrace buffer:
May  6 14:53:55 benny-laptop kernel: [ 7626.506812]    (ftrace buffer empty)
May  6 14:53:55 benny-laptop kernel: [ 7626.506815] CPU 1 
May  6 14:53:55 benny-laptop kernel: [ 7626.506819] Modules linked in: binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv input_polldev joydev lp parport arc4 ecb iwlagn snd_usb_audio snd_usb_lib iwlcore snd_hwdep snd_seq_dummy uvcvideo led_class snd_seq_oss snd_hda_intel mac80211 snd_seq_midi snd_rawmidi compat_ioctl32 snd_seq_midi_event psmouse snd_seq videodev snd_seq_device snd_pcm_oss snd_mixer_oss asix ricoh_mmc sdhci_pci sdhci cfg80211 v4l1_compat usbhid pcspkr serio_raw video snd_pcm snd_timer snd_page_alloc snd soundcore intel_agp iTCO_wdt iTCO_vendor_support output usbnet mii dcdbas btusb nvidia(P) ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
May  6 14:53:55 benny-laptop kernel: [ 7626.506919] Pid: 3749, comm: pulseaudio Tainted: P           2.6.28-11-generic #42-Ubuntu
May  6 14:53:55 benny-laptop kernel: [ 7626.506924] RIP: 0010:[<ffffffffa08c1b47>]  [<ffffffffa08c1b47>] snd_pcm_playback_poll+0x17/0xf0 [snd_pcm]
May  6 14:53:55 benny-laptop kernel: [ 7626.506945] RSP: 0018:ffff880132501aa8  EFLAGS: 00010246
May  6 14:53:55 benny-laptop kernel: [ 7626.506949] RAX: ffff88013cccb740 RBX: 0000000000000000 RCX: 0000000000000000
May  6 14:53:55 benny-laptop kernel: [ 7626.506953] RDX: 0000000000000006 RSI: 0000000000000000 RDI: ffff88011b409000
May  6 14:53:55 benny-laptop kernel: [ 7626.506958] RBP: ffff880132501ab8 R08: 0000000000000005 R09: ffff88011b409028
May  6 14:53:55 benny-laptop kernel: [ 7626.506962] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000000
May  6 14:53:55 benny-laptop kernel: [ 7626.506966] R13: ffff88011b409000 R14: 0000000000000000 R15: ffff880132501ddc
May  6 14:53:55 benny-laptop kernel: [ 7626.506972] FS:  00007f9a2dcc9950(0000) GS:ffff88013f803a80(0000) knlGS:0000000000000000
May  6 14:53:55 benny-laptop kernel: [ 7626.506977] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May  6 14:53:55 benny-laptop kernel: [ 7626.506982] CR2: 00000000000000a8 CR3: 0000000132492000 CR4: 00000000000006a0
May  6 14:53:55 benny-laptop kernel: [ 7626.506986] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May  6 14:53:55 benny-laptop kernel: [ 7626.506991] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May  6 14:53:55 benny-laptop kernel: [ 7626.506996] Process pulseaudio (pid: 3749, threadinfo ffff880132500000, task ffff88013371d980)
May  6 14:53:55 benny-laptop kernel: [ 7626.507004]  0000000000000000 ffff880132501dd4 ffff880132501b48 ffffffff802f7509
May  6 14:53:55 benny-laptop kernel: [ 7626.507382]  RSP <ffff880132501aa8>
May  6 14:53:55 benny-laptop kernel: [ 7626.507391] ---[ end trace aa58e0dd5bc6fb2a ]---
May  6 14:54:55 benny-laptop syslogd 1.5.0#5ubuntu3: restart.
```

However, sound was NOT playing on many other crashes.

---

### Post by Irishpolyglot on 2009-05-06
Someone suggested that I uninstall pulseaudio, since it gave them problems too. I tried that (following [this]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") guide to completely remove it) but it crashed again anyway:
```
May  6 20:09:31 benny-laptop -- MARK --
May  6 20:12:35 benny-laptop kernel: [ 2598.929586] gdl_indexer[3874]: segfault at ffffffdc016f5978 ip 00007fae1a8d1229 sp 00000000016f6cf0 error 4 in ld-2.9.so[7fae1a8c2000+20000]
May  6 20:14:38 benny-laptop syslogd 1.5.0#5ubuntu3: restart.
```
then again
```
May  6 21:55:43 benny-laptop kernel: [   17.357023] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
May  6 21:55:43 benny-laptop kernel: [   17.561981] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0d08bc0
May  6 21:55:45 benny-laptop kernel: [   19.203320] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  6 21:55:45 benny-laptop kernel: [   19.203322] Bluetooth: BNEP filters: protocol multicast
May  6 21:55:45 benny-laptop kernel: [   19.218758] Bridge firewalling registered
May  6 21:55:47 benny-laptop kernel: [   21.188912] ppdev: user-space parallel port driver
May  6 21:55:51 benny-laptop kernel: [   24.782055] eth1: link down
May  6 21:55:51 benny-laptop kernel: [   24.784277] ADDRCONF(NETDEV_UP): eth1: link is not ready
May  6 21:55:51 benny-laptop kernel: [   24.865553] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  6 21:55:51 benny-laptop kernel: [   24.902785] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-4965-2.ucode
May  6 21:55:51 benny-laptop kernel: [   25.374935] Registered led device: iwl-phy0:radio
May  6 21:55:51 benny-laptop kernel: [   25.374950] Registered led device: iwl-phy0:assoc
May  6 21:55:51 benny-laptop kernel: [   25.374961] Registered led device: iwl-phy0:RX
May  6 21:55:51 benny-laptop kernel: [   25.374973] Registered led device: iwl-phy0:TX
May  6 21:55:51 benny-laptop kernel: [   25.431317] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  6 21:56:10 benny-laptop kernel: [   44.051118] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  6 21:56:50 benny-laptop kernel: [   84.001023] Clocksource tsc unstable (delta = -227323486 ns)
May  6 21:56:51 benny-laptop kernel: [   85.661685] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
May  6 21:57:10 benny-laptop kernel: [  103.771498] CE: hpet increasing min_delta_ns to 15000 nsec
May  6 21:58:01 benny-laptop kernel: [  154.927339] CE: hpet increasing min_delta_ns to 22500 nsec
May  6 21:59:25 benny-laptop syslogd 1.5.0#5ubuntu3: restart.
```

---

### Post by Irishpolyglot on 2009-05-07
Can't anybody even give me a good suggestion?? I have one of Dell's most powerful laptop's and it's been broken ever since I installed Ubuntu, I'm sure there's something I can disable, remove to stop this??

---

### Post by Irishpolyglot on 2009-05-07
Tried to disable and kill all compiz functions. Froze a couple of hours later so that isn't it either...

---

### Post by Sylslay on 2009-05-07
1If it crash from overheat, try disable speedstep in BIOS, set for min freq first, or switch for full spedd all time without speedstep.
At dell 8600 were isue with speedstep.
2 have joy with that 
apt-get install cpufrequtils
cpufreq-info
modprobe acpi_cpufreq
modprobe speedstep-ich
cat /proc/cpuinfo | grep -i Mhz
cpufreq-set -d 650000 (min) -u 2280000 (max)  //write in /etc/rc.local
cpufreq-set -g performance -d 650000 -u 2280000 -c 0 //wpisac do /etc/rc.local

cpufreq-set -f 975000
cpufreq-set -f 1300000

cpufreq-selector -g performance
cpufreq-selector -g ondemand
cpufreq-selector -g powersave


3 Try find new driver for graphic, from lunchpad
[http://ppa.launchpad.net/nvida-](http://ppa.launchpad.net/nvida-).....
it always got option to find beter X-org , graphic driver

PS 4. Welkome at Volvo Ocean Reace , west, :popcorn:

---

### Post by Irishpolyglot on 2009-05-08
Note, the title of this thread should be XPS, NOT XMPS. That's a typo.

@Sylsay Thanks for your response!! I do not think the computer is overheating. I touched the underneath part the last two times and it was fine. It's a new computer so the fans are working perfectly. I'd rather not try your solution because of that; note that the Inspiron and the XPS are very different so I wouldn't try to use a solution for a different computer.
But thanks for the suggestion...
Anybody else??

---

### Post by x C0MMAND0 x on 2009-05-08
Try installing the sensors applet to see if it actually is overheating or not.  You can then add it to your main toolbar by right-clicking, going to "Add to Panel" and choosing "Hardware Sensors Monitor".

```
sudo apt-get install sensors-applet
```

*You may have to reboot after installing.  You shouldn't have to, but I recall one time I did so it would show up under the Add to Panel section.

---

### Post by jack@tortuga on 2009-05-13
Have you tried installing and booting to a different kernel to see if that solves the problem?

---

### Post by Irishpolyglot on 2009-05-13
@ x C0MMAND0 x
I installed the sensors applet, and despite the computer not feeling hot it is actually very hot! The readings are (varying up and down a degree or so every few seconds):
CPU: 50ºC (red line 3/4 way up)
temp1 48ºC (blue 1/4 way up; only one that looks safe)
GPU: 66ºC!!!!! This one is red and at the max. I've even had the computer on a special cooling support with a USB powered fan to make sure the underneath is well ventilated, but that's clearly making no difference.

Do you think that the high GPU temp is causing the problem? Should I go through Sylslay's steps outlined for the Inspiron? Thanks for the tip! If this is the cause of the problem, I hope I can solve it without losing high-end graphics abilities (kind of the reason I bought this computer...)

@jack
I may try that option next if the temperature issue isn't the cause of the problem.

How should I distinguish this fire? Sylsay's steps seem the best ones to go through, but maybe someone can confirm this before I try messing around in the BIOS?

---

### Post by darinmiller@cableone.net on 2009-05-17
Irishpolyglot,

I suspect your instability is from the NVidia drivers.  In 64bit Ubuntu 8.10, I rarely saw lock-ups, but 64bit 9.04 locks up regularly.
A few minutes after waking from sleep is when a majority of lock-ups occur. The lock up is typically preceded by:
[LIST]
[*] Network icons not working (displaying no connection when connection is present).
[*] Choppy Compiz behavior
[*] "Racing" gnome panel session consuming 50% of a dual core CPU.
[*] Firefox exhibits strange behaviour such as the sticky scrolling and back button failures.
[/LIST]
So why do I blame the video drivers? I've seen very similar behaviour occur in 8.10 when I upgraded to beta NVidia video drivers. The problems disappeared by reverting to earlier driver releases or installing subsequent drivers. Lockup frequency decreased in 9.04 when I updated to the 180.51 and now the 180.60 drivers.

I recommend disabling default 180.44 drivers in the System/Admininstration/Hardware option and manually installing the 180.60 driver from NVidia.

Download the lasted beta NVidia drivers here:
[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

Hit control-alt-f2 to take you a non-gui console.

Stop GDM, install the driver and restart GDM:
```
sudo /etc/init.d/gdm stop
sudo ./path/to/driver/NVIDIA-Linux-x86_64-180.60-pkg2.run
sudo /etc/init.d/gdm start

```

The 180.51 and 180.60 drivers still have bugs, i.e. using the NVidia control panel to configure an external monitor causes flakey gnome panel behaviour (180.44 works fine). Also, videos do not play after using the NVidia control panel (black screen) until an alt-sysrq-k keystroke sequence is administered (again 180.44 works fine as well as the buggy 185.08 driver).

Note: the latest 185.08 beta video driver screams under WINE, but the driver is quite buggy (my system won't sleep and has trouble shutting down).

---

### Post by peterDwilliams on 2009-06-11
I was having the same problem on my new M1730, complete lock-up with caps lock and scroll lock flashing.
After noticing a connection to wireless activity and finding disabling wireless stopped the crashes I searched and found this:
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/276990]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/276990")

**The solution for me was to enable the jaunty-backports repository and to install linux-backports-modules.**

Hope this helps.

---

### Post by bongey on 2009-06-21
I have m1730 and I am almost positive it is the default nvidia driver from ubuntu. Usually the only thing that can bring down a system like that is a bad driver of some sort. 
Also I had the same problem until I got rid of the default nvidia driver and installed one strait from nvidia. 

Go to [http://www.nvidia.com/object/linux_display_amd64_185.18.14.html](http://www.nvidia.com/object/linux_display_amd64_185.18.14.html) and download the driver. I am using a slight older one , NVIDIA-Linux-x86_64-180.51-pkg2.run . (Haven't tested the latest, though) ,which can be found on this page [http://www.nvidia.com/object/linux_amd64_display_archive.html](http://www.nvidia.com/object/linux_amd64_display_archive.html). 

Download the two, just in case. Put them in directory you can find from command line. 
I put them on my desktop for the time being. 

Open terminal . 
cd ~/Desktop
ls 
(Make sure you see the files you just downloaded)
sudo /etc/init.d/gdm stop 
You will drop back to a blank screen, hit alt+f1 , or alt+f2 (brings up different login terminals)
Enter your username and password.
sudo apt-get remove --purge nvidia-glx-180
sudo modprobe -r nvidia
cd /lib/modules/2.6.28-11-generic/kernel/drivers
find -name "nvidia*" -type f

IF IT returns a list of files , CAREFULLY remove them . Otherwise you will get conflicts of the wrong api version for the kernel module. 

example
./kernel/drivers/video/nvidia
./kernel/drivers/video/nvidia.ko
so ,
sudo rm ./kernal/drivers/video/nvidia.ko

cd ~/Desktop
sudo sh NVIDIA-Linux-x86_64-180.51-pkg2.run ( or whatever one you are going to install)

After it installs. 

modprobe -r nvidia
modprobe nvidia
dmesg  
The end should have the version loaded you installed
cat /etc/X11/xorg.conf | grep nvidia
should have Driver "nvidia"
Otherwise edit and find the Drivers section and switch it to nvidia. 
(use vim or some other text editor)

Next to test if it works correctly. 
startx 
If it loads without crashing , you have done things right, if it doesn't drop back to terminal . 
dmesg
if you see something about wrong api version , you didn't delete the all the files old nvidia files in the /lib/modules/2.6.28-11-generic/
make sure you have direct rendering (open terminal) 

glxgears 
should get around 10000 fps or at least more than 5,000 fps. 

sudo reboot ( if all is well)

---

