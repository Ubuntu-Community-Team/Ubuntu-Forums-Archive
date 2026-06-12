---
title: "WG311  Wireless causing inability to reboot, sudo su and more."
date: 2009-04-23
forum: General Help
---

### Post by haydnjones on 2009-04-23
Hey all,

Usually I have been able to figure out all of the problems I have come across in Ubuntu. Whilst I generally don't know what I'm doing through research I work it out but this one has really done my head in. Months of this issue and I gotten no where, even searching this is tough so I thought its about time I posted the problem.

In a nut shell wireless is dropping out and I believe its an issue with some part of wireless networking within Ubuntu. The system running Ubuntu is being used mainly as a file server via Samba but I also stream music and videos from it. 

The problem arises after random amount of time after streaming music or transferring files and requires a complete reboot before wireless is active again.

What is most strange is that when this "drop out" occurs the Ubuntu machine becomes completely useless. Trying to restart it via Applications > Quit > Reboot does nothing, no program (ie firefox) will launch and no command is processed through the terminal (ie sudo su, sudo reboot) does nothing. The only way out is to force restart the machine using the case reset button.

To me the "dropping out" sounds like a bandwidth issue or packets not being sent correctly but I can't explain the rest of it. I know it is not the router as when the "drop" occurs the desktop machine I work on can continue to use the internet. And I don't believe its the wireless card (although I did for awhile) because back in the day when it was running Windows XP there were no wireless problems.

The wireless card is a Netgear WG311 v3 using the correct drivers as when I first installed Ubuntu it was unsupported and I had to manually find and install the drivers after scouring the internet for information. Through my research on manually installing the drivers I didn't come across anyone who reported the problems I am having.

I have had this problem since 8.04.

Let me know if/what log files/outputs that may help find a solution and I'll put them up.

Thanks

---

### Post by haydnjones on 2009-04-30
-bump-

---

### Post by haydnjones on 2009-05-04
-bump-

---

### Post by haydnjones on 2009-05-08
-bump-

---

### Post by haydnjones on 2009-05-19
-bump-

---

### Post by rudy.b on 2009-05-19
I probably won't be much help, but if you haven't done so check the system log to see if you can find any common error message occuring each time this occurs.  To view the log:

System > Administration > Log File Viewer > messages

---

