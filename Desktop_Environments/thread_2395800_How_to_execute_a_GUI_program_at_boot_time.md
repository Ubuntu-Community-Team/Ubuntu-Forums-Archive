---
title: "How to execute a GUI program at boot time?"
date: 2018-07-07
forum: Desktop Environments
---

### Post by deepakdeshp on 2018-07-07
[COLOR=#000000][FONT=&quot]Hello,[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]I am running Ubuntu 18.04[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]I have a program which generates a GUI screen. This should happen without manual intervention like keyboard or mouse[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]1.I require the program to execute automatically at boot time.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]2.The resultant gui should be visible on the console.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Any suggestions accepted with thanks[/FONT][/COLOR]

---

### Post by TheFu on 2018-07-07
You cannot automatically run any GUI program at boot time, but you can automatically run it after login.  
So, setup an auto-login account, then inside that account, run the program automatically at login.

How that is accomplished depends on which variant of the Ubuntu desktop you are running.  For mine, I use openbox, there is an autostart file, which controls the programs run automatically at login.  If you google for "ubuntu desktop guide" there should be a section in that to explain how to auto-start programs at login.  
[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en)

BTW, allowing a userid to auto-login without any human interaction is a security nightmare.

---

### Post by PaulW2U on 2018-07-07
Further to TheFu's reply the easiest way to set up an application to run after login is to add the application to "Startup Applications" in Tweaks (you may need to install **gnome-tweaks** first).

The screenshot below shows that I have Terminator to start every time I log into Ubuntu 18.04.

---

### Post by Dennis N on 2018-07-07
If the application to be run is not on the list of applications in Tweaks (shown with the + bar), then you can add an application to start at login with the 'Startup Applications' utility. In activities window, type in 'Startup Applications'. Click 'ADD' and supply the details. For example, I have a script I made that runs on login and this is the way I do it.

---

### Post by yancek on 2018-07-07
You can also run a script on login by using crontab and simply entering:  @reboot /path/to/script

---

### Post by TheFu on 2018-07-07
> **yancek said:**
> You can also run a script on login by using crontab and simply entering:  @reboot /path/to/script

That won't work for GUI programs if a GUI session isn't already up with a userid logged in.
It does work nicely for non-GUI programs, provided enough environment is provided.

---

### Post by yancek on 2018-07-07
> [COLOR=#000000]That won't work for GUI programs if a GUI session isn't already up with a userid logged in.[/COLOR]

Agreed, that's my experience also.  Forgot to add the 'on login' part in my earlier post although that is not what the OP asked.  I think your suggestion would probably be the closest solution to what was requested.

---

