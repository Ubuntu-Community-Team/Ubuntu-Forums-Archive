---
title: "No text login on virtual terminals one through six"
date: 2012-01-28
forum: Desktop Environments
---

### Post by ElectricTriangle on 2012-01-28
Not entirely sure when or why this started to happen, but I have no video output or keyboard input on my virtual terminals (CTRL + ALT + F *), all I have is my desktop environment on terminal 7, as usual. I tested for keyboard input by using aplay and typing without being able to see, but that didn't work either, the terminals all just seem to be dead for some reason.

System - Ubuntu 11.10, Compiz

---

### Post by Bobhuber on 2012-01-28
These instructions are for a Plymouth logo in 10.04  but basically you want to enable uvesafb for your VT and boot cycle. Follow the post and you will get your text back in a virtual terminal in 11.10. If your not sure on your screen resolution just use 1024x768 in leau of 1280x1024 as recommended in the post. Use Alternative one ( Fixing Plymouths resolution ) in the post.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by ElectricTriangle on 2012-01-29
That worked, brilliant! Just out of curiosity, what did the uvesafb module do that wasn't working already? Ah, perhaps it also had something to do with a fglrx update?

---

### Post by Bobhuber on 2012-01-30
> **ElectricTriangle said:**
> That worked, brilliant! Just out of curiosity, what did the uvesafb module do that wasn't working already? Ah, perhaps it also had something to do with a fglrx update?
Yes there's a problem (been around quite a while) with Plymouth, the boot cycle and VT with certain configurations (proprietary drivers). It applies to Nvidia also.What you actualy did was enable and use the graphics capability of your Bios for boot (splash screen) and virtual terminal .
Glad I could help.

---

