---
title: "Software Update don't show updates"
date: 2017-04-27
forum: Desktop Environments
---

### Post by jrrpnani on 2017-04-27
Hi:

I have installed Ubuntu Gnome 16.04.2 in a new computer. In my previous computer, with the same Linux distribution, the Software Update show me a pop-up notification when was necessary to update. But I can't have a notification when are updates in this new computer system.
I have check my preferences in the system updates and they are sets to make the check daily. I know that can check my updates with apt-get, but in my old computer that was not necessary.
Is there any way to test if the system make the correct update checking by himself?

I have found here ([https://ubuntuforums.org/showthread.php?t=2330407&page=2&highlight=software-updates](https://ubuntuforums.org/showthread.php?t=2330407&page=2&highlight=software-updates)) a possibly solution. I have to check it.
> I solved this problem with the following settings in /etc/systemd/system/timers.target.wants/apt-daily.timer:

Code:

[Unit]
Description=Daily apt activities
DefaultDependencies=yes
After=network.target

[Timer]
#OnCalendar=*-*-* 6,18:00
#RandomizedDelaySec=12h
#AccuracySec=1h
#Persistent=true
OnBootSec=5min
OnUnitActiveSec=1d

[Install]
WantedBy=timers.target



---

### Post by sp40140 on 2017-04-28
Can you provide screen shot of the settings? I know you have set the daily checks, but there are other options on that screen which I want to confirm. (One example is " canonical-supported free and open source software (main) checkbox. Is it checked?)

---

### Post by LastDino on 2017-04-28
And might as well update your preferred server settings and update the list.

---

### Post by jrrpnani on 2017-04-28
My setting are in Spanish, but you can see what is cheeked:

[IMG]http://webs.ono.com/jrramosp/imagenes/fig1.png[/IMG]
[IMG]http://webs.ono.com/jrramosp/imagenes/fig2.png[/IMG]

---

### Post by sp40140 on 2017-04-28
These look ok to me. May be the delay is related to the server you have selected currently.

---

### Post by Dennis N on 2017-04-28
You have your setting to check for updates daily, but you will not get notifications of the security updates at all, because you have opted to "download and install automatically" for those. For other updates, you have opted to display these only "weekly".

Those settings are the default settings in 16.04.2 and also 17.04 release. A few days ago, I also installed Ubuntu Gnome 16.04.2. I changed my settings to "display immediately" for all updates, which I prefer. Instead of a pop up notification, the software updater launches (see screenshot attached), and it will be difficult to miss.

---

### Post by jrrpnani on 2017-06-14
I received an update of the Software application. And also I changed an option of the updates settings to "display inmmediately" (like Dennis N suggest) and now I have notifications of the system updates.

---

