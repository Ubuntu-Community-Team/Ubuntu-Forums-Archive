---
title: "Bluetooth off, WiFi on on a M1330n"
date: 2009-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gustavo Narea on 2009-07-10
Hello, everyone.

I have a Dell M1330n running Kubuntu 9.04 and I haven't found a way to disable Bluetooth without disabling WiFi.

I've already tried this at the BIOS level, but from there I can only control a switch that handles **both** WiFi and Bluetooth.

I also tried `sudo /etc/init.d/bluetooth stop`, but it doesn't seem to be what I'm searching for (the Bluetooth LED is still on).

All I want is to have WiFi on and Bluetooth off by default. I want Bluetooth to be on only when I'm using it, not all the time.

How can I do this?

Thanks in advance.

---

### Post by superm1 on 2009-07-10
Install the application smbios-utils.  There is a tool in there for turning off bluetooth only.

---

