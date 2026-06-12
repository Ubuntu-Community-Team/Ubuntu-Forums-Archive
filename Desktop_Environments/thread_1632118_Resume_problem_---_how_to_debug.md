---
title: "Resume problem --- how to debug?"
date: 2010-11-27
forum: Desktop Environments
---

### Post by kohsuke on 2010-11-27
I have a desktop system (P55-USB3 + Core i7 + Ubuntu 10.10) that fails to suspend/resume from memory. So I'm trying to diagnose the problem.

The first obstacle was easy enough --- when I put the system to sleep to memory, the computer comes back alive right away. A look at /var/log/kern.log revealed that one USB device (usb10) failed to suspend, and from there I was able to pin it down to the USB3 controller in the BIOS. Disabled that and this problem disappeared.

Now, I'm stuck with the second obstacle. The computer successfully goes into the suspend mode, but it hangs during resume. The monitor doesn't get any video signal, and it fails to respond to ping (netconsole doesn't work either.) After a forced reboot (that involves unplugging the power cable), /var/log/kern.log doesn't contain any interesting entries.

All the pm_test modes from freezer to core succeed (I followed [http://www.mjmwired.net/kernel/Documentation/power/basic-pm-debugging.txt](http://www.mjmwired.net/kernel/Documentation/power/basic-pm-debugging.txt))

I've also tried pm_trace ([https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)) but again kern.log nor dmesg contains anything after the suspend. Either the write didn't survive the forced power off, or the resume is failing even before that.

The motherboard doesn't have a serial port nor firewire, so getting kernel logs through them is not a possibility, either.

How do you go about diagnosing any further? Any help would be greatly appreciated.

---

### Post by madengineer on 2011-01-30
I wonder if a USB-serial adapter would work? It looks like there may be some support for this: [http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/configure-kernel.html]("http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/configure-kernel.html"). If I understand it right, you would boot with the option console=ttyUSB0 added, and see what it spits out. Hopefully it's not dependent on a module that might be unloaded when the fatal error happens.

I actually have the same motherboard (I assume you mean the Gigabyte GA-P55-USB3), a Core i7-875k, and an NVidia 8800GT. I ran into the same "immediate wakeup" problem because of the USB3 controller, which I discovered is because the module that drives it (xhci_hcd) does not support sleep in kernel versions before 2.6.37. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998"). In my case, running ```
sudo modprobe -r xhci_hcd
``` allowed sleep and successful wakeup, so since I have no USB3 devices, I've added xhci_hcd to /etc/modprobe.d/blacklist.conf for now. This is supposed to let the ports keep working but as USB 2.0.

---

### Post by kohsuke on 2011-01-30
Thanks for the information.

I wonder if there's a way to connect two PCs via some kind of "cross" USB cable so that they can talk to each other as if it's a serial cable. Because I don't own any computer with a serial port, going with USB-serial adapter means I need to buy 2 of them plus the cross serial cable.

I'll experiment if enabling the USB3 controller back in the BIOS and blacklisting xhci_hcd would help. After the controller is disabled, the module is no longer loaded, so I doubt if it makes a difference, but I guess it's worth a try.

---

### Post by Zomby Woof on 2011-02-01
I have the same issue sitth 10.04 and same motherboard & I7-870 cpu.
I disable the USB3 support, like you did and now when I resume from suspend it hangs but if I press the reset button it comes right up. So, suspend to ram is working but something is not right after it powers down.

---

