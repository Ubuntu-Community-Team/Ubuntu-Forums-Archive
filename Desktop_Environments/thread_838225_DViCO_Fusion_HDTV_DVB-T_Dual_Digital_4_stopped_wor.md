---
title: "DViCO Fusion HDTV DVB-T Dual Digital 4 stopped working (ubuntu 2.6.24-19)"
date: 2008-06-23
forum: Desktop Environments
---

### Post by tc7 on 2008-06-23
DViCO Fusion HDTV DVB-T Dual Digital 4 stopped working (ubuntu 2.6.24-19)

I've been running Hardy as a media center pc for the past few months (GIGABYTE GA-P35-DS3P, Q6600 core2 quad).

The only issues I've had relate to drivers for display (NVIDIA GIGABYTE 8600GTS 512MB) and digital TV card (DViCO Fusion HDTV DVB-T Dual Digital 4).

To configure MythTV I followed the excellent guide at: [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)

Normally when a new kernel update comes down I have to:
a) recompile NVidia driver (currently using: NVIDIA-Linux-x86-173.14.05-pkg0.run)
b) recompile DVB driver. Download xc-test-d4f7804a393c.tar.gz from: ([http://linuxtv.org/hg/~pascoe/xc-test/rev/d4f7804a393c]("http://linuxtv.org/hg/~pascoe/xc-test/rev/d4f7804a393c"))

I extracted the above archive to: <my driver directory>/dvico/xc-test-d4f7804a393c

I tried this for kernel update 2.6.24-19-generic and modprobe terminates abnormally on boot. 

I tried the following:
  make clean
  make
  sudo make install
  shutdown
  power off
  reboot

On boot modprobe would crash (unexpected exit) and pause the boot process for a couple of minutes. After login I would only have a single adapter in /dev/dvb/, and MythTV backend would hang trying to enumerate either dvb tuner.

I tried this a number of times including:
make rminstall, make distclean, make all, etc.:confused:

Here's (a typical) kernel log showing DVB driver load failure:
Jun 23 08:26:01 s2gpvr kernel: [   41.618890] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
Jun 23 08:26:01 s2gpvr kernel: [   41.639692] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000370
Jun 23 08:26:01 s2gpvr kernel: [   41.639695] printing eip: f8b25bd9 *pde = 00000000
Jun 23 08:26:01 s2gpvr kernel: [   41.639698] Oops: 0000 [#1] SMP
Jun 23 08:26:01 s2gpvr kernel: [   41.639700] Modules linked in: tuner_xc2028 snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_all
Jun 23 08:26:01 s2gpvr kernel: [   41.639731]
Jun 23 08:26:01 s2gpvr kernel: [   41.639733] Pid: 3687, comm: modprobe Tainted: P        (2.6.24-19-generic #1)
Jun 23 08:26:01 s2gpvr kernel: [   41.639734] EIP: 0060:[<f8b25bd9>] EFLAGS: 00010206 CPU: 0
Jun 23 08:26:01 s2gpvr kernel: [   41.639738] EIP is at xc2028_attach+0x139/0x220 [tuner_xc2028]
Jun 23 08:26:01 s2gpvr kernel: [   41.639740] EAX: 00000080 EBX: f8b2a2fc ECX: ffffffff EDX: 00000200
Jun 23 08:26:01 s2gpvr kernel: [   41.639741] ESI: f8b2838c EDI: f773eddc EBP: f6d19d68 ESP: f6d19d38
Jun 23 08:26:01 s2gpvr kernel: [   41.639743]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jun 23 08:26:01 s2gpvr kernel: [   41.639745] Process modprobe (pid: 3687, ti=f6d18000 task=f7264000 task.ti=f6d18000)
Jun 23 08:26:01 s2gpvr kernel: [   41.639746] Stack: 00000000 f6c00724 f6c00070 f6c00760 f6c00000 f773ec04 f6c00724 f6c00070
Jun 23 08:26:01 s2gpvr kernel: [   41.639751]        f6c00760 f6c00000 f8a7d1af f8a7e7f3 f6c0055c 00000061 f6c00000 00000000
Jun 23 08:26:01 s2gpvr kernel: [   41.639755]        f8a7ded0 f6c00724 f8a6e013 f6c00724 f6c00070 f6c00760 f6c00724 f8a6d8cd
Jun 23 08:26:01 s2gpvr kernel: [   41.639759] Call Trace:
Jun 23 08:26:01 s2gpvr kernel: [   41.639763]  [<f8a7d1af>] cxusb_dvico_xc3028_tuner_attach+0x4f/0xd0 [dvb_usb_cxusb]
Jun 23 08:26:01 s2gpvr kernel: [   41.639769]  [<f8a7ded0>] dvico_bluebird_xc2028_callback+0x0/0xb0 [dvb_usb_cxusb]
Jun 23 08:26:01 s2gpvr kernel: [   41.639774]  [<f8a6e013>] dvb_usb_adapter_frontend_init+0x73/0x100 [dvb_usb]
Jun 23 08:26:01 s2gpvr kernel: [   41.639780]  [<f8a6d8cd>] dvb_usb_device_init+0x3ad/0x630 [dvb_usb]
Jun 23 08:26:01 s2gpvr kernel: [   41.639789]  [<f8a7d108>] cxusb_probe+0xb8/0x110 [dvb_usb_cxusb]
Jun 23 08:26:01 s2gpvr kernel: [   41.639793]  [<f88a95d9>] usb_probe_interface+0xb9/0x140 [usbcore]
Jun 23 08:26:01 s2gpvr kernel: [   41.639809]  [driver_probe_device+0x88/0x190] driver_probe_device+0x88/0x190
Jun 23 08:26:01 s2gpvr kernel: [   41.639814]  [scsi_mod:kobject_uevent_env+0xf0/0x27d0] kobject_uevent_env+0xf0/0x3d0
Jun 23 08:26:01 s2gpvr kernel: [   41.639819]  [__driver_attach+0x9e/0xa0] __driver_attach+0x9e/0xa0
Jun 23 08:26:01 s2gpvr kernel: [   41.639823]  [scsi_mod:bus_for_each_dev+0x3b/0xe0] bus_for_each_dev+0x3b/0x60
Jun 23 08:26:01 s2gpvr kernel: [   41.639828]  [usbcore:driver_attach+0x16/0x2b0] driver_attach+0x16/0x20
Jun 23 08:26:01 s2gpvr kernel: [   41.639830]  [__driver_attach+0x0/0xa0] __driver_attach+0x0/0xa0
Jun 23 08:26:01 s2gpvr kernel: [   41.639833]  [bus_add_driver+0x8a/0x1e0] bus_add_driver+0x8a/0x1e0
Jun 23 08:26:01 s2gpvr kernel: [   41.639838]  [<f88a911e>] usb_register_driver+0x8e/0x110 [usbcore]
Jun 23 08:26:01 s2gpvr kernel: [   41.639852]  [<f882d018>] cxusb_module_init+0x18/0x35 [dvb_usb_cxusb]
Jun 23 08:26:01 s2gpvr kernel: [   41.639855]  [usbcore:blocking_notifier_call_chain+0x17/0x20] blocking_notifier_call_chain+0x17/0x20
Jun 23 08:26:01 s2gpvr kernel: [   41.639860]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Jun 23 08:26:01 s2gpvr kernel: [   41.639872]  [<c0136330>] msleep+0x0/0x20
Jun 23 08:26:01 s2gpvr kernel: [   41.639878]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Jun 23 08:26:01 s2gpvr kernel: [   41.639884]  =======================
Jun 23 08:26:01 s2gpvr kernel: [   41.639885] Code: 85 d4 00 00 00 8b 7c 24 14 be c0 82 b2 f8 b9 33 00 00 00 81 c7 0c 01 00 00 f3 a5 8b 53
Jun 23 08:26:01 s2gpvr kernel: [   41.639907] EIP: [<f8b25bd9>] xc2028_attach+0x139/0x220 [tuner_xc2028] SS:ESP 0068:f6d19d38
Jun 23 08:26:01 s2gpvr kernel: [   41.639912] ---[ end trace c15af9cb08dfd1cc ]---
J

All to no avail. Eventually I decided to try booting with the slightly older 2.6.24.18-generic kernel and after:
  cd <my driver directory>/dvico/xc-test-d4f7804a393c
  make clean
  make
  sudo make install
  shutdown
  power off
  reboot

Works fine again.:)

I hope this saves some frustration for someone else.

I'm still none the wiser as to why the 2.6.24.19 kernel causes the problem though. Any ideas anyone?

---

