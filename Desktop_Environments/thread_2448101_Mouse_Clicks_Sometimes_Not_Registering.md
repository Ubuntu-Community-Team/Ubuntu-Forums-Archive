---
title: "Mouse Clicks Sometimes Not Registering"
date: 2020-08-01
forum: Desktop Environments
---

### Post by yslited.linux on 2020-08-01
When I am working on a certain spreadsheet in LibreOffice Calc on my Ubuntu Laptop with xubuntu-desktop installed, often after a while mouse clicks would stop registering no matter where I click on the screen. To have the mouse clicks register again, I would have to CTRL-ALT-T a new terminal and run the command "xfwm4 --replace &" to get mouse clicks to work again.  I do not run into this issue with mouse clicks while using any other application, including running LibreOffice Calc with different spreadsheets open.  I've searched and searched all over the web for a solution to get rid of the problem entirely, but have not found any solution that has worked.  I am pretty sure that this isn't a hardware issue, because when I run "sudo -H libinput debug-events" in a separate window while the issue is occurring, mouse clicks I make do show up as events printed out in the terminal window. I am really tired of this reoccurring issue and would greatly appreciate it if someone could help me solve this issue. I'll also be more than happy to post any logs from my computer that may help others in determining what the cause of this issue is.  Unfortunately I won't be able to post a copy of the spreadsheet that this issue is associated with because that would be a FERPA violation.  FYI I am running Ubuntu 18.04.4 LTS, kernel version 5.4.0-42-generic #46~18.04.1-Ubuntu SMP Fri Jul 10 07:21:24 UTC 2020, Xfce version 4.12, X.Org X Server version 1.20.8, xfwm4 version 4.12.5 (revision d730ebb6), LibreOffice version 6.0.7.3 00m0(Build:3).

- UPDATE: even after running "xfwm4 --replace &" clicks don't register inside LibreOffice Calc with the spreadsheet I've mentioned. But if I CTRL-ALT-T a new terminal and type "soffice --calc" and I click around on the blank spreadsheet that the command opens mouse clicks are temporarily restored, and then after a while the clicks would stop registering again inside the spreadsheet.

---

