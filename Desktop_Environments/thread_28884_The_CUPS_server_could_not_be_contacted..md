---
title: "The CUPS server could not be contacted."
date: 2005-04-22
forum: Desktop Environments
---

### Post by Staesys on 2005-04-22
After selecting the "listen for LAN printers" option in "System->Administration->Printing", I get the following message "The CUPS server could not be contacted." everytime I try and change my printing...

I've tried a lot of suggestions I've seen in this forum and through google, and nothing seems to help.

When doing this from a root terminal "./cupsys start"

I get this "* Starting Common Unix Printing System: cupsd                           [ ok ]"

Any suggestions?

Thanks!

---

### Post by ubuntu_demon on 2005-04-22
$ sudo /etc/init.d/cupsd start
or when it's already running :
$ sudo /etc/init.d/cupsd restart 

When this doesn't work it could be that you miss some package. Try 
$sudo apt-get install ubuntu-base ubuntu-desktop

---

### Post by Staesys on 2005-04-22
I tried restarting CUPS and go this:

root@ubuntu:/etc/init.d # ./cupsys restart
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 98!

This really upsets me. The damn thing was working with my local printer just fine, but I was trying to add the network printer on the network to my system as well. It's a DJ 842C hooked up to a Netgear PS101 print server, btw.

I can go to [http://localhost:631](http://localhost:631) in my web browser, but when I try to manage my printers it times out finding the printer page.

In Gedit, I can go to file -> print and try to add a printer, but it no longer detects my DJ 970CXI printer like it did before.

I'm sure there's some setting I need to reset somewhere, but I admit to not knowing Linux that well at this point. I appreciate all of your help very much!

Thanks!

---

### Post by Alexander Kirillov on 2005-04-22
[QUOTE=Staesys]I tried restarting CUPS and go this:

root@ubuntu:/etc/init.d # ./cupsys restart
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 98!

This really upsets me. The damn thing was working with my local printer just fine, but I was trying to add the network printer on the network to my system as well. It's a DJ 842C hooked up to a Netgear PS101 print server, btw.

I can go to [http://localhost:631](http://localhost:631) in my web browser, but when I try to manage my printers it times out finding the printer page.

In Gedit, I can go to file -> print and try to add a printer, but it no longer detects my DJ 970CXI printer like it did before.

I'm sure there's some setting I need to reset somewhere, but I admit to not knowing Linux that well at this point. I appreciate all of your help very much!

Thanks![/QUOTE]
 I know little of print servers, but AFAIK, "listen for LAN printers" only waits for inrmation broadcast from CUPS servers. I have no idea what kind of sofware/protocol  Netgear PS101 uses, but if it isn't CUPS, this will not work. 

Maybe you could try accesing by selecting "network printer->windows printer (SMB)"? You'll need to install samba and related packages, though

---

### Post by Staesys on 2005-04-23
Okay, I guess the most important thing here is to figure out how to undo the "listen for LAN printers" selection I did because the local printer was working just fine until then, and now I can't get back into the printing preferences to change that setting back so I can get my local printer working again. I'd like to avoid a reinstall as I have a ton of stuff installed now, including a lot of stuff I compiled from source. Not to mention all of the system tweaks for sound and games and stuff I have done to get my computer working the way I want it.

*sigh*

This is starting to depress me.

BTW, I just installed SAMBA...so I'll see what I can do with that.

Thanks guys, I appreciate all of your help.

-Paul

---

### Post by mudra on 2005-04-23
I don't know if this will help but I had a problem with CUPS and that was because the lo was not being set up straight in the network boot up configuration. I found a thread here [http://www.ubuntuforums.org/showthread.php?t=12069&highlight=cups+127.0.0.1](http://www.ubuntuforums.org/showthread.php?t=12069&highlight=cups+127.0.0.1)

that helped me a lot.

Hope that this helps.

Mudra.

---

### Post by Staesys on 2005-04-23
Holy C*** I fixed it!

I'm not completely sure what I did, but it involves editing the /etc/cups/cupsd.conf and the /etc/cups/cupsd-browsing.conf files very carefully and then stopping the cups server, forcing a reload and then restarting the cups server.

In the cupsd.conf file I commented out any reference to browsing, and allowing connections from 192.168.102.200 (netgear ps101 print server) and port 631. In the cupsd-browsing.conf file I commented out the browsing line.

I'm not entirely sure exactly what I did, but hell, it's working now! At least in KDE, we'll see if it works in Gnome, but I'm sure it will.

*does happy dance*

Thanks to everyone who gave me their help with this issue, I appreciate your assistance very much!

-Paul

---

### Post by fizgig on 2005-10-19
@[B]mudra:

Thanks for your comment.  I was having the same problem and it turned out it was because I modified the networking startup script and lo wasn't being started.  I changed it to start lo and it's all good.  You saved my butt!
[/B]

---

