---
title: "Problems with xgl/compiz after update"
date: 2006-07-20
forum: Desktop Environments
---

### Post by hypersoar on 2006-07-20
Earlier today, my system automatically installed an update. It gave me a notification that it needed a reboot to complete, not listing what the upadte was. I then also installed a few updates which had just come out. After I rebooted, xgl no longer worked properly. None of the graphical effects are in place, and windows appear as merged with the menu bar at the top of the screen. 

It seems that one of the updates (I think the one which prompted the install) is causing this. Is there any way I can uninstall the offending update and get xgl working again?

---

### Post by adam.tropics on 2006-07-20
The offending update is probably a kernel update earlier in the week. I don't know which xgl install method you used, but if you are able to start a normal gnome session do so. Otherwise, open a terminal and enter 'metacity' This should give you window decoration at least, then you should check updates again, as there are more compiz ones I believe. Then, and I hate to say it, reboot...again. If there are still issues, post back.

---

### Post by hypersoar on 2006-07-20
I am able to start a normal gnome session. I just installed two compiz updates, yet the problem persists. I've rebooted several times since this started, including once after I installed the new updates.

---

### Post by adam.tropics on 2006-07-20
What video card do you have, and are you sure that in the normal gnoe session it is running correctly and without error. Also, have a look at [http://www.compiz.net](http://www.compiz.net) regarding your problem, there is a lot more info there.

---

### Post by hypersoar on 2006-07-20
I have a radeon 9550, and so far I haven't encountered any errors in my normal gnome session.

---

### Post by adam.tropics on 2006-07-20
If in a normal gnome session...not xgl, you open a terminal and type 'fglrxinfo' do you get a message regaring mesa ,or ATI? I am thinking that the kernel update may have screwed the fglrx driver. It shouldn't have done, if you used the repo version. But if you followed a guide somewhere to install the drivers from ATI's site, you may need to compile the modules again.

---

### Post by hypersoar on 2006-07-20
That was the problem. It's working now. Thank you.

---

