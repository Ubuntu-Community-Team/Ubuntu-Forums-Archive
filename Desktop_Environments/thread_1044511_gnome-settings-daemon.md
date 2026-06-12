---
title: "gnome-settings-daemon"
date: 2009-01-19
forum: Desktop Environments
---

### Post by novalis112 on 2009-01-19
Greetings...

I have a Hardy Ubuntu install using the Alternate CD and selecting the LTSP option.  I manually moved the system over to authenticate from an Active Directory server and to attach to the Active Directory Domain.  Everything had been working fine for at least several months, then a few days ago it stopped working.  I have not touched the system since I set it up (i.e. no updates have been installed, unless Ubuntu did them automatically, which I believe it does not do...).  Specifically, the problem is the dreaded and unfortunately vague gnome-settings-daemon startup error message:

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

Now I have seen many threads and bug postings that start with this error, but like so many others, my problems quickly diverge from the existing descriptions.  Every time I log in, it takes about 10 minutes before anything happens, and then this error message comes up.  After acknowledging the error, another few minutes go by, and then my desktop background appears, and a few desktop icons.  No panels appear so without dropping to the console there is no way for me to launch any applications.  At least some keyboard shortcuts (Alt-Tab for example) still appear to work correctly.

When I try to launch GSD manually from the shell once I have logged in, I get the following output, and nothing else, it just hangs:

```
jtrammell@PC1142:~$ sudo gnome-settings-daemon
[sudo] password for jtrammell:
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.background" on line 232 overrides entry on line 151
xrdb:  "*Text.background" on line 238 overrides entry on line 192
process 6194: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5196.
This is normally a bug in some application using the D-Bus library.
process 6194: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
process 6194: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
process 6194: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
process 6194: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
```

If I try the same thing without sudo I get:

```
jtrammell@PC1142:~$ gnome-settings-daemon
** (gnome-settings-daemon:6504): WARNING **: Couldn't connect to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** (gnome-settings-daemon:6504): WARNING **: Could not get a connection to the bus
```

From what I've gathered, this is all pointing to the dbus-daemon.  When I search for the dbus-daemon processes (before launchcing GSD manually, afterwards I find many more dbus-daemon processes) I find the following:

```
jtrammell@PC1142:~$ ps -ef | grep -i bus
...... /usr/bin/dbus-daemon --system
...... dbus-daemon --fork --print-address 20 --print-pid 22 --session
```


Since the problem has started I have run apt-get dist-upgrade and that had no affect on the issue as far as I can tell.  I checked dmesg and to my untrained eye there doesn't seem to be anything too scary there.

So.  What now?

---

### Post by novalis112 on 2009-01-28
So nobody has any idea what these errors mean?  Am I asking this question in the wrong place?

---

### Post by luvinit on 2009-02-01
Hi,
you are not alone in this, I get something similar in both Hardy And Intrepid. My LTSP stopped working in October and I can't get anybody to help me. This never happened in Gutsy Gibbon, so I had the idea of reinstalling that but my current graphics card isn't recognised by it. Somebody at the #edubuntu and #ltsp IRC channels was very helpful, ran through my setup with me, but still had no idea why it wouldn't work. If I ever find out I will let you know.

---

### Post by novalis112 on 2009-02-03
Well, it is very reassuring to know that there are other people out there who have also found this software to spontaneously stop working, and who have also not gotten any answers as to why or as to how to fix the problem...  ;)

But seriously.  This system was a demo system that I put together to show a client that Linux was a viable alternative to Windows in their business.  If it weren't for this failure, and more importantly the complete and utter failure to find any resources for resolving the issue on my part, it would have replaced perhaps 20% of the desktops in the company.  It was looking very good but now after having the system be unusable for almost a month the project is about to die.

Every time I try to show Linux some love, it pushes me away.

---

### Post by theparanoidone on 2009-02-05
bump... me too? what causes this?

---

