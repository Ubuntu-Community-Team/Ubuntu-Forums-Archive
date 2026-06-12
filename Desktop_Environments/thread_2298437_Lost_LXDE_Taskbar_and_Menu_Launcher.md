---
title: "Lost LXDE Taskbar and Menu Launcher"
date: 2015-10-11
forum: Desktop Environments
---

### Post by meltingpot2015 on 2015-10-11
Running Ubuntu 14.04 Trusty, found that the Task bar and Menu Launcher disappeared and reloaded automatically now and then. One day it would do this, then a couple of days later, again. But the third occasion, it would disappear, but would not reload.:(


I am running the LXDE Desktop. Sidenote: to find what desktop you are running. Press Ctrl-Atl-T, then type:
```
echo $XDG_CURRENT_DESKTOP
``` 
To solve taskbar problem, do not try the solution at  
[http://askubuntu.com/questions/475296/unity-launcher-and-menu-bar-disappeared-in-14-04](http://askubuntu.com/questions/475296/unity-launcher-and-menu-bar-disappeared-in-14-04) 
The solution ```
sudo service lightdm restart
``` then entering sudo password will restart your session. Yes, It will log you out. You will lose unsaved work. I found out the hard way!. The link above informs us in bold caps letters, but easily done..read one of the comments. I reckon the warning has to be at the top before running the command.
 
The solution for this thread (reloading taskbar only) is at [http://ubuntuforums.org/showthread.php?t=2207501&p=12938814#post12938814](http://ubuntuforums.org/showthread.php?t=2207501&p=12938814#post12938814) 
However, instead of command ```
lxpanel config
```use command ```
lxpanel
``` 
This will re-load your taskbar, the menu launcher (mine used to be on the left of the screen and was set to auto-hide) has not reappeared, but I never used it anyway. I reckon a restart would restore that. Not particularly concerned about it, as you would be able to do everything you were able to using the task bar again.:D

---

### Post by meltingpot2015 on 2015-10-27
Have discovered some issues with the reloaded taskbar. It does not group multiple occurences of the same application together. If you have 20 pdf files or txt files opened then your taskbar is going to be very crowded. See pic below:

[IMG]http://www.keepandshare.com/doc8/7977/lxdesktop-task-bar-manual-restart-png-19k?da=y[/IMG]

Also, the battery charge level indicator, wi-fi signal strength, and date on the taskbar has disappeared. See pic below what the taskbar looked like to begin with:

[IMG]http://www.keepandshare.com/doc8/7976/ubuntu-lxde-panel-how-it-looks-initially-png-29k?da=y[/IMG]

The icons on the left have changed, after restarting lxpanel. 

Can anyone suggest how to troubleshoot the causes for lxpanel restarting and sometimes stopping completely. Is there any logfiles I could look at or enable for further troubleshooting. 


This issue could be graphics card driver related - When I move windows, the refreshing takes unusually long.

---

