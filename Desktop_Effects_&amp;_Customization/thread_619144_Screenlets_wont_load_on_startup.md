---
title: "Screenlets wont load on startup"
date: 2007-11-21
forum: Desktop Effects &amp; Customization
---

### Post by JaggedOne on 2007-11-21
I just installed screenlets on 7.10. I start up each screenlet and it works fine, I even check the "Automatically start on login" button. When I reboot or log out, none of the screenlets start up and the auto start button is unchecked.

Also, whenever I start the screenlets manager I get this error.

Unable to connect or launch daemon. Some values may be displayed incorrectly.

I thought that may have something to do with it.

Btw, I did do quite a bit of searching for the answer before I posted this like I'm supposed to do. I found other threads on the subject but no working answers. Is there an answer out there?

---

### Post by h3hound on 2007-11-21
Getting the same issue except I have two Screenlets that operate normally, clear weather, and clear RSS.

At first login I tried running the Screenlets Manager from a terminal and got this:

Error in ScreenletsManager.connect_daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.ScreenletsDaemon was not provided by any .service files
Trying to launching screenlets-daemon ...
ScreenletsDaemon running ...

The manager starts the daemon for the session and things then work.  Looks like some 'which came first, chicken or the egg' situation for some screenlets.

---

### Post by pjones0404 on 2007-11-21
i am having the exact same issue. I receive the same error when launching the applet manager as well as the error when launching from terminal. 

some of my screenlets will launch automatically while others completely refuse to. the ones that work consistently are clear calendar, weather clock, and sticky notes. almost every other one that i have tried will not start every time i login. i can manually start them and it is fine for that session but it never carries over to the next time i login. 

i have even tried adding them individually to the sessions-startup applications and there is no difference. i have also went to the session and choose to save current session. yet it does not save it either. 

i would very much like to find out why this does not work. i will keep a close eye on this thread to see if there is any resolution as i have googled it to death...

---

### Post by vapore0n on 2007-11-21
I run them manually in the sessions.
Which is the same that setting the "launch at startup" thing would do

example from sessions manager.
to run calendar I run this:
/home/zip-it/.screenlets/Calendar/CalendarScreenlet.py > /dev/null

I did modify the source code of the screenlets application, so that it defaults to "keep below", else sometimes the screenlets would show above and wouldnt want to go below.

---

### Post by meoblast001 on 2007-11-23
> **JaggedOne said:**
> I just installed screenlets on 7.10. I start up each screenlet and it works fine, I even check the "Automatically start on login" button. When I reboot or log out, none of the screenlets start up and the auto start button is unchecked.

Also, whenever I start the screenlets manager I get this error.

Unable to connect or launch daemon. Some values may be displayed incorrectly.

I thought that may have something to do with it.

Btw, I did do quite a bit of searching for the answer before I posted this like I'm supposed to do. I found other threads on the subject but no working answers. Is there an answer out there?

Easy... You told the daemon to launch those widgets when the daemon starts, but you never told GNOME to launch the daemon when your session starts. Go to System > Preferences > Sessions. Click Add. Type "Screenlets" in the Name field and type "usr/local/share/screenlets-manager/screenlets-daemon.py" (excluding quotation marks) in the Command field. Click OK. Click Close. Logout. Login. Most (if not all) of your widgets should appear. I only noticed problems with the calender widget. Also, the "
Unable to connect or launch daemon. Some values may be displayed incorrectly." error is no problem. I wish you luck. =)

---

