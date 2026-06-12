---
title: "can no longer see workgroup computer on home network"
date: 2005-12-09
forum: General Help
---

### Post by daedalusman on 2005-12-09
I use to be able to see all the other computers on our home network (these other computers are all windows) but no longer. I have been searching these forums for the last couple of days trying to find a way to fix this and have tried numerous things but to no avail. This came about one day when I needed to restart my computer to use windows for a little while and when I came back to Ubuntu I couldn't initially connect to the internet at all. So I restarted again and once back into Ubuntu I was now able to connect to the internet but no longer could I see the workgroup computers. To my knowledge I didn't change anything concerning my network setup. I really need to get this fix as me and my housemates share files over our network and so now I just feel left out. Can someone please help me with this, let me know if you need some more info.

---

### Post by aclaunch on 2005-12-09
Were you using Samba to connect the various computers? You can check if it's running by doing " ps aux | grep smbd" and "ps aux | grep nmbd". There should be 2 instances of smbd running and 1 of nmbd. If not, do "sudo /usr/sbin/smbd -D" and "sudo /usr/sbin/nmbd -D". Everything should be OK after that but I'm not sure why it didn't survive a reboot.

Good Luck,
Alan

---

### Post by amohanty on 2005-12-09
Is the samba daemon running?

---

### Post by daedalusman on 2005-12-09
[QUOTE=aclaunch]Were you using Samba to connect the various computers? You can check if it's running by doing " ps aux | grep smbd" and "ps aux | grep nmbd". There should be 2 instances of smbd running and 1 of nmbd. If not, do "sudo /usr/sbin/smbd -D" and "sudo /usr/sbin/nmbd -D". Everything should be OK after that but I'm not sure why it didn't survive a reboot.

Good Luck,
Alan[/QUOTE]


Yeah both are running, 2 of smbd and 1 of nmbd, they are running as root, should that be different? When I go to the network folder I see "Windows Network" but when I click on it there is nothing in there. Could be a problem with the router changing my IP address (we use DHCP) and because of that Ubuntu is having some problems seeing the other computers, as their IP's would have been updated as well? Or do you think that it is a local firewall issue? I'm using firestarter though I'm not sure if it's even running currently. I don't know this is really baffling me.

---

### Post by daedalusman on 2005-12-09
[QUOTE=amohanty]Is the samba daemon running?[/QUOTE]


Is there the samba daemon different from smbd and nmbd?

---

### Post by amohanty on 2005-12-09
Nope its the same.. aclaunch's description is correct. Can you use the Places->Connect to Server to view the network shares?

---

