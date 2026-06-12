---
title: "VMWare and USB Printer- releasing ports to host"
date: 2007-03-23
forum: Desktop Environments
---

### Post by frankiethepill on 2007-03-23
If I use VMWare and use the usb printer, I cannot then use the printer from Ubuntu, even if I have released the usb port from the VM options in the vmware program, or even for that matter closed down the vmware program completely. The only way to use the printer again from Ubuntu is to reboot. Is there any way to force Ubuntu to see the usb port again once vmware has released it?

Sadly there is one program I _have_ to use through winders  :(

---

### Post by fjm03 on 2007-03-24
Are you utilizing a VMware player via SPM or a VMware server through a CLI install?

If a server, the following should release the USB controller back to host control:

1) From inside a machine return your mouse to VMware server control w/ Ctrl+Alt
2) Select **Removable Device **on the server's **_V_M **menu.
3) Select** USB Devices**
4) Select [B]Disconnect

[/B]There is also a known issue when utilizing a VMware Server on a 2.6 kernel host: Forcing control of  parport0 (parallel port) to the VMware Server disconnects the **lpmod** (line printer module) on the host kernel. If parport0 is under the control of the VMware Server, before a PP printer can be used on the host, the **lpmod** on the host must be restarted manually through the CLI (Terminal) or the the host must be rebooted.

I am not familiar with the VMware player and haven't utilized a USB printer on a virtual machine/appliance but this same issue my be in  play because a printer is involved. If this is the case, the howtos for checking module status (*modprobe <modulename>*) or a  manual restart of the **lpmod **(*modprobe* *parport_pc && modprobe ppdev*) are on the VMware Server forum.

---

### Post by frankiethepill on 2007-03-25
Thank you for your reply.

>1) From inside a machine return your mouse to VMware server control w/ Ctrl+Alt
>2) Select Removable Device on the server's VM menu.
>3) Select USB Devices
>4) Select Disconnect
doesn't work, so I'll look at your other suggestions, and the VMWare site, which I have looked at briefly but got a bit swamped by technical terms!

---

