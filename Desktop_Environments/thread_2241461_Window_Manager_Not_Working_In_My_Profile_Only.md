---
title: "Window Manager Not Working In My Profile Only"
date: 2014-08-26
forum: Desktop Environments
---

### Post by NoSalt on 2014-08-26
Hello All,

    I was using XUbuntu 12.04 and everything was working great. As I use this machine as a server, I do not log into the desktop very often, and I do most of my updates over the network via SSH. I am not sure if my problem happened after an update, but one day I logged into my account and the window manager was not working. None of the windows I opened had any title bars, along with the accompanying min/max, close, etc. buttons. I also cannot right-click on the desktop and I cannot switch to a different desktop using the desktop switcher. I created a new account and logged in with that, and everything works perfectly. A few days ago, I got prompted to upgrade to 14.04, so I did in the hopes that whatever was "broken" would be fixed with the update. As it turns out, that was not the case. The update went well, and I still have my issue in my profile only. Whenever I log in as another user, everything works great. I did a brief Google search for the issue and the only thing I could find was the command "xfce4 --replace", but I do not seem to have the "xfce4" command. I have a lot of "xfce4-xxxx" commands, but no "xfce4" by itself. Does anybody know what could be causing this, and possibly have a fix for me?

Thanks for taking the time to read. Have a great day. :-)

---

### Post by ajgreeny on 2014-08-26
Is xfwm4 running in the Settings-manager ->Session and Startup ->Session tab?

If it is not listed you need to start it with alt+F2, command xfwm4 and then check that it is showing and has the Restart Style of "Immediately".  If it is running perhaps a restart will help, though I presume from what you say that this still happens after a reboot of your system?

---

### Post by NoSalt on 2014-08-26
Yes ... I have rebooted multiple times and the problem persists. It wouldn't be so frustrating if it weren't only my profile that is messed up.

---

### Post by ajgreeny on 2014-08-26
> **NoSalt said:**
> Yes ... I have rebooted multiple times and the problem persists. It wouldn't be so frustrating if it weren't only my profile that is messed up.
And what about xfwm4 running?

---

### Post by NoSalt on 2014-08-26
I'm not sure what you're asking. When I "ps aux | grep xfce4" I get the following processes:

xfce4-session
xfce4-power-manager
xfce4-panel
xfce4-volumed

However, I do not have a binary named "xfce4" which I can run as "xfce4 --replace". All my binaries in /usr/bin are "xfce4-xxxxxxx".


I just re-read your question. When I "ps aux | grep xfwm4" I get nothing.

---

### Post by ajgreeny on 2014-08-27
Run command **which xfwm4** to see if it is even installed?  If not install it and then logout and in again, unless, of course, you are running a different window manager such as openbox or compiz and wish to continue using that one.

---

### Post by NoSalt on 2014-08-28
Running "which xfwm4" I get "/usr/bin/xfwm4".

So I tried running "xfwm4 --replace" again, but apparently I cannot do this via Putty, while at work. I'll give it a shot when I get home.

---

### Post by NoSalt on 2014-08-29
Ok ... so I finally got home and tried "xfce4 --replace", and it worked perfectly! So my two questions are (1) Why did this work (i.e., what went wrong to make this work), and (2) How do I prevent this from happening again, say when I restart the server again?

Thanks again to all who took the time to read and respond.

---

### Post by ajgreeny on 2014-08-30
As it is a server does the xsession start by default or do you usually boot to cli?  A gui xsession is not the way most servers are run and could be the cause of the problem.

Try removing all the saved sessions in ~/.cache/sessions if there are any which you can do from the **Settings-manager ->Sessions and Startup** and make sure that you have not set the system to remember sessions when shutting down.

Hopefully that will do it.

---

