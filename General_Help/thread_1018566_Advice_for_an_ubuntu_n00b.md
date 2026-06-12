---
title: "Advice for an ubuntu n00b"
date: 2008-12-22
forum: General Help
---

### Post by jonnojonno999 on 2008-12-22
Hi, i just installed ubuntu on my secondary system and everythings working great apart from my networking. I have a belkin wireless network utility (connected via usb) that i dont think works with linux, and the only ethernet ports in my house are occupied by my dads computer, any advice?

Cheers
Jon

---

### Post by bluefrog on 2008-12-22
belkin should work with ndiswrapper

sudo mkdir /home/windrivers
sudo cp /path/to/driver.inf /home/windrivers
sudo cp /path/to/driver.sys /home/windrivers
sudo ndiswrapper -i /home/windrivers/driver.inf

	to check

sudo ndiswrapper -l

	to load the kernel module

sudo modprobe ndiswrapper

	to load the kernel module on boot

sudo ndiswrapper -m  (alias modprobe)
echo ndiswrapper | tee -a /etc/modules  (boot activation)

---

