---
title: "gpilotd pilot sync broken in dapper"
date: 2006-06-02
forum: Desktop Environments
---

### Post by wastrel on 2006-06-02
I had this working fine in breezy, installed dapper today, and now I can't sync my clie to evolution reliably.  

This was a fresh dapper install, not an upgrade.  gpilotd seems to hang, crash, and sometimes even work when I try to sync.

jpilot works just fine, and reliably, so it's not a pilot-link or a USB issue.  I can watch in /var/log/messages as gpilotd crashes or just hangs, or works (rarely).

I'm using a Sony Clie PEG-TH55, with Palm OS 5.2.1.

Any ideas what to do to get this working reliably?

Here's a log of a crash:

=== Here I connect the clie to the sync cable and hit the hotsync button

Jun  2 18:22:45 localhost kernel: [4295157.501000] usb 2-2: new full speed USB device using uhci_hcd and address 6
Jun  2 18:22:45 localhost kernel: [4295157.634000] visor 2-2:1.0: Sony Clie 5.0 converter detected
Jun  2 18:22:45 localhost kernel: [4295157.634000] usb 2-2: Sony Clie 5.0 converter now attached to ttyUSB0
Jun  2 18:22:45 localhost kernel: [4295157.634000] usb 2-2: Sony Clie 5.0 converter now attached to ttyUSB1

=== So far so good, got some USB ports set up and attached, but the sync process on the Palm OS side just hangs.  It seems gpilotd has decided to crash:

Jun  2 18:22:56 localhost kernel: [4295168.144000] f0e33724
Jun  2 18:22:56 localhost kernel: [4295168.144000] PREEMPT
Jun  2 18:22:56 localhost kernel: [4295168.144000] Modules linked in: visor usbserial rfcomm l2cap bluetooth nvram uinput ppdev radeon drm speedstep_centrino cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi ibm_acpi hotkey dev_acpi container button acpi_sbs
battery i2c_acpi_ec i2c_core ac ipv6 dm_mod md_mod lp af_packet arc4 ieee80211_crypt_wep pcmcia e1000 joydev tsdev ipw2200 ieee80211 ieee80211_crypt parport_pc parport yenta_socket rsrc_nonstatic pcmcia_core irtty_sir sir_dev nsc_ircc irda crc_ccitt snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer hw_random snd soundcore rtc floppy snd_page_alloc psmouse shpchp pci_hotplug serio_raw pcspkr intel_agp agpgart evdev ext3 jbd ide_generic ehci_hcd uhci_hcd usbcore ide_cd cdrom ide_disk piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jun  2 18:22:56 localhost kernel: [4295168.144000] CPU:    0
Jun  2 18:22:56 localhost kernel: [4295168.144000] EIP:    0060:[pg0+815830820/1069368320]    Not tainted VLI
Jun  2 18:22:56 localhost kernel: [4295168.144000] EFLAGS: 00010246   (2.6.15-23-386)
Jun  2 18:22:56 localhost kernel: [4295168.144000] EIP is at serial_chars_in_buffer+0x14/0x80 [usbserial]
Jun  2 18:22:56 localhost kernel: [4295168.144000] eax: 00000000   ebx: 00000000   ecx: dd83e5c0   edx: e0633e40
Jun  2 18:22:56 localhost kernel: [4295168.144000] esi: 00000000   edi: dd83e5c0   ebp: 00000007   esp: e22f3ebc
Jun  2 18:22:56 localhost kernel: [4295168.144000] ds: 007b   es: 007b   ss: 0068
Jun  2 18:22:56 localhost kernel: [4295168.144000] Process gpilotd (pid: 5024, threadinfo=e22f2000 task=e223c030)
Jun  2 18:22:56 localhost kernel: [4295168.144000] Stack: ddaff000 c022428c ddaff000 ddaff000 dd83e5c0 ddaff00c c021fdd9 ddaff000
Jun  2 18:22:56 localhost kernel: [4295168.144000]        dd83e5c0 00000000 dd83e5c0 02000000 00000019 c0173bd4 dd83e5c0 00000000
Jun  2 18:22:56 localhost kernel: [4295168.144000]        00000000 0000001a 00000000 e06fc2ac e06fc2b0 e06fc2b4 e06fc2a4 e06fc2a8
Jun  2 18:22:56 localhost kernel: [4295168.144000] Call Trace:
Jun  2 18:22:56 localhost kernel: [4295168.144000]  [normal_poll+316/367] normal_poll+0x13c/0x16f
Jun  2 18:22:56 localhost kernel: [4295168.144000]  [tty_poll+73/112] tty_poll+0x49/0x70
Jun  2 18:22:56 localhost kernel: [4295168.144000]  [do_select+404/896] do_select+0x194/0x380
Jun  2 18:22:56 localhost kernel: [4295168.144000]  [__pollwait+0/176] __pollwait+0x0/0xb0
Jun  2 18:22:56 localhost kernel: [4295168.144000]  [sys_select+516/928] sys_select+0x204/0x3a0
Jun  2 18:22:56 localhost kernel: [4295168.144000]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Jun  2 18:22:56 localhost kernel: [4295168.144000] Code: 68 e7 67 e3 f0 e8 dd 8f 2e cf 83 c4 0c eb e0 90 8d b4 26 00 00 00 00 53 8b 44 24 08 8b 98 74 09 00 00 a1 04 a6 e3 f0 85 c0 75 1c <8b> 83 84 00 00 00 85 c0 74 31 8b 03 8b 40 04 89 5c 24 08 8b 88

