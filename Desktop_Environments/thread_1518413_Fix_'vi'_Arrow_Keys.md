---
title: "Fix 'vi' Arrow Keys"
date: 2010-06-26
forum: Desktop Environments
---

### Post by volobiz on 2010-06-26
On may last laptop, an Acer, the up, down, left, right cursor arrow keys  worked just fine inside of vi. But now when I use vi in Ubuntu 10.04  LTS, on a brand new eMachines E525 laptop, I can't get the arrow keys to  work. Instead, they display A, B, C, and D characters.

What's the fix to get this going?

Note that if I hold down the Alt key, the arrow keys seem to work  properly.

---

### Post by Dr_Willis on 2010-06-26
the default 'vi' in ubuntu is a vi 'light' version that does not use the keys  as you would expect.  (actually its the vim-tiny package)

If you install the 'full' vim package - you do get the arrow keys working and other nice features such as color  syntax.

Installing the 'vim' package should get you fixed up. There may be some other vim packages you might want as well.

**sudo apt-get install vim **

---

### Post by volobiz on 2010-06-26
You fixed me. Thanks. 

Odd change in Ubuntu distributions. Okay, I'll have to remember that from here on out.

---

### Post by Dr_Willis on 2010-06-27
This was changed a few years back (a few releases back?) - I imagine the main reason was due to the size of the vim packages. 

I make a little script that installs vim and about 30 things on every new install i make, so i rarely see the issue. About the only time i encounter this 'issue' (its not really a bug, its how vi works)  is on other peoples machines.

---

### Post by potatochip on 2010-08-14
Thanks, that's a great tip

---

