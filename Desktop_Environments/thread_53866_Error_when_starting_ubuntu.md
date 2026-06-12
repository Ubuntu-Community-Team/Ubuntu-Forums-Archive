---
title: "Error when starting ubuntu"
date: 2005-08-02
forum: Desktop Environments
---

### Post by remmus on 2005-08-02
Whenever ubuntu desktop starts, a message pops up: "Missing command to run" How to fix it? What is it? Recently I tried to installed Nessus to keep computer safe, but I think it doesn't go well because after this, the message keeps showing at start. How to fix it too? 
Thank you

---

### Post by Zelut on 2005-08-02
Do you get this message during boot-time or after gnome starts & you login?  It'll make a difference in troubleshooting this error if you can be more specific.  It sounds like it may just be related to a program you've installed, as you mention, but its good to be sure.

Let me know where it comes up & we'll find a fix for you.

---

### Post by remmus on 2005-08-02
After I login and enter the ubuntu desktop, the message pops up immediately along with firestarter's. 

Could I ask altogether a problem with firestarter? Following another threat's guide, I've done 

"Enter the following in a terminal:

sudo gedit /etc/sudoers

add the following text to the end (replacing username with your login):

username ALL= NOPASSWD: /etc/firestarter

then adding "sudo firestarter --start-hidden" to your gnome sessions startup"

It does start silently but there's still a pop up "You must have root user privilages to use firestarter" How to fix this too?

Thank you very much

---

### Post by Zelut on 2005-08-02
checking my /etc/sudoers it looks like I have a difference.  My line reads:

username ALL=NOPASSWD: /usr/sbin/firestarter .  I guess the pathing is different for our disto.  Give that a try & see if it helps.

---

### Post by remmus on 2005-08-02
My version is Ubuntu Linux 5.04 : The Hoary Hedgehog Release

I changed the line to "username ALL=NOPASSWD: /usr/sbin/firestarter." It's still same here--firestarter does start silently but still pops up the error message--"Insufficient privilage -- You must have root user privilages to use firestarter"

and I also got second error message at start: "Missing command to run" 
The error message keeps showing at start, after I login, right after enter the ubuntu desktop.

Thank you

---

### Post by kittcankitt on 2005-08-03
Hope you get it figured out because mine does the same...lol.  Actually it started about 2 weeks ago.  I am usually always on but due to a few big storms and a few power outages, my computer had to reboot.  I didn't install anything recently and haven't made any major changes here either.  I will mention though that the first time I had 3 error boxes pop up (not including firestarters' permission box) and I am now down to one error box.  

I know this doesn't help but at least you know you're not alone!  

kck

---

### Post by remmus on 2005-08-03
I'm thinking to format and reinstall ubuntu. I guess it's the nessus causes the error. I'm clueless about this.  :-?

---

