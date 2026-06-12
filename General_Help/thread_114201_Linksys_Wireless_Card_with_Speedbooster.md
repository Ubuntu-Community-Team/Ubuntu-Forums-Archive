---
title: "Linksys Wireless Card with Speedbooster"
date: 2006-01-08
forum: General Help
---

### Post by Sopranosmainman on 2006-01-08
Hey guys right now im running off my internal wireless card which kubuntu auto detected... but id rather run off of my Linksis Wireless card.... Can anyone tell me how i can install and activate my card.... the more attention to detail the better as im a newb.... also is there a way to disable my internal card once i get this running. Thanks

---

### Post by Titus A Duxass on 2006-01-08
You need to provide more details about your card, etc.

You should also use the wonderful search mechanism available on this forum.

Do a search for ndiswrapper and have a bit of a read.

---

### Post by Sopranosmainman on 2006-01-08
[QUOTE=Titus A Duxass]You need to provide more details about your card, etc.

You should also use the wonderful search mechanism available on this forum.

Do a search for ndiswrapper and have a bit of a read.[/QUOTE]

I downloaded and installed that and follwed the instructions.... i downloaded the windows drivers as stated... then when i did the command sudo ndiswrapper -i "name".inf, it tells me command not found, but when i check in adept... ndiswrapper is installed! Please Help. I Have a LInksys WPC54GS W/ SPEEDBOSTER wirless card. Thanks

---

### Post by Titus A Duxass on 2006-01-08
"sudo ndiswrapper -i "name".inf, it tells me command not found..."

That means you have not installed ndiswrapper.

What process did you use to install ndiswrapper?

---

### Post by Sopranosmainman on 2006-01-08
adept.... graphical user interface version found undfer K.. System

---

### Post by Titus A Duxass on 2006-01-08
Did your ndiswrapper install give any error messages?

Have you installed the kernel headers and sources?

---

### Post by Sopranosmainman on 2006-01-08
[QUOTE=Titus A Duxass]Did your ndiswrapper install give any error messages?

Have you installed the kernel headers and sources?[/QUOTE]

Dont know what kernel header is... so propbably not then... and im almost positive it was the source i installed

---

### Post by Sopranosmainman on 2006-01-08
OK i uninstalled and reinstalled ndiswrapper, and its finally found it.... now i installed the driver with no problems... but when i did the following:

ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
sh: /etc/modprobe.d/ndiswrapper: Permission denied
joe@Thinkpad:~$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

How do i go arouund fixing this?? Thanks

---

