---
title: "How run notify-osd as regular user not root?"
date: 2014-02-17
forum: Desktop Environments
---

### Post by DrAlbert on 2014-02-17
Hi
I installed kubuntu 13.04 on my laptop. I enjoying using KDE but I think the bubble notification in gnome is more beautifull than KDE. I installed notify-osd and I can see in ksysgaurd that there is a proccess notify-osd but the problem is that it is started as root not a regular user. for example if i use a command like this:
sudo notify-send "hello there"
I can see the bubble comming up in upper right corner but if i use the command without sudo like:
notify-send "hello there"
the notification will comes by knotify4 in lower right corner. I tried to kill notify-osd and start notify-osd again as a regullar user but it sys:
```


user1@dentmoc-Rev-1-0:~$ /usr/lib/x86_64-linux-gnu/notify-osd


** (notify-osd:8137): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


** (notify-osd:8137): WARNING **: Another instance has already registered org.freedesktop.Notifications


** (notify-osd:8137): WARNING **: Could not register instance

```
so how can I use notify-osd bubble notification instead of knotify4 and start notify-osd in startup as regular user not root?

---

### Post by tgalati4 on 2014-02-17
You might run into some issues.  Each notification framework is supposed to run in the desktop environment that it is programmed for.  There is probably no issue with running both knotify and nodify-osd, but KDE apps will still send notifications through knotify.  Does *notify-send* work?

---

### Post by DrAlbert on 2014-02-18
as i mentioned before notify-send works. if i use notify-send alone it will use knotify to send notification but if i use sudo notify-send it uses notify-osd and will send bubble notification. if you notice the section of top command about these 2 proccess you can find out that notify-osd is running as root user. I don't know this is true or not but it seems that root user is running gnome and if i use sudo notify-send it will send bubble notification.
```

 8768 user1     20   0  750m  25m  17m S   0.0  0.6   0:00.76 knotify4
 8849 root      20   0  585m  15m  10m S   0.0  0.4   0:03.52 notify-osd

```
I think if i run notify-osd as user1 (not root) the problem will be solve. but i can't run it and it will produce error.
thanks for reply.

---

### Post by tgalati4 on 2014-02-18
You might have to go into the source code for *notify-osd* and change it.  Does it matter if you start *notify-osd* first then start *knotify4*?

You are going to have to get into the details:  [https://wiki.ubuntu.com/NotificationDevelopmentGuidelines](https://wiki.ubuntu.com/NotificationDevelopmentGuidelines)

[https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)

What is the (annoying) behavior that knotify causes?  Perhaps there is a work-around or tweak rather than use another notification framework that was not designed to work cleanly with KDE.

Perhaps use *notification-daemon* which is the older framework (Gnome2 flavor) versus *notify-osd* (Gnome3/Unity flavor).

More edge cases with *notify-osd*:  [http://askubuntu.com/tags/notify-osd/hot](http://askubuntu.com/tags/notify-osd/hot)

---

### Post by DrAlbert on 2014-02-18
[ATTACH=CONFIG]250469[/ATTACH]
I uploaded a screenshot of 2 notification (you can see it above). nothing is wrong with knotify but I don't like the shape of it. I like the notify-osd bubble notification with rounded corners. I prefer notify-osd and knotify seems ugly to me.

```
[COLOR=#000000]Does it matter if you start [/COLOR]*notify-osd first then start [I]knotify4?*[/I]
```
I don't know how start notify-osd first. if I kill [I]knotify4 it will start again automatically. sorry but I'm not expert to do programming for it.
all of notification act like that example. so if I run guake , its notification will show with knotify at button but if I run sudo guake its notification will be bubble. I can't understand the reason.[/I]

---

### Post by tgalati4 on 2014-02-18
If you read through the links I provided, the notification framework actually sends the message to several frameworks depending on what you have installed.  So sometimes you will get one or the other depending on permissions and what notification commands are used by each application.  I don't know of a clean way to do what you want.  Try using the Unity desktop.  I'm sure the notifications will work correctly.

---

