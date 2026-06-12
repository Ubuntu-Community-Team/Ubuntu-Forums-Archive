---
title: "Computer name changed unexpectedly"
date: 2012-11-29
forum: Desktop Environments
---

### Post by faabiioo on 2012-11-29
Hi,

today I've seen again this weird behaviour. I turn on my PC after a normal shut-down, open the terminal, and I notice the oddity: instead of 
```
 fabio@fabuntu:~$
``` it has changed to ```
 fabio@mySurname-ws:~$
```.

is there a reason for this? and is there a way to fix it?

well, nothing severe here, but it is not the first time it happens, and it eventually turns back to the right string. 

I'd appreciate a clarification...
thanks

---

### Post by The Cog on 2012-11-29
Is your PC using DHCP? 
I wonder if the DHCP server is allocating it a name as well as an IP address occasionally. I have no idea how to prove whether or not this is what's happening though.

---

### Post by faabiioo on 2012-11-29
Well, I do use the DHPC server but I don't see why and how it could change  the name. And, I dont know if this might sound clever but, I'm in a kind of enterprise LAN, thus my IP is always the same

as I said, this already happened before, every time it changed in the very same way, and then back to normality somehow (kind of frightening!).

---

### Post by howefield on 2012-11-29
In terminal type

```
gksudo gedit /etc/hostname
```

Enter your password when prompted, edit as required. 

Again in terminal, do the same to the /etc/hosts file, making sure the name matched what you put into the first file.
   
```
gksudo gedit /etc/hosts
```

Then save and reboot.

---

### Post by faabiioo on 2012-11-29
Everything seems fine with these files. In hostname there's "FabUntU" as it should be, and the second file lists:
 "127.0.0.1  localhost" 
 "127.0.1.1  FabUntU"

and some lines about desirable IPv6 capable hosts. is there something to be changed here?

---

### Post by faabiioo on 2012-12-01
Well, just to mention, as I'm the one who started this topic: this morning everything went back to the right names. without me doing anything but normally shut down and power on this morning,

Well, as I wrote, nothing severe, but I think it is a rather weird behaviour, not quite desirable

thanks anyway

---

