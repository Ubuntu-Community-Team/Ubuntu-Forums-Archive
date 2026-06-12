---
title: "How to check if notifications are working correctly?"
date: 2009-04-30
forum: General Help
---

### Post by abcuser on 2009-04-30
Hi,
using Ubuntu 9.04 for couple of days and I haven't seen any notification yet. It looks notification system does not work on my PC. I have unpluged network cable and put it in again, I have increased volume, decreased it and no notification.

How to check if notifications are working?
Regards

---

### Post by Brandon Williams on 2009-04-30
You could download one of the python examples [from here](https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#Layout%20cases%20(with%20examples%20in%20C,%20Python%20and%20C#)) and see if it works. If a notification shows up when you run one of the example scripts, then the notification system is running and the problem is specific to the notifications that you are expecting to see.

---

### Post by abcuser on 2009-05-01
Brandon, thanks for help. I have downloaded python files and notifications are working well. I am just wondering when does some notifications appears, because this test notification is the first one I have seen. I tried increasing volume and removing network cable and USB cable and no notification at all. Can some one write some samples when notification appears?

---

### Post by Brandon Williams on 2009-05-01
With USB, it may depend on what you've got attached.

I get notification when I adjust the volume and when I connect to or disconnect from a network (wireless or ethernet). It seems that you should be seeing some notifications, too, since it's clear that notify-osd appears to be working correctly.

---

### Post by ddrichardson on 2009-05-01
> **Brandon Williams said:**
> You could download one of the python examples [from here]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#Layout%20cases%20%28with%20examples%20in%20C,%20Python%20and%20C#%29") and see if it works. If a notification shows up when you run one of the example scripts, then the notification system is running and the problem is specific to the notifications that you are expecting to see.
Just out of interest - you can send a message by opening a terminal and typing:```
notify-send "Message"
```

---

### Post by abcuser on 2009-05-02
> **ddrichardson said:**
> Just out of interest - you can send a message by opening a terminal and typing:```
notify-send "Message"
```
I get error that package is not installed:
"The program 'notify-send' is currently not installed.  You can install it by typing: sudo apt-get install libnotify-bin"
So I installed this package and I can execute notify-send messages. But I still think notification is not working correctly.

Does Ubuntu displays some notification if disk is full? I have tried this command: cat /dev/zero>FILE to fill disk (Don't try this on production computer!) and no notification was returned.

By the way I am using VirtualBox virtualization tool, do you think this is related to virtualization tool?

By the way, I have installed notify-osd on Ibex (on other virtual computer) too using this tutorial: [http://news.softpedia.com/news/Installing-Ubuntu-9-04-039-s-New-Notifications-in-Ubuntu-8-10-105221.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-04-039-s-New-Notifications-in-Ubuntu-8-10-105221.shtml) and notifications works fine on Ubuntu 8.10. If I unplug network cable I got error that network cable was unpluged. Interesting that notifications are working fine on my Ubuntu 8.10 but not on Ubuntu 9.04 where by default it should work.

Is there any way that some notifications can be omitted? Maybe some notifications are disabled?

---

### Post by ddrichardson on 2009-05-02
Are you running Jaunty in a VM?

---

### Post by abcuser on 2009-05-03
> **ddrichardson said:**
> Are you running Jaunty in a VM?
Yes I am running 9.04 in VM. I also run 8.10 in VM.
In 9.04 notifications are not working in 8.10 are working.

---

### Post by ddrichardson on 2009-05-03
I can't think of an obvious reason why that would happen, other than the change in OSD notification for Jaunty but it might be related to running in a VM. The best thing I can advise is to raise a [bug report]("https://bugs.launchpad.net/notify-osd/+bugs?search=Search&field.status=New&field.status=Incomplete&field.status=Confirmed&field.status=Triaged&field.status=In+Progress&field.status=Fix+Committed").

---

