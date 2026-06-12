---
title: "Does anyone use a Logitech G11 or G15 keyboard with linux?"
date: 2009-11-07
forum: Gaming &amp; Leisure
---

### Post by j7%&lt;RmUg on 2009-11-07
Im wondering about this because they are both great keyboards and are exactly what i need, does anyone who uses one have any problems with it on linux? A G19 is too expensive for me at the moment so please dont suggest that.

Thanks.

---

### Post by Clopin on 2009-11-08
Currently using G15 with G15Daemon and G15Macro.
TBH I think G15Macro really needs the feature to record time delay between keyboard presses.

---

### Post by j7%&lt;RmUg on 2009-11-08
Ok, so i take it that ubuntu has support for its macro keys? and that the different color backlights work in ubuntu?

---

### Post by Clopin on 2009-11-08
Yes, the macro keys work if you install G15Macro using Synaptic.
Ofc you can only have orange backlight if you got a G15v2, but yes, the backlight works.

---

### Post by j7%&lt;RmUg on 2009-11-08
Thanks very much for the info, i just found it in synaptic, looks like im getting a G15.

---

### Post by ROY.G.BIV on 2009-12-27
Edit: don't bother, I've given up on this keyboard, it just does not work.

---

### Post by xbaez on 2009-12-29
Hello
I have this keyboard and works great, except all the num keys 
they don't work

Can anybody please help me?
this is one of the reasons I wouldn't use Ubuntu, since it's a nice expensive keyboard and the numbers are absolutely necessary

---

### Post by RobbieThe1st on 2009-12-30
Huh, thats odd. I have no trouble whatsoever with my G15V2 - I installed G15Daemon and G15Macro, and both are working fine.
I also learned that the LCD works natively with Mumble - After installing Mumble I got a new LCD window for all the current users. 

My only issue is that I haven't been able to get G15Macro to auto-start for some odd reason, but I'm assuming theres some trick to it which I've missed(and I haven't looked too hard).

---

### Post by xbaez on 2009-12-31
> **RobbieThe1st said:**
> Huh, thats odd. I have no trouble whatsoever with my G15V2 - I installed G15Daemon and G15Macro, and both are working fine.
I also learned that the LCD works natively with Mumble - After installing Mumble I got a new LCD window for all the current users. 

My only issue is that I haven't been able to get G15Macro to auto-start for some odd reason, but I'm assuming theres some trick to it which I've missed(and I haven't looked too hard).


How can I completely disable Ubuntu from installing new packages?

I hate when I install new software and something else breaks

I followed the Ubuntu Guide, and then, I think maybe a software or daeom or something or kernel (I really don't know), is not allowing me to enjoy my G15 keyboard

---

### Post by bdaman80 on 2009-12-31
Under your keyboard settings make sure you uncheck the option to allow arrow movements with the keypad.  Not sure if this is your problem, but that one has got me before

---

### Post by xbaez on 2010-01-01
> **bdaman80 said:**
> Under your keyboard settings make sure you uncheck the option to allow arrow movements with the keypad.  Not sure if this is your problem, but that one has got me before


can you please tell me where exactly I do that?
I tweaked with the options today and never found any option that enabled the keyboard

---

### Post by ROY.G.BIV on 2010-01-01
system => preferences => keyboard => mouse keys.

I just wanted to give an update on my situation... I don't think this an issue with the software, it seems to extend far beyond that. I don't know if its my repos, libraries or what, but I haven't been able to download many packages successfully. For example, I tried to install g15daemon a minute ago, here is what it gave me: ```
E: g15daemon: subprocess post-installation script returned error exit status 1
``` g15macro? ```
E: g15daemon: subprocess post-installation script returned error exit status 1
E: g15macro: dependency problems - leaving unconfigured
```There are no dependency issues... I had a bigger error list the other day, that I tried to copy/paste, but it didn't copy, so I lost it. :( That was via system update via synaptic(gave me more error info than CLI). Can someone help me figure out what's wrong here?

---

### Post by xbaez on 2010-01-03
> **xbaez said:**
> can you please tell me where exactly I do that?
I tweaked with the options today and never found any option that enabled the keyboard

Awesome man that did the trick!
Enjoying macros as well to swith to workspaces

---

