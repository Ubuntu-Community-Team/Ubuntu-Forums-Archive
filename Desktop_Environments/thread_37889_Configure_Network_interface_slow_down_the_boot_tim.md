---
title: "Configure Network interface slow down the boot time"
date: 2005-05-29
forum: Desktop Environments
---

### Post by hyapadi on 2005-05-29
I wonder why my computer boot so slowly. Then I try to cancel the "configuring network interfaces" during boot. The rest of the process went fast. but the "configuring network interface" take a very long time. What should I do to speed up the boot time?

note : I'm using an ethernet card eth0 and wireless card ath0. The wireless card using wpa supplicant.

---

### Post by Peter Alien on 2005-05-29
I have a Cable Modem, and when i boot with it turned off, it takes a good time for the boot to complete, but when i boot with it turned on, it boots very quicky.

With Wireless i really dont know.

---

### Post by kaarel on 2005-06-01
[QUOTE=hyapadi]I wonder why my computer boot so slowly. Then I try to cancel the "configuring network interfaces" during boot. The rest of the process went fast. but the "configuring network interface" take a very long time. What should I do to speed up the boot time?[/QUOTE]

I have the same problem and the same question. I use a laptop and often are not connected to a network. But the boot process attempts to start a network interface. So it spends a lot of time doing so and ultimately still fails because as I said I am not connected to a network. The only solution I know of is to press Ctrl+C during "configuring network interface". Everything else is fast and smooth during boot.

[EDIT]Ok I just found a thread that covers the same topic, gives some quick solutions and also suggestions for better default Ubuntu. See [**Reducing network timeout for offline laptops**]("http://www.ubuntuforums.org/showthread.php?t=31198")[/EDIT]

---

