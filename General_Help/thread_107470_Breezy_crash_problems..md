---
title: "Breezy crash problems."
date: 2005-12-23
forum: General Help
---

### Post by yamagami on 2005-12-23
Hey all,

I'm running Breezy on a Toshiba Satellite (upgraded from Hoary).  After upgrading to the 2.6.12-10 kernel, 
i started to experience crashes every time in gnome. It would just 'restart' itself, loging out and loosing all 
data. Sometimes it would crash the whole system forcing me to reset, 
and sometimes it would crash on boot, but it did crash every time. 
when i use the 2.6.10-5-386 things work ok, BUT i need to boot my machine twice:
The first time i boot up the machine would crash, kernel would panic, or gnome would start restarting itself or freeze up. 
(it always something different - the fun never stops here).
I'll then turn off the laptop violently (holding the power button for a few sec) and boot again. 
That second time the machine runs fine. no problems, no hangs, no crash. 

The randomness of the problem is what bothers me... 

Any ideas???  

Harel  
:smile:

---

### Post by schilcha on 2005-12-23
Have a look at the log-files (e.g. /var/log/syslog, /var/log/messages, ...). Maybe you can find something there that will give you a hint.

Good Luck!

---

### Post by yamagami on 2005-12-23
From the syslog and messages i can see the following after gnome restarts itself about every 30 seconds or minute. (I hope i copied all the relevant stuff...). There are other types of 'crashes' though like i said - once i restart (the second time)  the machine is fine - until the next time i turn it off and on again...

