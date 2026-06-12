---
title: "SATA/USB device name problems..."
date: 2009-04-18
forum: General Help
---

### Post by elli222 on 2009-04-18
This is one very strange problem. It is really hard to explain, so excuse me if i get some terminology wrong.

My problem is that my Only Hard Disk keeps changing sd* device names.

The problem is... My USB mouse!

If i boot the computer without the mouse attached, the SATA disk will be: 
/dev/sda

BUT! if i boot WITH my usb mouse plugged, the SATA Disk will (sometimes) be labeled:
/dev/sdc

This may be because the mouse has some built-in memory, for remembering settings set by the logitech SetPoint software, but this is irrelevent.

The problem: The USB Mouse gets its device name before the sata disk! This screws up configuration files (for hddtemp, or smartd) looking for temprature information and S.M.A.R.T information in a USB mouse!

How can i make the mouse get a device name last, without unplugging it every time i want to boot my computer. ( and replugging it when X loads)

Thanks, elli222

PS: My mouse, for other people experiencing similar problems, is a Logitech G5.

---

### Post by juancarlospaco on 2009-04-18
Use UUID, for this reason has been created UUID, it just like a serial number replacing the short name

---

