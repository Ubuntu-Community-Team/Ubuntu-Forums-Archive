---
title: "Virtualbox and the mouse"
date: 2009-04-02
forum: General Help
---

### Post by wongpk on 2009-04-02
I can't seems to find any information on the forum nor google, so I just post here.

I installed Virtualbox in my Ubuntu system, as I want to install Vista on the Virtualbox, I cannot use the mouse in the Virtualbox, beside the keyboard. How and what can I do so I can move the cursor in the Virtualbox?

---

### Post by 3Miro on 2009-04-02
It is a very good idea to get the doumentation (i.e. user manual) Virtual Box from [http://www.virtualbox.org/](http://www.virtualbox.org/) It is long, but you only need to read the sections that you want, and it is very well written.

VB and the host (Ubuntu Linux I assume), need to share the keyboard and the mouse. Until you install VirtualBoxGuestAddons (check it out at he manual and perhaps download those from the web-page), there is a trick.

Click on the VB window while Windows is running, a message would pop-up. Select, don't show this again and click capture. Now click inside windows again. Now your mouse should be captured, i.e. you cannot leave the window's window, but you can work under windows. To get the mouse pointer back to Linux -> press right Ctr.

The guest add-ons will make this much easier, however, you have to install windows before you can install them.

---

