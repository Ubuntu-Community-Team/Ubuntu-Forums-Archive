---
title: "NVIDIA GeForce GTX 560 64 bit driver installer"
date: 2014-03-25
forum: Gaming &amp; Leisure
---

### Post by docmax2 on 2014-03-25
Hell, I am a newbee to this O/S. I am running Windows 7 64 bit and Ubuntu 13.10 on the same HD, gaming computer. NVIDIA comes up with a driver that has .run and i think i need a installer. I am not into writing scripts to install something. All and any help would be welcomed.

Thanks,  Max

---

### Post by oldrocker99 on 2014-03-25
OK, here's a step-by-step way to install it:

1. Open a terminal and type:
```
sudo apt-get install dkms
``` (This keeps you from having to reinstall the driver after a kernel update)

2. Hit CTRL-ALT-F1 and log in as you normally would

3. Type:
```
sudo service ldm stop
``` Note: if you get a "no service named ldm found," try using lightdm, kdm, or gdm instead. You're looking for a "service ldm stopped, waiting" response.

4. Now cd to the folder where your nVidia .run file is and type
```
sudo sh NIVIDIA*.run[code]

And it **SHOULD** install. Afterwards, type:
[code]sudo service ldm start
```

You can then press CTRL-ALT-F7 to get back to the desktop. I would reboot (one of the few times you need to reboot using Ubuntu). Then go to NVIDIA Settings and set your desired resolution, etc.

Good luck! And please post here if it worked, or if it didn't.

And welcome to Ubuntu!

---

### Post by MikeCyber on 2014-03-26
Also make sure to have the kernel sources installed before running the *.run. After that I would simply reboot: sudo reboot

---

### Post by oldrocker99 on 2014-03-26
> **MikeCyber said:**
> Also make sure to have the kernel sources installed before running the *.run. After that I would simply reboot: sudo reboot

Absolutely. You do need to have the kernel sources installed, and that was important to add.

---

