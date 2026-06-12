---
title: "Dapper Freeze on Logout/Shutdown"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Im_Just_GrayT on 2006-08-09
For some reaon every time I try to shutdown or logout the screen just freezes, No buttons work or anything. My system monitor is still scrolling just fine, but i cant click on anything. Anyone know whats wrong?

---

### Post by jordilin on 2006-08-09
Yes, since I installed Dapper it has happened to me two times, but not as a regular/daily basis. It could be your graphics card driver. Which one are you using. What kind of card do you have?

---

### Post by Im_Just_GrayT on 2006-08-09
Yeah, it happens every time I try to logout, shutdown, or restart. 
about the graphics card, I'm not quite sure what driver It's using. But I just have an onboard graphics card, built into my motherboard. How would I find out what driver it's using?

---

### Post by jordilin on 2006-08-09
> **Im_Just_GrayT said:**
> Yeah, it happens every time I try to logout, shutdown, or restart. 
about the graphics card, I'm not quite sure what driver It's using. But I just have an onboard graphics card, built into my motherboard. How would I find out what driver it's using?

take a look at /etc/X11/xorg.conf In this file you'll find which driver are you using. 
Look for something like this:
> Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection


---

### Post by Im_Just_GrayT on 2006-08-09
This it?
```
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
```

---

### Post by jordilin on 2006-08-10
> **Im_Just_GrayT said:**
> This it?
```
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
```

It seems your graphics card is built into your motherboard. I don't know if this could be the problem. Take a look at system logs, i.e. /var/log/messages for any clue. Look at the minute you shutdown and see if there's any log in messages

---

### Post by Homie Bongo on 2006-08-20
Hello, the same problem happens to me -- whenever I try to logout, restart, switch user or shut down my pc freezes. It hangs right after and a distorted picture with looped freezed sound appears. It hadn't happen before I installed nVidia drivers (using Automatix). 
this is from my *xorg.conf*:
> Section "Device"
    Identifier     "NVIDIA Corporation NV35 [GeForce FX 5900]"
    Driver         "nvidia"
EndSection
Or should I start a new feed?
Thank you for any help!

---

### Post by mark_e_wallace on 2006-08-22
> **Homie Bongo said:**
> Hello, the same problem happens to me -- whenever I try to logout, restart, switch user or shut down my pc freezes. It hangs right after and a distorted picture with looped freezed sound appears. It hadn't happen before I installed nVidia drivers (using Automatix). 
this is from my *xorg.conf*:

Or should I start a new feed?
Thank you for any help!

This happens to me as well. Eager for any solution that y'all may have.

- Mark

---

### Post by RJNFC on 2006-08-27
> **Homie Bongo said:**
> Hello, the same problem happens to me -- whenever I try to logout, restart, switch user or shut down my pc freezes. It hangs right after and a distorted picture with looped freezed sound appears. It hadn't happen before I installed nVidia drivers (using Automatix).

This is an exact description of the issue I just had, including using automatix and the graphics card model (5900).  I fixed it by removing the "splash" option from the kernel line in my /boot/grub/menu.lst file.

---