=== Well, that was fun - here's where I disconnect the thing to try again.

Jun  2 18:24:49 localhost kernel: [4295168.144000]  <6>usb 2-2: USB disconnect, address 6
Jun  2 18:24:49 localhost kernel: [4295281.295000] visor 2-2:1.0: device disconnected

---

### Post by murex on 2006-06-04
Similar problem here, can't sync my Tungsten E2 with gdpilot.

---

### Post by tc10b on 2006-06-04
I can't sync my m515 either :(

---

### Post by matthew on 2006-06-04
Palm m130 here...also unable to sync.

---

### Post by wastrel on 2006-06-04
Seems there's a bug in about this - hopefully a fix soon...

[https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653](https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653)

I am getting better performance, but still some hangs and crashes, after installing the replacement gnome-pilot and libgnome-pilot packages here (get the right ones for your architecture):

[http://daniel.holba.ch/ubuntu/gnome-pilot/](http://daniel.holba.ch/ubuntu/gnome-pilot/)

---

### Post by supermarchino on 2006-07-11
these packages worked for me for sync with evolution on my clié tj37. grazie.

---

### Post by matthew on 2006-07-11
> **wastrel said:**
> Seems there's a bug in about this - hopefully a fix soon...

[https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653](https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653)

I am getting better performance, but still some hangs and crashes, after installing the replacement gnome-pilot and libgnome-pilot packages here (get the right ones for your architecture):

[http://daniel.holba.ch/ubuntu/gnome-pilot/](http://daniel.holba.ch/ubuntu/gnome-pilot/)That is definitely an improvement. Thank you for the info! It still isn't consistent, though. I was glad to read the bug page where they discuss the problem and show what is being done to try to fix it. We may just need to wait until kernel 2.6.17 is available for Dapper or until the next upgrade.

---

### Post by shroomling on 2006-09-15
> **wastrel said:**
> Seems there's a bug in about this - hopefully a fix soon...

[https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653](https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653)

I am getting better performance, but still some hangs and crashes, after installing the replacement gnome-pilot and libgnome-pilot packages here (get the right ones for your architecture):

[http://daniel.holba.ch/ubuntu/gnome-pilot/](http://daniel.holba.ch/ubuntu/gnome-pilot/)

Yes, I have the same issue.  I started the daemon manually from the console and managed to find that it was crashing when backing up "ImgFile-Foto" - upon further investigation it turns out this is a [known problem]("http://www.pilot-link.org/book/print/97").  The only way to resolve the crash is to work around it.  Basically you need to disable your backup conduit, the rest should work fine.  You can do a manual backup and specify exclusions to avoid the crash.  See the following link for more detailed information:
[http://cpbotha.net/weblogs/cpbotha/archives/000929.html]("http://cpbotha.net/weblogs/cpbotha/archives/000929.html")

---

