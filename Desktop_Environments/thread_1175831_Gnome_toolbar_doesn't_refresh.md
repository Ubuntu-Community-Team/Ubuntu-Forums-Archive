---
title: "Gnome toolbar doesn't refresh"
date: 2009-06-01
forum: Desktop Environments
---

### Post by Timtro on 2009-06-01
Hi,

I apologise for the vague title. I'm not quite sure how to describe the problem in so few words.

FYI: I'm using an up-to-date Jaunty.

A couple of weeks ago I got myself in trouble because I thought it was much earlier in the day than it really was. This was because the time on the gnome toolbar was wrong. If I go into the clock options and toggle to 12 hour time, then back to 24, it updates and works fine until my next log in.

I noticed also that my gmail notifier tray app, my random background switcher tray app, etc were't updating on the toolbar either, so the problem is the whole toolbar, not the clock. Its just not updating its appearance unless it is strongly forced by adjusting the properties of the clock.

Does anyone know what causes this, or better yet, how to fix it?

Thanks in advance.


Best regards,



Tim.

---

### Post by Therion on 2009-06-01
Let's try the simplest fix first:```
sudo apt-get install ntpdate
```
This package (Network Time Protocol) will ensure that the clock on your Gnome Panel stays synchronized with one or more time server(s).  

Install the package then right-click on your clock in the panel to start and configure NTP.  Once you do that, hopefully, things will get back to normal.

---

### Post by Timtro on 2009-06-01
> **Therion said:**
> Let's try the simplest fix first: ... 

I already have that package. I suppose it's installed by default in Jaunty. I should edit my original post to clarify that I am using an up-to-date 9.04.

Like I said, the problem isn't the clock, its the panel. The clock has the correct time once I give it a kick by changing something major.

Thanks anyhow.

---

