---
title: "KDE time zone service"
date: 2016-07-09
forum: Desktop Environments
---

### Post by tschill on 2016-07-09
I am used to KAlarm, because seemingly this is the best alarm app one can find to launch text alarms. In my previous computer running on 14.04 I had no problems with KAlarm. My new computer runs now on 16.10 and after startup it shows the message

>  Time zones are not accessible:
KAlarm will use the UTC time zone.

(The KDE time zone service is not available:
check that ktimezoned is installed.)



Indeed, KAlarm has only UTC time zone available, which is not my time zone. I[ found the developers website]("http://www.astrojar.org.uk/kalarm/bugs.html") and there s/he says:

> Sometimes the only time zone which KAlarm makes available may be the UTC  time zone. This will result in alarm times being offset by a fixed  amount dependent on your local time zone. This fault occurs in two  different circumstances:
[LIST]
[*]When running the KDE 4 version of KAlarm under a non-KDE desktop,  e.g. Gnome, this can be due to a bug in the KDE libraries (kdelibs). To  fix this, kdelibs 4.4.1 or later must be installed. 
[*]The KDE time zone service application, ktimezoned, may not be  installed. A startup warning about the non-availability of the KDE time  zone service has been added since KAlarm version 2.6.0. 
[/LIST]


I checked in Synaptic manager and [I do have kdelibs 4:4.14.16 installed]("http://storage9.static.itmages.com/i/16/0709/h_1468094672_3737991_683cdffb77.jpeg"). So this doesn't seem to be the problem. But I was not able to find any information, why KDE time zone servie ktimezoned is not installed now under 16.10. Synaptic doesn't show anything when searching for ktimezoned. Imho I didn't have to do anything under 14.04 that made the KDE time zone service available. 

I appreciate you taking time reading all this and I am very grateful for any suggestions.

---

### Post by tschill on 2016-07-09
[I found a workaround here. ]("https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/1512107")
After installing Plasma Windowed and a restart, time zones were available. But still internally KAlarm seems to use UTC time. If I set the alarm to 21:00, the alarm created will show then the UTC time 22:00 and release the alarm at 22:00. Hm.

But I also noticed now the tick box "Ignore time zone". This solves the problem, because now KAlarm strictly uses the system time. Strange nonetheless and quite annoying, because KAlarm has the preset to untick the "Ignore time zone" box.

Another way to solve this is to set the KAlarm preset for time zone to UTC. Now an alarm generated shows the UTC time instead the computer system time, but releases the alarm at the desired system time. None of this is of course fully satisfactory. And it worked so well in 14.04!

---

