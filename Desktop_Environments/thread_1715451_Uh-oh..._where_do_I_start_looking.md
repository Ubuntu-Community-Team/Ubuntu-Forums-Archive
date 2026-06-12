---
title: "Uh-oh... where do I start looking?"
date: 2011-03-27
forum: Desktop Environments
---

### Post by Karl10 on 2011-03-27
[FONT="Comic Sans MS"][SIZE="2"]Hi Folks

Not sure where to start here... System's been running okay for about 5 months (Ubuntu 10.10, 32-bit; Asus G73JH-A1 laptop {RoG gaming rig}), but for the last couple of weeks it's been getting squirrely: 1.) Compiz Fusion set to load on boot; it doesn't. Settings checked as start on boot, it just doesn't and has to be loaded manually from desktop  2.) Desktop Drapes (wallpaper changer) also set to load on boot; also doesn't do so, even though checked to do so, and also must be loaded manually from desktop.  3.) Something is hogging CPU cycles something awful; if I have more than a few tabs in Firefox open, it takes forever to scroll or reload, and the entire system just bogs almost to the point of unusability.  This same behavior exists offline when using any graphic capability (Shotwell or even just Nautilus file manager, if viewing graphics as thumbnails.

I realize this is kind of all over the place and all-inclusive, but although my experience USING Ubuntu goes on several years, it's been generally so trouble-free that I've not had to dig around under the hood much, and I'm kind of at a loss as to where to begin troubleshooting this mess.  Would it be easier to just back-up and nuke/reinstall the OS??  Practical maybe, but not very educational.  Any links or insight gratefully received!

Karl

P.S.  I've made no changes to system other then the occasional app download, and routine upgrades/updates, and really can't associate this behavior with any of those.[/SIZE][/FONT]

---

### Post by mikewhatever on 2011-03-27
You can easily figure out what is overloading the CPU by installing and looking at the output of 'htop', also, look at disk space availability with 'df -h'. 
It seems that the problems you describe are user space, and if so, creating another user will solve them as effectively as reinstalling.

---

### Post by Krytarik on 2011-03-27
Did this all start at the same time?

A web search revealed that your laptop has an ATI Mobility Radeon HD 5870 graphics processor (for everybody else).

What video driver are you running?
How did you install those?

---

