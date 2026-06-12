---
title: "Difficulty running Gnome apps"
date: 2006-03-18
forum: Desktop Environments
---

### Post by Mr Squiddy on 2006-03-18
Hi,

under 5.10, if I try to run certain Gnome/GTK apps in KDE, the apps usually fail.  Often the skeleton of a window will appear but I get a 'window not responding' message if I try to close it.

So far this has happened with anjuna, screem and bluefish.  I also get a similar response with Totem media player.

Do I need to load some more libs, or make a config change?

TIA

---

### Post by aysiu on 2006-03-18
Has it always been this way or has something changed recently (installed a new icon theme or something, for example)?

---

### Post by Mr Squiddy on 2006-03-18
I have had Kubuntu running for a couple of weeks now.  I have only really noticed the problem today.  I did run Automatiks today, it was this that installed the development apps which didn't run properly.

---

### Post by aysiu on 2006-03-18
Can you try creating a new user, logging in as that user, and then trying to launch those applications?

This is a control test.

If the new user can launch the applications successfully, it means that there's something wrong with your *user configuration files*.

If the new user experiences the same problem launching those applications, it means there's something wrong with *how the applications were installed*.

---

### Post by Mr Squiddy on 2006-03-18
Well, the solution was slightly unexpected.

I ran the apps using strace.  All three apps stalled at a point where they tried to connect to a service running on the loopback interface.  I tried to ping the loopback (127.0.0.1 as I am sure you know) without success.  I then tried adding the address to the lo interface using ipconfig.  I got an error message but I could then ping the lo interface.  After that all the apps ran just fine.

Odd.

---

