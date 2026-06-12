---
title: "AWN and Compiz"
date: 2007-10-16
forum: Desktop Effects &amp; Customization
---

### Post by carolinamagi on 2007-10-16
Hello! I hope this is the appropriate section for this question . . .

I downloaded/install AWN using the following link and instructions:
[https://launchpad.net/awn](https://launchpad.net/awn)

So far as  I can tell the install went fine, "Avant Window Navigator" appears in the Applications mneu, and "Awn Manager" appears under System prefs. I can load the Awn manager and play with the settings.
When I try and load avant window navigator from the gui, I see a box appear on the screen and promptly disappear. When I go to the command prompt and try "avant-window-navigator" I get the following error message:

Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

I have compiz installed but I don't know how to adjust settings in that program to allow AWN to load properly.

I suppose this question has a few parts:
Do I have the correct version of compiz installed?
If so, what am I doing wrong in compiz?
If I don't have the correct compiz, should I uninstall it and replace it?

Sorry for the bother! 
Thanks in advance for your help!!!

---

### Post by Rupertronco on 2007-10-16
Do you have compiz, or compiz fusion installed? I've never used the original compiz, so I'm not sure if it meets the compositing requirements of AWN. I'd suggest installing fusion anyway, since it's far superior to the original compiz, and I can assure you that it meets all of the compositing requirements for awn. 

The problem may be with the awn install also. The easiest way to test that out would be to reinstall awn from Trevino's repository since it's already packaged in a .deb.

---

### Post by bromix on 2007-10-16
I use an ATI Radeon 9600.  In order for AWN to work, I had to install compizfusion, and in order for compiz fusion to work, I had to install XGL.   Let me know if you need help.  Having them both installed, I think all you would need to do would be install xserver-xgl.    That worked peachy for me.

---

### Post by bromix on 2007-10-16
Are you using Feisty or Gutsy?  I can help ya out either way if you need assistance.

---

### Post by Rupertronco on 2007-10-16
> **bromix said:**
> I use an ATI Radeon 9600.  In order for AWN to work, I had to install compizfusion, and in order for compiz fusion to work, I had to install XGL.   Let me know if you need help.  Having them both installed, I think all you would need to do would be install xserver-xgl.    That worked peachy for me.

XGL is only a necessity for ATi users. It's not needed for any other type of video card. It's best to see what he's using before recommending that.

---

### Post by bromix on 2007-10-16
True...  What are your system specs?

---

### Post by carolinamagi on 2007-10-21
> **bromix said:**
> Are you using Feisty or Gutsy?  I can help ya out either way if you need assistance.

When I posted this I was using fesity and have since updated to gutsy.

Thanks!

---

