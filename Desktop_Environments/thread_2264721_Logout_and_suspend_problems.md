---
title: "Logout and suspend problems"
date: 2015-02-09
forum: Desktop Environments
---

### Post by janosik-jozsef on 2015-02-09
Hi,
I installed Xubuntu 14.04.1 on my laptop and desktop PC and everything were OK, but somehow things changed, I don't know why and how I could correct them:
- after logout only the wallpaper and the mouse cursor is visible, and the system is idle (except I can move the cursor)
- after suspending (xfce4-session-logout --suspend) the power stops, but restarting the system with the power on button - although the machine is working - the display remains black,
on my laptop the logout works well: a login screen appears immediately, the suspend process is wrong but in this case it is a video driver issue as far as I know 

thanks

After a week the situation is better (again I don't know why):
- now the logout is Ok (login dialog appears)
[COLOR=#333333][FONT=Verdana]- [/FONT][/COLOR][COLOR=#333333][FONT=Verdana]resuming after[/FONT][/COLOR][COLOR=#333333][FONT=Verdana] 'xfce4-session-logout --suspend' with the power switch the login dialog asks the password, although after resuming from the suspend mode caused by timeout (PowerManager setting: Power saving mode after ... minutes inactivity) there is no need to bother with password. After installation it worked without login, but somehow things changed, but as far as I know I didn't make any setting that may cause this behaviour. How can I eliminate the login dialog, what is the difference between the two suspend modes?[/FONT][/COLOR]

---

