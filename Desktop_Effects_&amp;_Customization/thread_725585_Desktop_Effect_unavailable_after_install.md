---
title: "Desktop Effect unavailable after install"
date: 2008-03-15
forum: Desktop Effects &amp; Customization
---

### Post by davyboy04 on 2008-03-15
I just intalled Ubuntu and now the desktop effects are unavailable.  They worked awesome with the live cd, but now it say that my hardware doesn't support them.  If my hardware was good enough when I was running off a CD, how could they not be good enough after the install?

---

### Post by VTBuc on 2008-03-15
You probably don't have 3d acceleration enabled. Check your restricted drivers manager. Go to System> Administration> Restricted Drivers Manager. Make sure the graphics driver checked.

If that doesn't work, let me know and there's a couple other things that could fix it.

---

### Post by davyboy04 on 2008-03-15
Hello VTBuc thank you for your help.

The only thing listed in my restricted drivers is the software modem.  I don't use dial-up so I don't need that at all.  

ALSO, i just found out that Rythmbox won't update the codecs.  It downloaded and installed codecs fine and I was able to my mp3s with the live cd.  But now I can't.  These are the only two things going on but they are pretty big deals to me.

---

### Post by VTBuc on 2008-03-16
Okay, you might have generic graphics card drivers. Here's what you do. Go to System> Administration> Screen and Graphics

Click the tab that says Graphics Card. Does it have a driver listed for your actual graphics card or a generic one? If a generic one, find the proper one through the dropdown list. Make SURE to click the "Test" button. Let me know if that works.

---

### Post by davyboy04 on 2008-03-18
HI VTBuc!!   
It says generic.  How do I know which one to pick?  

Sorry for the delay, but I took a long weekend :)

---

### Post by FuturePilot on 2008-03-19
What graphics card do you have?
If you don't know
```
lspci | grep VGA
```
will tell you.

---

