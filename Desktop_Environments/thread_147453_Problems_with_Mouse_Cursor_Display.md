---
title: "Problems with Mouse Cursor Display"
date: 2006-03-20
forum: Desktop Environments
---

### Post by linuxguy27 on 2006-03-20
Hello all,
I just installed ubuntu and really like what it has to offer.  It was a very easy install except for one thing, the mouse.

I have a 1cm by 1cm square on my screen for a mouse cursor.  I can click on things but the mouse is a large square on the screen.

What do I have to configure to correct this issue?

Also, for some reason while I using Ubuntu the screen just went blank and I had to reboot.

I have a Acer Travelmate 260 if that helps.

Thanks for your information in advance

Linuxguy

---

### Post by linuxguy27 on 2006-03-21
Hello all, I am posting to let you all know that I was able to solve the problem with my mouse cursor.

Thanks to the help from a person in the irc channel I was able to make my mouse pointer appear.  Here is how I did it:

1. reconfigured xorg - during this reconfiguration x810 was selected by default as the video driver.  I was told to change that to vesa.

2. Once I finished the reconfiguration I did a complete shutdown.  I restarted the computer.  The screen flickered for a few moments before the login screen appeared.  

I was happy to discover my mouse pointer was now back to normal.

Special thanks goes to brenner from #ubuntu on irc for his help with this matter.

If anyone has any questions about this issue please feel free to post in this thread.

thanks again
Linuxguy

---

