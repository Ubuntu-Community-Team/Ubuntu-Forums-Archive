---
title: "I just want something similar to expose &amp; a keystroke simulator."
date: 2011-01-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by utahgimp on 2011-01-27
I use an Dell Mini 10v. I had OSX installed but Apple updates keep breaking the hack. I really like Ubuntu but I'm new and I will have a learning curve to endure. There are just a handful of things I want to make the OS do and I am having trouble.
 
I'm using 10.10 netbook edition, however, I always boot into desktop mode. **I can't seem to get CompizConfig to actually make the "expose-like" scaling effect to work**. I tried installing Ubuntu Tweak, but it didn't help, so I uninstalled it. The scale button is checked, but nothing happens when I hit the correct key. When I set a hot corner, there is no response. I am now wondering if the graphics card drivers that must have either been included in the distro or downloaded during an update, may not be sufficient to make CompizConfig work correctly. I have reinstalled CompizConfig stuff from the Software center. I still can't get the expose trick to work.
 
Also, I have used a program called Butler on OSX in order to **type out certain keystrokes when I press a hotkey combination**. I have several long usernames and other words that I need to type out regularly. The keystroke simulator saved A LOT of time. I don't know what to look for in Ubuntu to make this happen.

---

### Post by gordintoronto on 2011-01-27
I think your graphics adapter does not support compiz, but I could be wrong. Open Accessories/Terminal and type this command:
lspci
Look for the line that includes the word VGA; it is your graphics adapter. Now you can Google its identification with the word compiz or driver.

---

