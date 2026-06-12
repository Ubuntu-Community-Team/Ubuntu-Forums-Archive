---
title: "[SOLVED] I disabled the gdm service."
date: 2008-02-20
forum: Desktop Environments
---

### Post by inyoka on 2008-02-20
Okay I know it sounds daft, but I had my reasons okay!!

System>Administration>Services>gdm> and I clicked stop.

Not surprisingly when I rebooted instead of going to the command line it gives me a black screen.  I can boot into the failsafe kernel and start gdm manually, but I cannot get back into Services, its says "You are not allowed to access the system configuration". Yes it prompts for a password and it is correct.

I also get an error "Failed to initialise HAL" when I login, although I dont know if this is related.

If anyone can tell me how to undo this I would be very grateful :)  I tried looking in a couple of K01gdm files from the rc1 and 6 directories TNA they seem to start gdm, but it isnt starting.:confused:

---

### Post by Whiffle on 2008-02-20
try

sudo update-rc.d gdm defaults

---

### Post by lsmobrian on 2008-02-20
if that doesnt work maybe   

sudo dpkg-reconfigure gdm

---

### Post by inyoka on 2008-02-20
Thank you both, I was sure both your idea's would work but I got the following errors:

"sudo update-rc.d gdm defaults"
Gave the message "System startup links for /etc/init.d/gdm already exist "

"sudo dpkg-reconfigure gdm"
Gave the message "invoke-rc.d: initscript gdm, action "reload" failed"

Any other ideas?  When I boot to the recovery mode from the gdm menu I dont have networking, if I did I could try re-installing gdm.  Anyone know how to get networking up and running, ifconfig only show the local loopback interface and /etc/init.d/networking start, and ifup eth0 do nothing.  It appears as though eth0 doesn't exist, how do I get it to start my network card up? :(

---

### Post by inyoka on 2008-02-20
Okay one of the commands above appears to have created the /etc/rc.local file, this was missing before as I believe is standard practise in Ubuntu now.  Anyway long story short I added :
```
/etc/init.d/gdm start
```
Booted up all okay, re-enabled gdm, removed the line from rc.local and all is well.

Thank you soooo much to lsmobrian and Whiffle, not sure which of your commands created the rc.local but as soon as it appeared I knew I could fix it. Hope I can return the favour someday ;)

---

