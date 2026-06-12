---
title: "USB 2.0 on Dell Precision 690 in Hardy"
date: 2008-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cycletronic on 2008-05-19
Hello,

I have not been able to get USB 2.0 to work on a dell precision 690 in Dapper, Gutsy or Hardy (and now I am only interested in Hardy).  If I remove ehci_hcd, then everything functions at the 1.1 level, but I have just now run into a situation where I have used up all of the bandwidth of the 1.1 channel.  The situation for the curious is at least 2 webcams, a usb-serial converter, and a Swissranger ranging camera all on the same hub (at a distance from the computer), and the hub connecting to the computer.  The hub is 2.0 capable.  As a workaround, I might be able to get several usb-extension cables and connect each device to a separate port on the computer, but I would like to solve this problem anyway.

I'm not ultra-savvy with these kinds of problems, but I do have limited skill.  All of my searches have come up empty, so I ask here.

In gnome-device-manager, there is a node for USB EHCI Controller with this information:
Model: 631xESB/632xESB/3100 Chipset EHCI USB2 Controller
Vendor: Intel Corporation (Dell)
Connection: PCI (Peripheral Component Interconnect)

When I enable ehci_hcd, the output from dmesg is like the following:
```
[ 2160.411360] usb 5-4: new high speed USB device using ehci_hcd and address 119

[ 2160.898144] usb 5-4: new high speed USB device using ehci_hcd and address 121

[ 2162.510120] usb 5-4: new high speed USB device using ehci_hcd and address 3

[ 2162.999051] usb 5-4: new high speed USB device using ehci_hcd and address 5

[ 2163.296158] usb 5-4: new high speed USB device using ehci_hcd and address 6

[ 2163.782944] usb 5-4: new high speed USB device using ehci_hcd and address 8


```

Note that the address wraps around.  This continues in an infinite loop, and the devices never connect.  Any 1.1 devices, such as the keyboard and mouse, connect fine as long as they are not on the hub, but anything that wants 2.0 connectivity fails.

I have tried plugging the hub and other devices into all of the ports on the computer to no avail.  Let me know if there is any info that would be useful to you in diagnosing this problem.

Can somebody point me to some resources or give some kind of idea of things to try?

Many thanks!

---

### Post by cycletronic on 2008-05-20
As I was playing around with this some more, I paid more attention to the dmesg output upon modprobe ehci_hcd.  Here's the output that happens, all relevant to the modprobe:
```

[52476.507689] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 18

[52476.507706] PCI: Setting latency timer of device 0000:00:1d.7 to 64

[52476.507709] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[52476.507739] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5

[52476.511638] ehci_hcd 0000:00:1d.7: debug port 1

[52476.511645] PCI: cache line size of 32 is not supported by device 0000:00:1d.7

[52476.511654] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xff980800

[52476.526756] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[52476.526910] usb usb5: configuration #1 chosen from 1 choice

[52476.526935] hub 5-0:1.0: USB hub found

[52476.526941] hub 5-0:1.0: 8 ports detected


```

I'm curious about the latency timer and cache line size... could those have any effect on usb 2.0 functioning?

---

