---
title: "Samsung bluetooth file exchange (and a compliment :p)"
date: 2005-06-23
forum: Desktop Environments
---

### Post by sickdude on 2005-06-23
ok im having some troubles with the bluetooth file exchange

i have a samsung D500 with bluetooth and i want to get the pics on my pc using the bluetooth protocol.

i have apt'ed bluez and all the other bluetooth thingies but i cant seem to send files to my pc or brouws thrue my phone with bluetooth


i got a datacable to but thats not working either so i would like to know more about that to i mean it has to be possible to get inside my phone and get all the pics of of it




ok with these things said i still want to say that ubuntu is a super distro and everything works great, someone i know wanted me to burn some stuff from a usb-stick on a cd so i thought crap now i have to reboot and get all windooows xp and stuff but hey lets try, and it worked directly and i was like yea i use linux and im so cool :P so thnx for that you guys :D  \\:D/

---

### Post by v79 on 2005-06-23
Hey, I've got the same phone and I've got bluetooth working, although I had to change a configuration file by hand... I had to change the file /etc/bluetooth/hcid.conf and change the 'Local device class' to read 

class 0x100100;

You have to use sudo gedit /etc/bluetooth/hcid.conf to edit this file.

From what I understand, this line tells the computer what sort of device your phone is, in this case 0x100100 means something like "general bluetooth device". You might have to restart after making this change, but maybe not.

To send files to your phone, use the command: gnome-obex-send <filename>, To receive files from the phone, I use a program called gnome-obex-server.

Hope this works for you...

Liam D

---

### Post by derrick1985 on 2005-06-23
This worked perfectly for me.

[http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth)

---

