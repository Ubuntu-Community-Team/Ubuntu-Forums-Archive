---
title: "Could not start kstartupconfig"
date: 2006-02-10
forum: Desktop Environments
---

### Post by jose0425 on 2006-02-10
**"Could not start kstartupconfig. Check your installation" I'm getting that message everytime i log on to KDE.**
[SIZE="4"]I'm getting that just after i changed my preferences in KDE in Preferences>Control Center.[/SIZE]
It may be that or it may be something else :rolleyes: . Anyway i'm getting just the message, nothing happens next to that, no crashes, no more messages (until next reboot), no malfunctions.
Can anyone please help me?:confused:

---

### Post by robgr85 on 2008-04-04
got the same problem.

help appreciated!

---

### Post by Jordanwb on 2008-07-04
I got the same error with ArchLinux after installing KDE. This is how I fixed it: 

At the login screen hit Ctrl-Alt-F1, this will bring you to a console window. Login,
Now run this command "sudo chown {YOUR_USERNAME} /home/{YOUR_USERNAME}" (minus quotes)

{YOUR_USERNAME} being your username (replace curly brackets). Then "sudo shutdown -r now"

[Edit] Whoa this topic is 2.5 years old.

---

### Post by canzel on 2008-07-12
I had the same problem after I changed the permissions on "home" directory.
Fixed it by booting up and using Alt+Ctrl+F1 Username (mysuername) Password (mypassword)
sudo chmod 755 home
(password)
shutdown -r now

A OK after that. Bit of a scare though. Will not try that again, apparantly the system is trying to build your profile in "home" instad of "home/yourusername"

---

