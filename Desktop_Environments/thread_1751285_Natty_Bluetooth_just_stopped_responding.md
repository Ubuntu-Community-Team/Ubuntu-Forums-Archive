---
title: "Natty Bluetooth just stopped responding"
date: 2011-05-06
forum: Desktop Environments
---

### Post by encefalocardia on 2011-05-06
Moments ago I was using, as always, my bluetooth devices on my Macbookpro4,1 and suddenly the icon disappeared and my devices disconected. I thought the daemon just crashed so I tried to restart but I got a command not found error. I opened the Bluetooth preference dialog and it said that no bluetooth device was present on the system. I restarted and same result.

As a last measure I completely pruged bluez and gnome.bluetooth and reinstalled. Same result.

Any ideas?

---

### Post by encefalocardia on 2011-05-06
Please guys. No one?

---

### Post by encefalocardia on 2011-05-06
I think I found out the problem (or at least part of it). After uninstalling all the bluetooth components from synaptic, purging their config files and restarting the system, there's still a bluetooth zombie process running, with a do_exit on channel. Is there anyway to kill this?

---

### Post by kostkon on 2011-05-06
If it's a user space process, just use the system monitor to kill it.

Next time it happens, you could try doing a hardware reset on your bluetooth adapter/device:
```
sudo hciconfig hci0 reset
```

---

### Post by encefalocardia on 2011-05-06
Im having a No such device error using that command. I guess its time to accept that my bluetooth internal device died, right?

---

### Post by B Crowther on 2011-05-06
> **encefalocardia said:**
> Im having a No such device error using that command. I guess its time to accept that my bluetooth internal device died, right?
Have you tried sudo restart service bluetooth?

Seems to be a common Natty problem: restart service is working for me.

Check: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/762964](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/762964)

---

### Post by JunCTionS on 2011-05-07
> **B Crowther said:**
> Have you tried sudo restart service bluetooth?

Seems to be a common Natty problem: restart service is working for me.

Check: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/762964](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/762964)


Thank you very much :)

---

### Post by yurx cherio on 2011-05-10
Neither restarting the service nor the device worked for me. The bluetooth seems to be working but I can not longer browse files on my device. I used to be able to browse file on my Nokia via bluetooth. I Natty I could pair it, I marked the computer as a trusted device on the phone but still can't browse files on the phone.

---

