---
title: "17,1 System Error Pop Up after boot"
date: 2017-05-08
forum: Desktop Environments
---

### Post by scojopa on 2017-05-08
Just installed 17,1 on lenovo t460s
Getting a popup after login and pretty slow boot to desktop assume could be the cause

In dmsg and kernel.log I see this

[  112.648648] fwupd[1954]: segfault at 8 ip 00007fcfbc0fb741 sp 00007ffeafbdb5b0 error 4 in libfu_plugin_synapticsmst.so[7fcfbc0f6000+7000]

Can anyone help me dig deeper to the cause

I am not experiencing any resources issues. Or performance when using the desktop except the auto-hide of the  launcher does not work. 

Thanks,

---

### Post by ajgreeny on 2017-05-08
Do you mean 17.10 as there is no 17.1, or is that a typo for 17.04?

17.10 is still very much an ongoing process in development, so if that is what you really installed, be prepared for many breakages along the way.

---

### Post by scojopa on 2017-05-08
I know. Was just asking for some insight. Do you think more productive to enter as a bug?

---

### Post by ajgreeny on 2017-05-09
So which version is it; you have still not told us, 17.04 or 17.10?

---

### Post by roborative on 2017-05-10
I'm seeing the same issue with a Lenovo Carbon X1 running 17.04.

Here's a bit more logging info:

```
syslog:May 10 10:27:51 rob-ThinkPad-X1-Carbon-4th dbus[1183]: [system] Activating via systemd: service name='org.freedesktop.fwupd' unit='fwupd.service'
syslog:May 10 10:27:52 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: ignoring add-delay as device usb:00:08 already pending
syslog:May 10 10:27:52 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: ignoring add-delay as device usb:00:04:04 already pending
syslog:May 10 10:27:52 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: ignoring add-delay as device usb:00:04:01:04 already pending
syslog:May 10 10:27:52 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: ignoring add-delay as device usb:00:04:01:01:04 already pending
syslog:May 10 10:27:52 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: ignoring add-delay as device usb:00:04:01:01:01 already pending
syslog:May 10 10:27:55 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: disabling plugin because: failed to coldplug raspberrypi: Raspberry PI firmware updating not supported, no /boot/start.elf
syslog:May 10 10:27:55 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: disabling plugin because: failed to coldplug uefi: UEFI firmware updating not supported
syslog:May 10 10:27:55 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: ignoring add-delay as device ro__sys_devices_pci0000_00_0000_00_14_0_usb2_2_4_2_4_1_2_4_1_1_2_4_1_1_1_0 already pending
syslog:May 10 10:27:55 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: ignoring add-delay as device ro__sys_devices_pci0000_00_0000_00_02_0 already pending
syslog:May 10 10:27:55 rob-ThinkPad-X1-Carbon-4th fwupd[13969]: Unknown board_id 204
syslog:May 10 10:27:55 rob-ThinkPad-X1-Carbon-4th kernel: [88768.501033] fwupd[13969]: segfault at 8 ip 00007fd7479ed741 sp 00007fff7cfd0cb0 error 4 in libfu_plugin_synapticsmst.so[7fd7479e8000+7000]
syslog:May 10 10:27:55 rob-ThinkPad-X1-Carbon-4th systemd[1]: fwupd.service: Main process exited, code=dumped, status=11/SEGV
syslog:May 10 10:27:55 rob-ThinkPad-X1-Carbon-4th systemd[1]: fwupd.service: Unit entered failed state.
syslog:May 10 10:27:55 rob-ThinkPad-X1-Carbon-4th systemd[1]: fwupd.service: Failed with result 'core-dump'.

```

---

### Post by scojopa on 2017-05-10
it as 17.04 I killed it

---

### Post by roborative on 2017-05-11
@scojopa I'm not following you.

---

