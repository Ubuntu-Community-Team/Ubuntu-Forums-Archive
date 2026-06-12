---
title: "Dell Mini vs WiFi"
date: 2011-03-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by K-Sub on 2011-03-30
I have a Dell Mini 10v (model 1011?). Up until now the wireless has worked just fine. I started the computer the other day and no WiFi. I reinstalled the driver for th Broadcom Wireless card. It worked fine. I cycled the machine a few times. All good.
 
I turned on the machine last night. Again, no WiFi. I again installed the driver, though it was rough and I got a "**SystemError:installArchives () failed"** message. Regardless, once I restarted the machine it all worked fine. Again I cycled the machine a couple of times and all was good.
 
I'm getting ready to take this computer on a vacation and I'm concerned about losing WiFi when i cannot easily fix it. I need to try tonight to see if I'm still good.
 
Any thoughts on why this keeps happening? Any easy ways to fix it if I can't get online when I have the problem?

---

### Post by TBABill on 2011-03-30
It could be that your machine is set to turn off the wireless after a certain number of minutes without use and when it goes into suspend or hibernate. Can you adjust your power settings to NOT control the wireless? Or better yet, have power settings shut off while on AC. I do that. I just have my screen go black when not in use, but it never suspends or hibernates. My wireless (Broadcom, Dell) never fails to stay connected that way.

---

### Post by K-Sub on 2011-03-30
Thanks, but that's not it.  I don't lose wireless while operating, it just doesn't work after the machine has been turned off because the driver is no longer installed!
 
I have had this machine for a bit over a year and this problem just started this week.

---

### Post by TBABill on 2011-03-30
> **K-Sub said:**
> Thanks, but that's not it. I don't lose wireless while operating, it just doesn't work after the machine has been turned off because the driver is no longer installed!
 
I have had this machine for a bit over a year and this problem just started this week.
 
If it's a matter of just not having the driver active when you restart, just edit /etc/modules and enter the driver name at the end of the list.
 
For example, my Broadcom BCM4312 uses the sta driver. Its module is actually wl. So I would ```
gksudo gedit /etc/modules
``` and add ```
wl
``` to the end, save and restart. Then it loads every time I restart the machine.

---

### Post by K-Sub on 2011-03-30
> **TBABill said:**
> If it's a matter of just not having the driver active when you restart, just edit /etc/modules and enter the driver name at the end of the list.
 
For example, my Broadcom BCM4312 uses the sta driver. Its module is actually wl. So I would ```
gksudo gedit /etc/modules
``` and add ```
wl
``` to the end, save and restart. Then it loads every time I restart the machine.
 
 
Thanks.
 
How do you know that the module is wl?
 
My machine does not seem to use the sta driver, I don't have it in front of me but it is another driver like b43. When I loaded the sta driver, I didn't get wireless.
 
Thanx!

---

### Post by TBABill on 2011-03-31
Ummm....the STA driver's kernel module is wl. That's how the system recognizes it, not as STA. If you use the b43 driver, however, you'd place b43 into /etc/modules. But be sure it's the b43 and not b43legacy, ssb, or brcm80211. Whatever driver you are using should be what you put at the end of /etc/modules.

---

### Post by ugm6hr on 2011-04-02
> **K-Sub said:**
> I have had this machine for a bit over a year and this problem just started this week.

Seems a little odd for a software problem.
Perhaps the wifi card is a little unseated, and just needs to be plugged in better?
Next time it doesn't work - check lspci or lshw to ensure it is still recognised correctly.

---

