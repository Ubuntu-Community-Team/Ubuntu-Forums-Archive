---
title: "Maple 12 won't accept keyboard input."
date: 2009-03-06
forum: General Help
---

### Post by benjorino on 2009-03-06
I have maple 12 for linux, running in Ubuntu 8.04 Hardy Heron, but I can't get it to recognise the keyboard... Any ideas?

I had trouble even getting it to run for a while (it just opened a blank window). That was fixed by running "export AWT_TOOLKIT=MToolkit" in the terminal every time before starting maple. (Just thought I'd mention that in case it could be in anyway related to the keyboard issue)

Weirdly, if I open the options window in maple I can still type in the boxes there... its just the input in the main program that is not working.

Thanks for your time.

---

### Post by PheonixKotori on 2009-03-06
I have no solution for you, but I'm experiencing the same problem. Also using the 'export' command to get display to work. Browsing other forums revealed nothing, except lots of people are having the problem, and lots of people are not.

When I first start Maple, I can create a new worksheet and then keyboard input seems to be accepted...sometimes. Saving the file ends this, however.

---

### Post by C. M .Hughes on 2009-07-05
Hi all,
I too have the same problem, I'm using Maple 13 on Ubunutu 9.04. 

I discovered the same tactic that you mentioned about opening a new Worksheet- it seems to work reliably, but it's a bit of a pain. I've contacted Maplesoft support and will repost if I get a solution back. 

One thing I can help with though: instead of typing the export command you mentioned every time, you can add it to xmaple. See [this post]("http://ubuntuforums.org/showthread.php?t=907702").

---

### Post by alek_a on 2009-08-06
I also have this problem, using Maple 12 and Ubuntu Jaunty.

The help from the official maple site 

[http://www.maplesoft.com/support/faqs/detail.aspx?sid=32697](http://www.maplesoft.com/support/faqs/detail.aspx?sid=32697)

was useless as I dont use SCIM (nor I understand what the issue is really, my hack level is rather low).

I use java linked to sun-java6-xxx and not Maple's own java (this issue seems independent of this). BTW, you can ignore the

export AWT_TOOLKIT=MToolkit 

fix if Java is thus linked. Though you then get some warnings in the terminal when you start maple, they seem harmless enough.

---

