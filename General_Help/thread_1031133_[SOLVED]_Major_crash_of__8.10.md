---
title: "[SOLVED] Major crash of  8.10"
date: 2009-01-05
forum: General Help
---

### Post by slylock on 2009-01-05
First I am a new user to Ubuntu and Linux. I am running Ubuntu 8.10 and Windows Xp SP3 V2 on a Pentium 4 1.8ghz 512Mb RAM.
the drive is not partioned. I can acces some files thru C:/ thru MY COMPUTER on my windows. 

I was updating my software, as requested by the synapsis program. During the install portion the PC crashed. I do not know why! the screen went black and the PC froze. I hard rebooted the system and logged back into ubuntu. I then got awole bunch of error report messages. I tried to log the reports but the website was asking alot of questions I couldn't answer. Like what went wrong, and heck I don't know the lest about Linux or Ubuntu. Then the desktop started to look funny, not right in the sense of looks, I could not see the open windows on the Panel, and alot of the Icons where not matching the theme. I ran the update manager agian and tried to finish the install, but It told me it could not get a "Lock" then it froze agian. I hard rebooted the system agian. Ubuntu would not run. I got an error that I have a BIOS bug. 
So I then rebooted and logged into Windows and came here. Does anyone know what is going on? Is there a way to get my Ubuntu running agian, I only Installed 2 days ago and have not had a chance to performe a back up. but I have filles on Ubuntu I do not want to loose.

Slylock

---

### Post by blazemore on 2009-01-05
I'm sorry to hear you're having difficulties.

Maybe you could copy and paste some of the error messages? We might be able to assist you a little better.

Also, if you ignore the error messages and try running the upgrade again, perhaps that will fix the problem.

If it freezes again, try waiting. If it's still frozen after 60 seconds, then we need to work out what package is causing the problem. But try running the upgrade again first.

---

### Post by slylock on 2009-01-05
I get the BIOS error message during start up. I can no longer access Ubuntu. The system told me I need to (something near this) 'djkg config a* , something about clearing the cache of the updater in the command line... I can access ubuntu root files thru windows as well as the command line...Basicly the updater failed and the system is now unstable. I need to revert the updates to the originale files from the inital install. I am just a week new to linux. So I do not know any root commands and have no idea how to do this.

---

### Post by blazemore on 2009-01-05
Oh right Okay I'm assuming you're on another PC now so if not you might want to write this down.
When your computer boots up, choose Ubuntu... Recovery Mode.

Let it boot, and you get a menu.
Run them all. Let them all finish, errors or not.

Then choose to drop to a root shell, and run the following command:

```
dpkg-reconfigure --force --all
```

---

### Post by slylock on 2009-01-05
ok, I am on the same PC. I have WIndows and Ubuntu both installed. OK, I only get 2 choices....Ubuntu or Windows XP. When I choose to load Ubuntu it goes into command line like normal...Thats when I get the BIOS error. The PC stops working because Ubuntu can not access the shell. I have the ability to access command line thru windows. Can I use this command in windows? I am assuming this is a reset/clear cache command for the updater???

well ok I can not access thru Windows...it is a different tool than I thought. I am going to shut down and get you that error message about BIOS.
thanks

---

### Post by sendblink23 on 2009-01-05
I would simply recommend by your issue.. since its huge..  By Crashing.. during updates


Well ... Actually in your Case.. WIPE your current Ubuntu with the live CD

And Re-Install it to the same place, that way you won't encounter that issue..


One question.. why do you say.. you didnt partition it? I'm guessing you did.. since you have the choice in the booting of your computer (Ubuntu or Windows).. you just didn't notice it through instalation on LiveCD.

Anyways...  just Install it over the Same partition of you Current Failed Ubuntu..  you will have a new Clean working Ubuntu that way. (you can do all that through the LiveCD)

---

### Post by slylock on 2009-01-05
OK, I went thru the recovery menu and recovered to Kernel 2.6.27-7. I am in Ubuntu now. The issue seemed to be in the update to Kernel 2.6.27-9. i did not run the Live cd. I simply extracted the Ubuntu ISO and Installed it on my HD thru Windows. They share the same drive, Ubuntu just has 30GB attached to it, the only true partition is the swap.

Thank you for the direct into the recovery menu....I need to press escape to get into that menu! I was having a Kernel Panic error as well as the BIOS error.

(I am not resolving this quite yet, I want to restart and see what happens. Keep your fingers crossed for me!)

---

### Post by sendblink23 on 2009-01-05
Well good to know that other method of installing it... 

Anyways.. I hope it does go through finally the Restart...


If goes well ...  don't forget to mark.. *Solved on your thread

---

### Post by slylock on 2009-01-05
OK!!! It seems it also updated to Kernel 2.6.27-9 at the same time it repaired the files!!! ok so its resolved! Thanks to everyone for there help!

---

### Post by theacerguy on 2009-01-05
i would just reinstall ubuntu mines 1.6ghz atom aspire one 512 mb it is fine for me (even after 437 updates at once!!) just use a live to back up then reinstall

---

### Post by slylock on 2009-01-05
I thought I changed the thread Title, but it seems only to change on the first post. How do I Change the thread title, so that it will show resolved?

Thanks

---

### Post by blazemore on 2009-01-05
No need, it's done.

One day, they'll make me a mod...

---

