---
title: "mouse doesnt work  AAARGH!"
date: 2005-10-13
forum: Desktop Environments
---

### Post by greengrass on 2005-10-13
how do you figure out what port the mouse is connected to?

---

### Post by bin on 2005-10-13
PS/2 mouse will normally be /dev/psaux

What sort of mouse do you have?

in light 

bin

---

### Post by greengrass on 2005-10-13
i am using an old mouse with a 9 pin connector

---

### Post by bin on 2005-10-13
Ah that'll be a serial mouse then, should be /dev/ttyS0 for com1 or ttyS1 for com2.

Ubuntu *should* have picked that up - do you have a serial modem connected?

in light

bin

---

### Post by greengrass on 2005-10-13
I am very green at this.  

How do you know if its at ttys0 or ttys1?

I am going to connect a Westell  327W dsl modem but its not connected yet

---

### Post by bin on 2005-10-13
Well, if you've only got one serial port that the mouse will fit into then there's an even chance it will be com1. 

I may be answering this the wrong way round. I guess that your mouse is not working in Ubuntu 5.10 and you want to make it work? It's all tied in with the X11 server - have you searched for Serial Mouse in the different Ubuntu Forums?

in light 

bin

---

