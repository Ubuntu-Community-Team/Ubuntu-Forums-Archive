---
title: "ubuntu is unable to connect to a peap network"
date: 2009-05-14
forum: General Help
---

### Post by Meow27 on 2009-05-14
[http://ubuntuforums.org/showthread.php?t=1143975](http://ubuntuforums.org/showthread.php?t=1143975)
> **Meow27 said:**
> im trying to connect to a network that is set to a "Student and staff traffic is set to WPA+WPA2 AES+TKIP EAP-MSCHAP v2."

its a self signed certificate. normally on the windows clients, certificate validation is disabled. and there is no option for disabling it on the gnome network manager in ubuntu jaunty.

i have the correct username and pass... etc.[i noticed that no certificates are automatically downloaded to my machine, something i think the windows computers do by defualt.] im also the only one in my school that is using any form of linux, so im alone in this case, 
additionally the tech department is unwilling to buy an annual $500 VeriSign WLAN Server Certificate

go daddy doesn't sell wireless certs for this use

any ideas of how to get around this? 
(note im writing this along with the tech department so my flipping of tenses changes. sorry about that)
continueing from this thread 


ive been getting no replies and i really need solutions!
at this rate im gonna have to switch to windows again! :'(

---

### Post by Meow27 on 2009-05-15
bump

---

### Post by hexanol on 2009-05-15
I don't know if it could help.

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/freeradiuspeapwpasupplicant-653620/#post3206217](http://www.linuxquestions.org/questions/linux-wireless-networking-41/freeradiuspeapwpasupplicant-653620/#post3206217)

---

### Post by Meow27 on 2009-05-18
i dont think it could because the only changeable variable here is the setting on my notebook, again, im dual-booting with windows right now so i can live, but if i cant use ubuntu as my primary OS, that's just a tad bit annoying if ya know what i mean ;)

thanks for *replying *though, i thought i was a loner :P

---

### Post by Meow27 on 2009-05-27
bump

---

### Post by kerry_s on 2009-05-27
[http://narnia.cs.ttu.edu/drupal/node/147](http://narnia.cs.ttu.edu/drupal/node/147)

---

### Post by NoBugs! on 2009-08-28
I noticed there's a new updated version of networkmanager, that might possibly help:
[http://packages.ubuntu.com/search?keywords=network-manager](http://packages.ubuntu.com/search?keywords=network-manager)

This seems to be the easiest way to set up networkmanager with this type of network:
[http://lug.wsu.edu/wireless/peap/ubuntu](http://lug.wsu.edu/wireless/peap/ubuntu)

---

