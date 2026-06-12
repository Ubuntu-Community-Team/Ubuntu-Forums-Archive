---
title: "Help needed: Installing Firefox 1.5x and 2.0x together"
date: 2007-03-27
forum: Desktop Environments
---

### Post by abstrakt on 2007-03-27
I'm running the latest beta of feisty 7.04, so far everything is great, but I do have one small problem.
I need to be able to run both versions of Firefox (I use the old one for a specific web based classroom application for some of my classes), but I'm having trouble.  

2.0.0.3 runs fine, but when I download and extract 1.5.11 to it's own directory and run ./firefox from where I extracted the files, it just fires up version 2 instead.  Is there any way to have both versions installed and running from two separate icons?

Thank you.

---

### Post by aysiu on 2007-03-27
Maybe they can't be both running simultaneously? Maybe that's why it fires up 2.0 instead of 1.5?

I know you can have them separate, as I've done that before.

Do you close 2.0 before you try launching 1.5?

---

### Post by abstrakt on 2007-03-28
yes I'm sure that 2.0 is completely closed before I try to run 1.5.

I'm sure it can be done I just don't know how exactly.

---

### Post by aysiu on 2007-03-28
What you're doing should work.

Can you post the exact terminal output--including the changing of directories?

---

### Post by abstrakt on 2007-03-31
I was able to partially solve the problem - it was a strange thing.  I had to remove firefox 2.x from the adept installer, then point a new launcher icon to the location of the older version I had extracted.  Once I was sure the old version worked, I reinstalled the new version from adept and both versions worked (kinda).

Now if I can figure out how to get both versions of firefox to use the java plugin, I'll be happy.

---

