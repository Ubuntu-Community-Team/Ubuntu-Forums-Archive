---
title: "kdmthemes broken in hardy ?"
date: 2008-04-26
forum: Desktop Environments
---

### Post by akwatve on 2008-04-26
hi,

i recently upgraded to hardy and looks like kdetheme is broken (or somthing is miserably wrong). it lets me log in but i cannot log out. i cant shut down or do anything that involves logging out of my account. it just hangs. i observed that if i uninstall themes and use bare kdm things are fine. i am on acer aspire 5052 using amd x86_64 (if that matters).

the worst part is when my machine hangs i have to do a hard reboot by holding power key pressed for 5 seconds. i cant use alt + printscr + s + u+ b. 

i would like to know if anyone else has seen this problem.

---

### Post by akwatve on 2008-05-07
*bump*

---

### Post by Xiong Chiamiov on 2008-05-08
I'll take a look at kdmthemes when I get back from class.  In the meantime, when it freezes, can you do a ctrl+shift+backspace to restart X?  Are you using KDE3.5 or 4?

EDIT: I didn't have any problems in 3.5.9, though of course it screwed up my nice settings ;).

---

### Post by akwatve on 2008-05-11
Hi,

I cant do ctrl+shift+backspace ... the machine just hangs. It does not respond to any "SOFT" reset commands. Even alt + print_screen + s + u+ b does not work. Only option I am left with is to do a hard reboot by pressing and holding the power key for 5 seconds

---

### Post by ChameleonDave on 2008-06-04
Can you shut the computer down from the command line?

```
sudo shutdown -h now
```

```
sudo reboot
```

---

### Post by akwatve on 2008-06-04
I can't do anything. When I click on "logout", The screen goes blank and then nothing works. I cant even open a terminal to shut it down. So I cannot try commands you mentioned.

---

### Post by ChameleonDave on 2008-06-04
> **akwatve said:**
> I can't do anything. When I click on "logout", The screen goes blank and then nothing works. I cant even open a terminal to shut it down. So I cannot try commands you mentioned.

I mean, don't click on "log out" at all.  Enter those commands *instead*.

---

### Post by akwatve on 2008-06-04
Ahhh. Sorry abt that.
Let me try. I will post here after I give it a try.

---

### Post by akwatve on 2008-06-04
I tried to run those commands to bring the system down.
Both of them work perfectly fine.
I was able to reboot/shutdown my system from the terminal

---

### Post by akwatve on 2008-06-04
One interesting observation. I just uninstalled and reinstalled kdm and kdm themes. And it seems to be working properly for now. I don't know what exactly had gone wrong.

---

### Post by takowl on 2008-06-05
This sounds a bit like an issue I had, which was related to ATI graphics drivers. If it starts happening again, and you also have an ATI graphics card with the proprietary drivers, can you upgrade to the version of xorg-driver-fglrx in hardy-backports--that solved it for me.

---

### Post by akwatve on 2008-06-05
Yes, I do have an ATI card and proprietary driver. I will try your suggestion if it happens again.
But for now I don't want to fiddle with a running configuration :-)

---