```
Dec 23 22:21:13 localhost kernel: uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Dec 23 22:21:13 localhost kernel: hub 3-0:1.0: USB hub found
Dec 23 22:21:13 localhost kernel: hub 3-0:1.0: 2 ports detected
Dec 23 22:21:13 localhost kernel: usb 2-2: new low speed USB device using uhci_hcd and address 2
Dec 23 22:21:13 localhost kernel: input: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:1d.1-2
Dec 23 22:21:14 localhost input.agent[8973]:      tsdev: already loaded
Dec 23 22:21:14 localhost input.agent[8973]:      mousedev: already loaded
Dec 23 22:21:14 localhost input.agent[8973]:      evdev: already loaded
Dec 23 22:21:14 localhost usb.agent[9088]:      usbhid: already loaded
Dec 23 22:21:14 localhost usb.agent[9014]:      usbcore: already loaded
Dec 23 22:21:14 localhost usb.agent[9020]:      usbcore: already loaded
Dec 23 22:21:14 localhost usb.agent[9025]:      usbcore: already loaded
Dec 23 22:21:18 localhost input.agent[9271]:      evdev: already loaded
Dec 23 22:21:18 localhost input.agent[9256]:      evdev: already loaded
Dec 23 22:21:18 localhost input.agent[9323]:      evdev: already loaded
Dec 23 22:21:19 localhost kernel: ACPI: AC Adapter [ACAD] (on-line)
Dec 23 22:21:19 localhost kernel: ACPI: Battery Slot [BAT1] (battery present)
Dec 23 22:21:28 localhost dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 0
Dec 23 22:21:28 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Dec 23 22:21:28 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Dec 23 22:21:28 localhost dhclient: All rights reserved.
Dec 23 22:21:28 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Dec 23 22:21:28 localhost dhclient: 
Dec 23 22:21:28 localhost dhclient: sit0: unknown hardware address type 776
Dec 23 22:21:28 localhost dhclient: sit0: unknown hardware address type 776
Dec 23 22:21:28 localhost dhclient: Bind socket to interface: No such device
Dec 23 22:21:28 localhost dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Dec 23 22:21:28 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Dec 23 22:21:28 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Dec 23 22:21:28 localhost dhclient: All rights reserved.
Dec 23 22:21:28 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Dec 23 22:21:28 localhost dhclient: 
Dec 23 22:21:28 localhost dhclient: sit0: unknown hardware address type 776
Dec 23 22:21:28 localhost dhclient: sit0: unknown hardware address type 776
Dec 23 22:21:28 localhost dhclient: Listening on LPF/eth1/00:02:2d:ab:08:66
Dec 23 22:21:28 localhost dhclient: Sending on   LPF/eth1/00:02:2d:ab:08:66
Dec 23 22:21:28 localhost dhclient: Sending on   Socket/fallback
Dec 23 22:21:29 localhost kernel: eth1: New link status: Connected (0001)
Dec 23 22:21:30 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Dec 23 22:21:30 localhost dhclient: DHCPOFFER from 192.168.0.1
Dec 23 22:21:30 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Dec 23 22:21:37 localhost dhclient: DHCPACK from 192.168.0.1
Dec 23 22:21:39 localhost dhclient: bound to 192.168.0.104 -- renewal in 247 seconds.
Dec 23 22:21:39 localhost kernel: ACPI: Power Button (FF) [PWRF]
Dec 23 22:21:39 localhost kernel: ACPI: Lid Switch [LID]
Dec 23 22:21:39 localhost kernel: eth1: no IPv6 routers present
Dec 23 22:22:04 localhost kernel: Unable to handle kernel paging request at virtual address f498a7ec
Dec 23 22:22:04 localhost kernel:  printing eip:
Dec 23 22:22:04 localhost kernel: c011f7c7
Dec 23 22:22:04 localhost kernel: *pde = 00000000
Dec 23 22:22:04 localhost kernel: Oops: 0002 [#1]
Dec 23 22:22:04 localhost kernel: PREEMPT 
Dec 23 22:22:04 localhost kernel: Modules linked in: thermal fan button battery ac uhci_hcd 8139too isofs udf ipv6 rfcomm l2cap bluetooth proc_intf freq_table cpufreq_userspace cpufreq_ondemand cpufreq_powersave orinoco_cs orinoco hermes pcmcia i915 drm video sony_acpi pcc_acpi container af_packet floppy rtc yenta_socket pcmcia_core 8139cp mii slamr snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc hw_random shpchp pci_hotplug usbhid usbcore intel_agp agpgart nls_cp437 ntfs dm_mod tsdev evdev capability commoncap psmouse mousedev parport_pc lp parport ide_cd cdrom md ext3 jbd ide_generic piix ide_disk ide_core unix processor fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
Dec 23 22:22:04 localhost kernel: CPU:    0
Dec 23 22:22:04 localhost kernel: EIP:    0060:[sigprocmask+140/176]    Tainted: P      VLI
Dec 23 22:22:04 localhost kernel: EFLAGS: 00013202   (2.6.10-5-386) 
Dec 23 22:22:04 localhost kernel: EIP is at sigprocmask+0x8c/0xb0
Dec 23 22:22:04 localhost kernel: eax: 00000000   ebx: ebf09fac   ecx: ecac8ac0   edx: 00000000
Dec 23 22:22:04 localhost kernel: esi: 10000000   edi: 00000000   ebp: 00000000   esp: ebf09f84
Dec 23 22:22:04 localhost kernel: ds: 007b   es: 007b   ss: 0068
Dec 23 22:22:04 localhost kernel: Process Xorg (pid: 5509, threadinfo=ebf08000 task=ecac8ac0)
Dec 23 22:22:04 localhost kernel: Stack: fffffff2 ebf09fac bffff134 ebf08000 c011f83b 00000000 ebf09fac ebf09fa4 
Dec 23 22:22:04 localhost kernel:        ee1839f4 ebf09fc4 10000000 00000000 00000000 00000008 b7f860dc c0102fa1 
Dec 23 22:22:04 localhost kernel:        00000000 bffff1b4 bffff134 00000008 b7f860dc bffff11c 000000af 0000007b 
Dec 23 22:22:04 localhost kernel: Call Trace:
Dec 23 22:22:04 localhost kernel:  [sys_rt_sigprocmask+80/183] sys_rt_sigprocmask+0x50/0xb7
Dec 23 22:22:04 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Dec 23 22:22:04 localhost kernel: Code: 00 00 eb 18 8b 03 8b 53 04 89 91 78 04 00 00 89 81 74 04 00 00 eb 05 bd ea ff ff ff e8 41 e2 ff ff fb b8 00 00 00 00 00 00 00 00 <00> 8b 40 08 a8 08 74 05 e8 fb 6f 14 00 83 7c 24 1c 00 74 09 8b 
Dec 23 22:22:04 localhost kernel:  <6>note: Xorg[5509] exited with preempt_count 1
Dec 23 22:22:04 localhost kernel: scheduling while atomic: Xorg/0x00000001/5509
Dec 23 22:22:05 localhost kernel:  [schedule+76/1109] schedule+0x4c/0x455
Dec 23 22:22:05 localhost kernel:  [unmap_vmas+226/463] unmap_vmas+0xe2/0x1cf
Dec 23 22:22:05 localhost kernel:  [unmap_vmas+354/463] unmap_vmas+0x162/0x1cf
Dec 23 22:22:05 localhost kernel:  [exit_mmap+99/291] exit_mmap+0x63/0x123
Dec 23 22:22:05 localhost kernel:  [mmput+32/125] mmput+0x20/0x7d
Dec 23 22:22:05 localhost kernel:  [do_exit+378/903] do_exit+0x17a/0x387
Dec 23 22:22:05 localhost kernel:  [do_trap+0/199] do_trap+0x0/0xc7
Dec 23 22:22:05 localhost kernel:  [do_page_fault+877/1255] do_page_fault+0x36d/0x4e7
Dec 23 22:22:05 localhost kernel:  [do_page_fault+934/1255] do_page_fault+0x3a6/0x4e7
Dec 23 22:22:05 localhost kernel:  [setup_frame+481/624] setup_frame+0x1e1/0x270
Dec 23 22:22:05 localhost kernel:  [handle_signal+118/200] handle_signal+0x76/0xc8
Dec 23 22:22:05 localhost kernel:  [do_select+637/658] do_select+0x27d/0x292
Dec 23 22:22:05 localhost kernel:  [do_page_fault+0/1255] do_page_fault+0x0/0x4e7
Dec 23 22:22:05 localhost kernel:  [error_code+43/48] error_code+0x2b/0x30
Dec 23 22:22:05 localhost kernel:  [flush_old_exec+1125/1676] flush_old_exec+0x465/0x68c
Dec 23 22:22:05 localhost kernel:  [sigprocmask+140/176] sigprocmask+0x8c/0xb0
Dec 23 22:22:05 localhost kernel:  [sys_rt_sigprocmask+80/183] sys_rt_sigprocmask+0x50/0xb7
Dec 23 22:22:05 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Dec 23 22:22:05 localhost kernel: scheduling while atomic: Xorg/0x00000002/5509
Dec 23 22:22:05 localhost kernel:  [schedule+76/1109] schedule+0x4c/0x455
```

---

### Post by Cuppa-Chino on 2005-12-27
have a similar two boot problem and cannot find anything big that would seem to be wrong.
I have bog standard hardware, have posted also in various other threads no breakthrough yet

---

### Post by yamagami on 2005-12-27
Yeah its a strange one isn't it? The logs do show X crashing, but no reason why...
I'm quite baffled by this and I'm trying not to get used to the double boot ...

Anyone????  :confused: 

Harel

---

### Post by yamagami on 2006-04-14
**Seems** like that using i686 kernel has fixed this problem...

---

### Post by yamagami on 2006-04-20
Err, nope. still occurs, though seems like less often.

---

