---
title: "System wakes up right after suspending"
date: 2009-02-12
forum: General Help
---

### Post by scary_jeff on 2009-02-12
Hi,

My usual way to leave my laptop is just to close the lid and let it go into suspend. Recently this has become unreliable; I come back from work, and the laptop has been on all day. I looked in syslog (I don't know where else to look), and it does show the system going to sleep, but it looks like it instantly wakes up again, but only sometimes. I have included a cut down version of the syslog (it's very long without cutting stuff out):

```
Feb 12 08:48:08 jeff-laptop ntpd[29718]: kernel time sync status change 4001
Feb 12 08:55:05 jeff-laptop kernel: [254847.474406] [drm] Num pipes: 1
Feb 12 08:55:05 jeff-laptop NetworkManager: <info>  Sleeping...
Feb 12 08:55:05 jeff-laptop NetworkManager: <info>  (eth0): now unmanaged
Feb 12 08:55:05 jeff-laptop NetworkManager: <info>  (eth0): device state change$
Feb 12 08:55:05 jeff-laptop NetworkManager: <info>  (eth0): cleaning up...
Feb 12 08:55:05 jeff-laptop NetworkManager: <info>  (eth0): taking down device.
Feb 12 08:55:05 jeff-laptop NetworkManager: <info>  (eth1): now unmanaged
Feb 12 08:55:05 jeff-laptop NetworkManager: <info>  (eth1): device state change$
Feb 12 08:55:05 jeff-laptop NetworkManager: <info>  (eth1): deactivating device$
Feb 12 08:55:05 jeff-laptop kernel: [254848.192091] usb 3-1: USB disconnect, ad$
Feb 12 08:55:05 jeff-laptop kernel: [254848.194591] btusb_intr_complete: hci0 u$
Feb 12 08:55:06 jeff-laptop bluetoothd[5136]: HCI dev 0 down
Feb 12 08:55:06 jeff-laptop bluetoothd[5136]: Unregistered interface org.bluez.$
Feb 12 08:55:06 jeff-laptop bluetoothd[5136]: Unregistered interface org.bluez.$
Feb 12 08:55:06 jeff-laptop bluetoothd[5136]: Unregistered interface org.bluez.$
Feb 12 08:55:06 jeff-laptop bluetoothd[5136]: Adapter /org/bluez/hci0 has been $
Feb 12 08:55:06 jeff-laptop bluetoothd[5136]: Stopping security manager 0
Feb 12 08:55:06 jeff-laptop kernel: [254848.200618] btusb_send_frame: hci0 urb $
Feb 12 08:55:06 jeff-laptop NetworkManager: <info>  eth1: canceled DHCP transac$
Feb 12 08:55:06 jeff-laptop NetworkManager: <WARN>  check_one_route(): (eth1) e$
Feb 12 08:55:06 jeff-laptop avahi-daemon[4605]: Withdrawing address record for $
Feb 12 08:55:06 jeff-laptop avahi-daemon[4605]: Leaving mDNS multicast group on$
Feb 12 08:55:06 jeff-laptop avahi-daemon[4605]: Interface eth1.IPv4 no longer r$
Feb 12 08:55:06 jeff-laptop NetworkManager: <info>  (eth1): cleaning up...
Feb 12 08:55:06 jeff-laptop NetworkManager: <info>  (eth1): taking down device.
Feb 12 08:55:06 jeff-laptop avahi-daemon[4605]: Withdrawing address record for $
Feb 12 08:55:06 jeff-laptop bluetoothd[5136]: HCI dev 0 unregistered
Feb 12 08:55:06 jeff-laptop bluetoothd[5136]: Unregister path: /org/bluez/hci0
Feb 12 08:55:07 jeff-laptop kernel: [254849.741393] PM: Syncing filesystems ...$
Feb 12 08:55:07 jeff-laptop kernel: [254849.745511] PM: Preparing system for me$
Feb 12 08:55:27 jeff-laptop kernel: <0104140>] work_notifysig+0x13/0x23
Feb 12 08:55:27 jeff-laptop kernel: [254869.758391]  =======================
Feb 12 08:55:27 jeff-laptop kernel: [254869.758393] hald-addon-in D c02e5cc6   $
Feb 12 08:55:27 jeff-laptop kernel: [254869.758397]        f6ba5ebc 00000086 f6$
Feb 12 08:55:27 jeff-laptop kernel: [254869.758404]        f6ba5edc 00000001 f6$


...

Feb 12 08:55:28 jeff-laptop kernel: [254869.767494]   .rt_time                 $
Feb 12 08:55:28 jeff-laptop kernel: [254869.767496]   .rt_runtime              $
Feb 12 08:55:28 jeff-laptop kernel: [254869.767500]
Feb 12 08:55:28 jeff-laptop kernel: [254869.767501] runnable tasks:
Feb 12 08:55:28 jeff-laptop kernel: [254869.767502]             task   PID     $
Feb 12 08:55:28 jeff-laptop kernel: [254869.767504] ---------------------------$
Feb 12 08:55:28 jeff-laptop kernel: [254869.767524] R     pm-suspend 30264  260$
Feb 12 08:55:28 jeff-laptop kernel: [254869.767532]
Feb 12 08:55:28 jeff-laptop kernel: [254869.767574]  cifsd
Feb 12 08:55:28 jeff-laptop kernel: [254869.767602]
Feb 12 08:55:28 jeff-laptop kernel: [254869.767604] Restarting tasks ... done.
Feb 12 08:55:28 jeff-laptop anacron[30419]: Anacron 2.3 started on 2009-02-12
Feb 12 08:55:28 jeff-laptop anacron[30419]: Will run job `cron.weekly' in 10 mi$
Feb 12 08:55:28 jeff-laptop anacron[30419]: Jobs will be executed sequentially
Feb 12 08:55:29 jeff-laptop NetworkManager: <info>  Waking up...
Feb 12 08:55:29 jeff-laptop NetworkManager: <info>  (eth0): now managed

```

How do I stop this happening? Is it a cron job that is waking the system up? If so, I would be happy to simply block cron from waking the system as a solution.

[edit] oh sorry, it's ubuntu 8.10 32 bit [/edit]

Cheers

---

### Post by scary_jeff on 2009-02-18
Any thoughts on this? I know it's not the 'lid is closed' button, because the screen isn't turned on. How could the machine end up not being in suspend with the lid closed, when the option to do so is set?

---

### Post by scary_jeff on 2009-02-25
I did a clean install for another reason, and this problem is still present. The monitor is still turned off when I return to the PC, but it's still come back out of suspend only moments after entering it.
This must be due to some update since 8.10 release, does nobody have an idea? :(

---

### Post by scary_jeff on 2009-02-27
Well I made some progress. I noticed that the problem was only happening in the mornings. The difference was that in the morning, my mythtv backend was not switched on, and so its shared folder that I was mounting on boot of the laptop was not found.
This turned out to be a kernel bug: [http://bugzilla.kernel.org/show_bug.cgi?id=11050](http://bugzilla.kernel.org/show_bug.cgi?id=11050)
The bug is fixed in the latest kernel, but I don't want to run 9.04 alpha, so I'll have to wait until 9.04 release.

---

### Post by Yellow Pasque on 2009-02-27
You may also be able to fix it if you have an option in your BIOS to disable the PC from waking on LAN activity.

---

