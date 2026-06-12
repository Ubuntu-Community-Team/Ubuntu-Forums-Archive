---
title: "Setting up Network in Ubuntu"
date: 2005-05-24
forum: Desktop Environments
---

### Post by CustomX on 2005-05-24
Hello guys, im very new to the whole ubuntu / linux thing :P. when i installed ubuntu i didnt worry about network config i thought i could do it in ubuntu after its finished :). Now im wondering is there a step by step instructions to set it up in Ubuntu?, 
I have currently got Windows XP Professional on my computer connected to 1.5/256mb ADSL using a Billion BIPAC 5102 Modem/Router. I Have my computer as the host and my dads (Ubuntu machine) into the router. Now im just wondering how i go about setting up the network for internet access? Also i am running a Realtek NIC card in the ubuntu machine.

Cheers,
DeAN

---

### Post by ola on 2005-05-24
You can use the "System / Administration / Networking" tool available from the gnome panel. 

You can activate the network card there and set static or dynamic IP address.

If you want to take a look at the config file see /etc/networking/interfaces if you want help for that you can use the man-pages for the interface file (man interfaces) (you quit the manpage with q)

Good luck!

---

### Post by CustomX on 2005-05-24
Hey guys, my network card is activated and i have tried both running a static ip and DHCP but still unable to work.ive ran ifocnfig and have an ip. my gateway is 192.168.1.254 and my ip for my windows machine is 192.168.1.100. ive set it in the ubuntu machien to 192.168.1.150 and the DNS and gateway to 192.168.1.254

any ideas?

ive checked gateway and stuff with route -n and it seems ok. but still cant connect :S

---

### Post by lorap on 2005-05-25
hi buddy!
to integrate with windows you've install "samba", "samba-common" and "samba-doc" of course (via synaptic package manager).
all information you'll need read here:

[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=printer+sharing@gmail.com](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=printer+sharing@gmail.com) 

hope it'd help you as it did to a friend of mine.
pavel

---

