---
title: "How to swtich between GNOME and KDE?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by Physicist on 2006-06-28
Who could tell me how to swith the decault login desktop environment from KDE to GNOME if both are installed? Or this is not a valid question?

a Ubuntu/Linux newbie

---

### Post by aysiu on 2006-06-28
If GDM is your login manager, then your default will stay your default until you switch to another environment. Then you'll be asked if you want to make this new environment the default one or use it just for that session.

If KDM is your login manager, the default will always be whatever you used last.

---

### Post by Physicist on 2006-06-28
Well, could I invoke this socalled GDM under failsafe session or other way and set my login desktop environment to be Ubuntu. I might screwed up something yesterday evening as I installed an aweful lot of KDE packages. I mean I might by mistake set the desktop environment to KDE and actually my system don't have enough things to support that so I got this loopback thing: the system think I want KDE so it give me a Kubuntu login window but as I input my login info it fails to get all necessary resource to actually start a KDE desktop so it returns back to the login window. This is my guess. So, is there a way I can invoke GDM to set definitvely my default desktop environment to be GNOME which I happily used for the past couple of weeks?

---

### Post by aysiu on 2006-06-28
Press Control-Alt-F1.
Log in.
```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/kdm stop
sudo cp /etc/X11/default-display-manager /etc/X11/default-display-manager.backup
sudo nano /etc/X11/default-display-manager
``` Replace ```
/usr/bin/kdm
``` with ```
/usr/sbin/gdm
``` Save (Control-X), confirm (Y), and exit (Enter) ```
sudo /etc/init.d/gdm restart
```

---

### Post by xynamax on 2006-06-28
When you are at the Login/Splash Screen click "options"

Then you can select the session properties to launch Gnome instead of KDE, and on your subseuent logins you can set the Login to be "whatever my last one was"  

You shouldn't need to start a failsafe sessions or anything...


Or are you at a point here where your Login/Splash Screen is not displaying?

---

### Post by Physicist on 2006-06-28
Thank you for trying to help me out.
After running
```

sudo aptitude install gdm

```
I got error msg:
dpkg: error processing backuppc (--configure)
subprocess post-installation script returned error exit status 1
Errors were encountered while processing 
backuppc
(I do remember that I saw similar error msg yesterday after installing a lot of KDE related packages)
then the prompt come up again, shall I just forget about this error msg and go ahead implement
```

sudo /etc/init.d/kdm stop

```
?

---

### Post by aysiu on 2006-06-28
You can go ahead with the rest of the instructions, but that error message is probably the culprit responsible for whatever issues you're having.

**Edit**: [Apparently the problem you're experiencing isn't that common and seems to happen to German-speaking users](http://www.google.com/search?hl=en&q=dpkg%3A+error+processing+backuppc+%28--configure%29+&btnG=Google+Search).

---

### Post by Physicist on 2006-06-28
After implementing the third line of your instruction:
```

sudo /etc/init.d/kdm stop

```

The the command line prompt disappear and I get a blue kubuntu logo with a dark blue status bar thing
under it, and this thing keep in the screen just for ever, not really any progress shown within that status bar.

BTW, I don't speek any German at all.
Shall I just give up and remove everything from my laptop and start a new installation now? I have been doing nothing but trying to get a clue what is going on the whole day. My ....

---

### Post by aysiu on 2006-06-28
You know, when a Google search result for an error turns up fewer than 50 results, I generally give up and go for a reinstall.

---

### Post by Physicist on 2006-06-28
[QUOTE=aysiu]You know, when a Google search result for an error turns up fewer than 50 results, I generally give up and go for a reinstall.[/QUOTE]

OK. What would you suggest to me to avoid such seemingly unnecessay hassle after this new installation? Yesterday evening, it was just a little thought that I should have an IDE for tex typesetting that invoked me to go thru all these. Is this wish too luxurious for Ubuntu?

I hope all common software can have an installation guide here someday.

Kile isn't that rare a software for academic community. And I am sure somebody are using Kile on a Ubuntu. Duh, I lived happily with WindowsXP+WinEdt.

---

### Post by Delkster on 2006-06-28
I was left wondering if you couldn't get to the graphical login screen at all or if starting the desktop just fails after logging in.

In the latter case, in your situation I'd just try to find the option for selecting your 'session' in the login screen and choosing Gnome instead of KDE. From there on you could proceed to fixing anything else that there may be to correct.

GDM is the display manager (login manager) that ships with Gnome while KDM is its equivalent in KDE. You can, however, log in to either desktop environment from either display manager, so if at least one of them starts up and allows you to log in, you should be able to get Gnome running.

---

