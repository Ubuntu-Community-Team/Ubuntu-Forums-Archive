---
title: "Maximum number of clients reached"
date: 2010-02-18
forum: Desktop Environments
---

### Post by wfaulk on 2010-02-18
In the last week or so, I've frequently been running out of X server client connection slots and getting "Maximum number of clients reached" errors.  For example, I'm getting it right now and I'm running 3 pterms, Chrome, and Thunderbird; I've even killed my panel.  'xwininfo -root -children' produces what seems to be an absurd number of X clients (150-ish, when it's able to make a connection), even immediately after Gnome/Xfce startup.

It doesn't take long.  A day at most.  I've had this system up and running for months, and this just started happening.  I did install some X development libraries (x11proto-core-dev, libmotif-dev, x11proto-print-dev, and x11proto-xext-dev plus their dependencies) about two weeks ago, but this problem has not been happening that long.  I've installed other packages, but nothing that would seem to have any relation to this problem.

I've logged out and in, rebooted, and changed from Gnome to Xfce, and none of the changes helped.  Can anyone help?  Even any ideas about how to track down what programs are creating the connections in the xwininfo output would help.

---

### Post by 8forty on 2010-03-12
I'm getting the same thing, and have discovered that if I close chrome, I'm able to open new windows again.  When I restart chrome with the same windows, I don't run out of clients again for another few hours to a day.  This is on 64-bit Jaunty.

Note that I don't have the same problems on my 32-bit Jaunty machine.

---

### Post by teh zcat on 2010-03-15
I just encountered this problem after installing the Lastpass extension for Google Chrome. Disabling the extension solved the problem.

---

### Post by 8forty on 2010-03-15
That's interesting, as I also recently added lastpass (and chrome).  I had used lastpass with firefox for months without any problems.

---

### Post by bob lp on 2010-03-16
Please give this a try (you will need to first uninstall because the version hasn't changed), we are hoping it is fixed:

[https://lastpass.com/lpchrome_bin.crx](https://lastpass.com/lpchrome_bin.crx)

Thanks
Bob (from LastPass)

---

### Post by ngohaibac on 2010-03-17
> **teh zcat said:**
> I just encountered this problem after installing the Lastpass extension for Google Chrome. Disabling the extension solved the problem.

Thanks for that, I was looking for the solution for days. Yesterday, I suspended my PC and today when come back I can't even see anything display on my screen and had to restart PC again. After several hours I can't open any windows.

I tried to close all Chrome windows, everything works fine again.

Wish Lastpass fixes this issue, since it is my favorite extension in Firefox. If not, I will use Firefox only :)

---

### Post by tommy_vercetti on 2010-03-17
> **bob lp said:**
> Please give this a try (you will need to first uninstall because the version hasn't changed), we are hoping it is fixed:

[https://lastpass.com/lpchrome_bin.crx](https://lastpass.com/lpchrome_bin.crx)

Thanks
Bob (from LastPass)

Thanks, that seems to have solved the problem.:popcorn:

---

### Post by ngohaibac on 2010-03-17
> **bob lp said:**
> Please give this a try (you will need to first uninstall because the version hasn't changed), we are hoping it is fixed:

[https://lastpass.com/lpchrome_bin.crx](https://lastpass.com/lpchrome_bin.crx)

Thanks
Bob (from LastPass)

Work like a charm. I can confirm that there is no error at all after install that package.

Everyone should notice about that. And I think that thread is solved.

---

### Post by 8forty on 2010-03-17
Worked for me too.

---

### Post by teh zcat on 2010-03-17
Fix works for me too. Thanks, Bob from Lastpass!

---

### Post by lonerunner on 2010-12-25
I dont have lastpass extension, and i dont use chrome i use firefox and i get same error, it happens when a lot of processes or things are open in ubuntu, it doesnt have anything related with firefox and chrome. if i cant open something i close anything i have open. For example i have 3 file browser windows open and i want to start skype, i just close one browser window and i can start skype, how many things i close that many things i open. If i reach maximum number of clients and close 5 tabs in firefox or 3 tabs in firefox and 2 browser windows i can open 5 new things. So i guess its not related to lastpass extension, its some global settings restriction

---

### Post by ayreon2084 on 2011-05-10
I was trying to solve this issue for weeks... but i have the solution now.

For me at least the guilty was the MinimizeToTray plugin in Thunderbird! Uninstalling that crap finally solved the problem.

Hope it helps somebody

---

### Post by winz on 2011-05-20
> **ayreon2084 said:**
> I was trying to solve this issue for weeks... but i have the solution now.

For me at least the guilty was the MinimizeToTray plugin in Thunderbird! Uninstalling that crap finally solved the problem.

Hope it helps somebody

ayreon2084, you rock!!! Thank you. It helped me too!

---

### Post by graben3 on 2011-08-21
I had the same problem : ie could not open any program and closing one window allowed me to open another. 

Seems to me that disabling the minimize to tray plugin of thunderbird solved the problem !

Thanks !

---

### Post by graben3 on 2011-08-21
> **winz said:**
> ayreon2084, you rock!!! Thank you. It helped me too!

Thank You !

---

### Post by graben3 on 2011-08-21
To replace the MinimizeToTray plugin, there is this one that works : FireTray 0.3.1

---

### Post by ianni67 on 2011-11-22
Yes I can confirm that minimizetotray 1.0.8 was crapping the whole system (Ubuntu 10.04).
I removed it and everything went fine.
THANK YOU!

---

