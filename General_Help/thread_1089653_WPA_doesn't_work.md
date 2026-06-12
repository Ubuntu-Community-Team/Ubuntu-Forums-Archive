---
title: "WPA doesn't work"
date: 2009-03-07
forum: General Help
---

### Post by malfist on 2009-03-07
When I try to connect to a WPA Personal or Enterprise wireless network for which I know the correct setting (I've set it up on windows many many times), I cannot. Network Manager will say connection... for like 2 or 3 minutes, and then it will ask for the password again.

Any idea what's wrong or how I can fix it?

Thanks.

---

### Post by Hobgoblin on 2009-03-07
> **malfist said:**
> 
Any idea what's wrong or how I can fix it?


Post some more information, such as your wireless card make/model.

---

### Post by Nano_ext3 on 2009-03-07
First, please run the following command in Terminal:

"lspci | grep Network"

Report that information to us so we can better assist you.  You could also try installing the WPA supplicant package, why is very detailed in this thread:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)


Hope this helps, and get back to us if you require further assistance,

Cheers!

-Nano

---

### Post by malfist on 2009-03-08
Sorry I forgot, it's an Intel PRO/Wirelss 3945.
```

00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

The WPASupplicant is installed from the repository, I seem to remember it working before gusty but really hasn't since.

---

### Post by malfist on 2009-03-08
> **Nano_ext3 said:**
> First, please run the following command in Terminal:

"lspci | grep Network"

Report that information to us so we can better assist you.  You could also try installing the WPA supplicant package, why is very detailed in this thread:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)


Hope this helps, and get back to us if you require further assistance,

Cheers!

-Nano

I also have more than one wireless network. I use WPA2 Personal at home, and at school I have a WPA2 Enterprise using PEAP, and that walkthough seems to be geared toward single network use. I've been using NetworkManager.

---

