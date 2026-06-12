---
title: "howto config notifier to require ack before vanish"
date: 2011-01-03
forum: Desktop Environments
---

### Post by SaintDanBert on 2011-01-03
All sorts of system events and activities result in a notifier dialog in the top right screen.

Where are all of these built-in notifiers stored and configured?

How do I configure a notifier to remain on-screen until "forever" or until the end-user selects OK or similar as acknowledgement?

For example, I have a script that touches a server from time to time.
If that touch does not happen, I want a notifier. If this fails when the end-user is not around or not watching, I want it to stay on screen until the end-user selects OK or similar to ack that they know about the outage.

Merci d'avance,
~~~ 0;-Dan

---

### Post by Krytarik on 2011-01-03
To display such a "notification bubble" you can use the "notify-send" command from the "libnotify-bin" package. To show a confirmable message window use it with the option "-t 0". I've just yet learned it either, nice!:-)

---

### Post by SaintDanBert on 2011-01-03
THANKS!  That is a nifty trick.  I'll be sure to use it.

I have need to alter one or more built-in notifiers and cannot find where
they are stored and configured. 

I've done a **find ... -exec grep** search without success.
Any ideas?

~~~ 0;-Dan

---

### Post by peterfernandes238 on 2011-01-04
How do I configure a notifier to remain on-screen until "forever" or until the end-user selects OK or similar as acknowledgement?
------------
Peter Fernandes

---

### Post by Krytarik on 2011-01-04
> **SaintDanBert said:**
> THANKS!  That is a nifty trick.  I'll be sure to use it.

I have need to alter one or more built-in notifiers and cannot find where
they are stored and configured. 

I've done a **find ... -exec grep** search without success.
Any ideas?

~~~ 0;-Dan
Unfortunately I also don't had luck in modifying the built-in notifications, especially regarding the "urgency" option.

@peterfernandes238: Do you mean built-in notifications or custom ones, the way I described above?

---

### Post by SaintDanBert on 2011-01-04
> **Krytarik said:**
> ...
@peterfernandes238: Do you mean built-in notifications or custom ones, the way I described above?

I want the knowledge to do [highlight]both[/highlight].
[list]
[*] I have desire to alter built-in notifiers in various ways.
(This is somewhere in /etc/acpi or /etc/pm or similar ... or out in
/usr/lib somewhere. I'm still looking.)
[*] I have my own toys that I want to use notifiers with.
(I can now do this with my scripts and **notify-send**. Direct use of the notify API will wait.)
[/list]

---

