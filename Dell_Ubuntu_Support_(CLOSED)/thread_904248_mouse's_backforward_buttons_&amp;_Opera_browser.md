---
title: "mouse's back/forward buttons &amp; Opera browser"
date: 2008-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2008-08-29
With Ubuntu 8.04, the Opera browser wasn't responding to the back/forward buttons on my Dell Bluetooth Travel Mouse.  Firefox responded fine, just not Opera.  (Clicking on the back and forward arrow icons on the toolbars worked for both browsers.)  The cure was in the file **/usr/share/opera/ini/standard_mouse.ini**.  That file has the two entries:
Button6 = Back
Button7 = Forward

Just remove or comment out those two lines (or just leave them in place), and add:
Button7 = Back
Button8 = Forward

That causes the back/forward buttons on **both browsers** to work fine.

*TimDaniels*

---

### Post by jvaverka24.86 on 2008-10-18
Just wanted to add another possibility...

I needed to make this Buttons 8 and 9 instead, like this...

Button8         = Back
Button9         = Forward

---

### Post by slockton on 2008-11-01
Hello,

Thanks for the tip - this got my Apple Mighty Mouse working properly with Opera 9.62 (on Intrepid Ibex).

Before that I was to scroll downwards with the scroll button Opera recognised this as "back" - VERY annoying.

Cheers,
S

---

### Post by shinew on 2008-12-30
thanks for the tip!
if you have a logitech MX1000 laser mouse, the "Back" is "Button8" & "Forward" is "Button9".

---

### Post by voxel on 2009-01-19
Yes, thanks for the tip!
I have a Logitech MX510 and setting Back to Button8 and Forward to Button9 works for Opera 9.63

---

### Post by Sunflower1970 on 2009-02-08
Awesome. Just found this thread by chance. For me, I have a MS Intellimouse Explorer Wireless, and I had to change it to Button4 for "Back" and Button5 for "Forward"

(This is on Arch, not Ubuntu BTW, and my version of Opera is 10.00)

---

### Post by Eestlane on 2009-03-15
Thank you so much!
I was messing with xorg conf file and other mouse stuff and didn't think it's Operas fault. Thank you!

Button8 & 9 worked for me btw.

---

### Post by supernerd1991 on 2009-07-16
if you are using opera 10.00 or later the standard_mouse.ini file is located in "/usr/share/opera/ui" not "/usr/share/opera/ini" as in earlier versions. 

so the file is /usr/share/opera/ui/standard_mouse.ini"

---

### Post by dtyger on 2009-10-23
> **voxel said:**
> Yes, thanks for the tip!
I have a Logitech MX510 and setting Back to Button8 and Forward to Button9 works for Opera 9.63

It works fine for Logitech MS510, 
but I ought to add: it's better to set 
Button8                            = Back
Button9                            = Forward | Fast forward

---

### Post by moe_syzlak on 2009-10-23
The solution is Firefox 3.5.

---

### Post by Bouke on 2010-01-23
Thank you, it saved me a lot of time figuring it out myself! :) Using a Dell Bluetooth Traveler Mouse on Opera 10.10, I had to change the ini file to this:

```
Button8							= Back
Button9							= Forward

```

---

### Post by boomshop on 2010-06-14
Hey!

It's possible to do this in the user's home directory for keeping changes over reinstall. Instead of editing /usr/.../standard_mouse.ini just create **~/.opera/standard_mouse.ini** and insert your preferences there. Seems that it's enough to just insert the two lines here since the other options are read from the file in /usr/...

---

