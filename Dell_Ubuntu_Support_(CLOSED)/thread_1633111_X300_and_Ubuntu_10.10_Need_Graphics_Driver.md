---
title: "X300 and Ubuntu 10.10 Need Graphics Driver?"
date: 2010-11-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kpayton on 2010-11-28
Acording to Dells website I show it as having an Intel Chipset but I can't find drivers anywhere for it.  Default RES is 1024x768.

Can someone help me?

Dell X300 running Ubuntu 10.10

---

### Post by garvinrick4 on 2010-11-28
Are they in System/Admin/hardware drivers?

---

### Post by kpayton on 2010-11-28
> **garvinrick4 said:**
> Are they in System/Admin/hardware drivers?



No - No proprietary drivers are in use on the system.

---

### Post by garvinrick4 on 2010-11-28
What is not working your graphics card, you want to set it at a particular resolution, other problems?
Run this code in a terminal:
```
sudo lspci -v | less 
```Copy and paste which card and driver is the problem:
Users can see what you got going and help you. 
Lots of users with same card and driver.

---

### Post by kpayton on 2010-11-29
> **garvinrick4 said:**
> What is not working your graphics card, you want to set it at a particular resolution, other problems?
Run this code in a terminal:
```
sudo lspci -v | less 
```Copy and paste which card and driver is the problem:
Users can see what you got going and help you. 
Lots of users with same card and driver.

Sorry it took me a bit to reply to this.  

Well I ran the command and as it turns out it DOES have the correct driver or atleast the correct chipset.

I guess what I'm after here is I can't go any higher on RES than 1024x768 which is fine on the laptop but I'm using the laptop for my television in my bedroom.  Its night a higher powered machine by any sense just a junker I had downstairs.  The monitor actually says "UNKNOWN"  And I can't enable special effects on the monitor either.

Any ideas?

---

