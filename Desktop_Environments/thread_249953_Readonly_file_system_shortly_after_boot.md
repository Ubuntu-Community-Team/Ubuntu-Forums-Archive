---
title: "Readonly file system shortly after boot"
date: 2006-09-03
forum: Desktop Environments
---

### Post by sefs on 2006-09-03
Hi all i am recieving a very strange problem.  Shortly after booting up.  Like 2-4 mins after if that long...my system seems to go to a read only status.

What could be wrong.

Thanks.

---

### Post by mssever on 2006-09-03
When there are certain errors, the kernel changes your root filesystem to readonly to prevent hosing your system. /var/log/dmesg (typing dmesg also works, usually) should contain error messages that will tell you what the problem is.

---

### Post by sefs on 2006-09-04
> **mssever said:**
> When there are certain errors, the kernel changes your root filesystem to readonly to prevent hosing your system. /var/log/dmesg (typing dmesg also works, usually) should contain error messages that will tell you what the problem is.

Thanks very much. I will check there to see what the problem is.

When i rebooted it finally forced me into maintainence mode and made me run fsck, which found a lot of erros ... inode something or the other was 16 and change to 8 then did some fixes to directores or something like that.  Had no idea what was going on there.

But after running thru that everything *seems* to work fine.  But am afraid that there may be some damaged files deep down in the system that the fixes  would have caused? or since the system is journaling ... i dont have to worry about that?

Thanks for you answer am looking foward to see the dmesg thing.

Best Regards.

---

### Post by mssever on 2006-09-05
Sounds like your filesystem was corrupted. fsck probably was able to fix everything, but I would make sure that I had a good backup, anyway. Also, if you keep getting problems of this sort, it could be a sign that your hard drive is dying.

---

### Post by davidm on 2006-09-07
I don't believe this is a hardware problem. It's happened to me twice on my EPIA Nehemiah, with two different drives. Here are some ugly dmesg lines:

[17886047.008000] Call Trace:
[17886047.008000]  [<c0160d51>] __fput+0x131/0x160
[17886047.008000]  [<c015f34b>] filp_close+0x3b/0x80
[17886047.008000]  [<c015f3f1>] sys_close+0x61/0xb0
[17886047.008000]  [<c010304b>] sysenter_past_esp+0x54/0x79
[17886047.008000] Code: 1d 34 18 00 eb b6 8b 83 88 01 00 00 e8 b0 ed fa ff eb d7 8d b4 26 00 00 00 00 8d bc 27 00 00 00 00 56 53 8b 44 24 0c 85 c0 74 2d <8b> 58 34 50 e8 cd 0c 07 00 58 85 db 74 1f be 00 e0 ff ff 21 e6
[17886047.008000]  <1>Unable to handle kernel NULL pointer dereference at virtual address 00000834
[17886859.824000]  printing eip:
[17886859.824000] c01692ca
[17886859.824000] *pde = 00000000
[17886859.824000] Oops: 0000 [#7]
[17886859.824000] PREEMPT
[17886859.824000] Modules linked in: ext2 pl2303 usbserial nls_cp437 vfat fat isofs nls_utf8 udf sg sd_mod usb_storage usblp via drm rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec ipv6 dm_mod md_mod sr_mod sbp2 scsi_mod lp af_packet tsdev snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq floppy pcmcia rtc snd_via82xx gameport snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss pcspkr parport_pc parport snd_pcm snd_timer snd_page_alloc snd_mpu401_uart snd_rawmidi snd_seq_device psmouse serio_raw i2c_viapro i2c_core via_rhine via_ircc irda mii crc_ccitt snd soundcore shpchp pci_hotplug yenta_socket rsrc_nonstatic pcmcia_core via_agp agpgart evdev ext3 jbd ide_generic ehci_hcd uhci_hcd usbcore ohci1394 ieee1394 ide_cd cdrom ide_disk via82cxxx generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[17886859.824000] CPU:    0
[17886859.824000] EIP:    0060:[<c01692ca>]    Not tainted VLI
[17886859.824000] EFLAGS: 00210206   (2.6.15-26-386)
[17886859.824000] EIP is at cdev_put+0xa/0x50
[17886859.824000] eax: 00000800   ebx: c3cc8ac0   ecx: eb897678   edx: c3cc8ac0
[17886859.824000] esi: c3cc8ac0   edi: eb897678   ebp: f34e9910   esp: e5971f58
[17886859.824000] ds: 007b   es: 007b   ss: 0068
[17886859.824000] Process chown (pid: 18514, threadinfo=e5970000 task=d1d20570)
[17886859.824000] Stack: c3cc8ac0 c3cc8ac0 c0160d51 00000800 dfff4ea0 c3cc8ac0 00000000 f119e740
[17886859.824000]        c3cc8ac0 c015f34b c3cc8ac0 f119e740 c3cc8ac0 f119e740 e5970000 00000004
[17886859.824000]        f119e740 c015f3f1 c3cc8ac0 f119e740 00000004 00000004 08070117 e5970000
[17886859.824000] Call Trace:
[17886859.824000]  [<c0160d51>] __fput+0x131/0x160
[17886859.824000]  [<c015f34b>] filp_close+0x3b/0x80
[17886859.824000]  [<c015f3f1>] sys_close+0x61/0xb0
[17886859.824000]  [<c010304b>] sysenter_past_esp+0x54/0x79
[17886859.824000] Code: 1d 34 18 00 eb b6 8b 83 88 01 00 00 e8 b0 ed fa ff eb d7 8d b4 26 00 00 00 00 8d bc 27 00 00 00 00 56 53 8b 44 24 0c 85 c0 74 2d <8b> 58 34 50 e8 cd 0c 07 00 58 85 db 74 1f be 00 e0 ff ff 21 e6
[17886859.824000]  <2>EXT3-fs error (device hda1): ext3_free_blocks: Freeing blocks in system zones - Block = 512, count = 1
[17888192.548000] Remounting filesystem read-only

---

### Post by switlikbob on 2007-12-13
I am having the same issue.  I have tried 2 drives.  It seems that after a short period of time, the file systems switched to read-only mode for no apparent reason.  Sometimes the system freezes.  Other times, I will be forced to run fsck on boot.  It fixes a ton of errors, then I reboot...repeat cycle!  Nothing in the logs that helps.  I also ran hard drive utilities to test the integrity of the 2 drives before installing ubuntu...no errors were reported.

---

### Post by mssever on 2007-12-13
> **switlikbob said:**
> I am having the same issue.  I have tried 2 drives.  It seems that after a short period of time, the file systems switched to read-only mode for no apparent reason.  Sometimes the system freezes.  Other times, I will be forced to run fsck on boot.  It fixes a ton of errors, then I reboot...repeat cycle!  Nothing in the logs that helps.  I also ran hard drive utilities to test the integrity of the 2 drives before installing ubuntu...no errors were reported.

Can you boot from a live CD? Have you run the memory test? This definitely sounds to me like a hardware issue of some type. Additionally, what happens if you manually remount / rewrite? ```
sudo mount -o remount,rw /
```

---

