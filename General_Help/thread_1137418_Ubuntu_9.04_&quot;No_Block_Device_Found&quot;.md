---
title: "Ubuntu 9.04 &quot;No Block Device Found&quot;"
date: 2009-04-25
forum: General Help
---

### Post by Syntaxhead on 2009-04-25
Hello,

I just upgraded Ubuntu 8.10 to Ubuntu 9.04. When I select Ubuntu from the GRUB bootloader, I get a message "No Block Device Found" four times then get the Busybox. At this point I have to type *[COLOR="DarkRed"]dmraid -ay[/COLOR]* then I have to type [COLOR="DarkRed"]*exit*[/COLOR]. Then I can log in. How can I fix this so I log into Ubuntu straight from the bootloader?


My PC configuration is as follows:
Intel DP35DP
Quad Core Processor
8GB DDR2 RAM
Nvidia 8800 GTS

---

### Post by nikgare on 2009-04-26
The file you need to edit is /bnoot/grub/menu.lst

You should just be able to put extra options on to the end of the kernel line, I believe.

---

### Post by fermulator on 2009-05-05
This I believe is related to bug [315375]("https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/315735").

Does it work for you now with latest updates?

---

### Post by whiteguy1104 on 2009-07-20
i have the same problem exept im not using raid and i dont know any way to fix it

---

### Post by fermulator on 2009-07-25
> **whiteguy1104 said:**
> i have the same problem exept im not using raid and i dont know any way to fix it

What *are* you using then?

---

