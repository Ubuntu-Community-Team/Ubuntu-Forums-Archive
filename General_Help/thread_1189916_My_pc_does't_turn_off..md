---
title: "My pc does't turn off."
date: 2009-06-17
forum: General Help
---

### Post by Bonsanto on 2009-06-17
Hi guys, I bought a new Pc, I armed it and installed on it, Windows Vislag and Ubuntu 9.04. The thing is that my pc can't shut down from UBuntu, but It can do it from Vislag, When I try to shut it off it restarts... :(
 
My motherboard is an Intel DG41TY, I have a Core 2 duo model 7400, and 4gb ram mark Kingston. :S

ANy Idea of the problem?

---

### Post by dhughes on 2009-06-17
Open Terminal and try ```
sudo shutdown -h now
``` and see if that will power down your system. I'm not sure why it isn't working as it should.

---

### Post by SuperSonic4 on 2009-06-17
sometimes the above command just reboots the PC. You can force power off by passing a -P flag

```
sudo shutdown -hP now
```

If that works I'm guessing it's because your user is not in the power group

---

### Post by Bonsanto on 2009-06-18
Didn't work, It keeps rebooting :S

---

### Post by t4thfavor on 2009-06-18
sudo poweroff

Try that, from a commandline. It may give you info on what is causing the lock. I bet it will just shut down though.

---

### Post by lsatenstein on 2009-06-20
I am running crontab with poweroff as 

30 1 * * *  /sbin/poweroff   

I tried all command line options with poweroff, with halt, with shutdown,

and the Ubuntu version does not do a full poweroff, but leaves the power remaining on. System leds are light, and keyboard lights work with keys.

I believe that "poweroff -P" is not respected.  nor is "shutdown now".

Works with Fedora, so it should work with UBUNTU.  I am on JJ 9.04 and my system is a desktop unit that has a new dual core with 4 gigs of ram.

---

### Post by Bonsanto on 2009-06-26
You have this same motherboard and same problem? Is so weird I can turn it off with Windows XP, Vista and with Mandriva, but with ubuntu it reboots :S

---

### Post by rob1408 on 2009-06-26
You could try this.

sudo gedit /etc/modules

then add this to the end and then save

apm power_off=1

reboot your computer and then try and shut it down.

---

