---
title: "Gnome: Shutdown fails (GLib Error)"
date: 2008-04-12
forum: Desktop Environments
---

### Post by sirweber on 2008-04-12
hi all,

since quite a time, i've got the following message when shutting down or restarting my Thinkpad via the Gnome Shutdown button:

> gdm[5866]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed 

after having showed this error, the machine eventually shuts down after several seconds.

I already googled quite a lot, but was unable to find a solution for this case... 
How can I give you more information? Logs...? which ones?? 

- Thinkpad Z61m
- Ubuntu Gutsy 7.10
- All software is kept up-to-date

Thank you in advance!

Cheers
Stefan

---

### Post by sirweber on 2008-04-14
sorry for pushing this up, but I really can't imagine that nobody has any kind of tip how to solve this... .:S

:confused:

---

### Post by kellemes on 2008-04-14
Google shows 2 hits, they where both yours :-)

I can only point to your logs in /var/log
Maybe "messages" shows something?

---

### Post by sirweber on 2008-04-14
xD yes i know, how did I manage to get this error... *confused*

I can't find anything special in messages, i tried several other logs but wasnt able to find anything useful...

**/var/log/messages**
> Apr  9 08:22:59 localhost syslogd 1.4.1#21ubuntu3: restart.
Apr  9 08:40:44 localhost -- MARK --
Apr  9 09:00:44 localhost -- MARK --
Apr  9 09:20:44 localhost -- MARK --
Apr  9 09:37:18 localhost exiting on signal 15

can i switch on extended logging somehow? thank you so far...

cheers

---

### Post by kellemes on 2008-04-15
> **sirweber said:**
> xD yes i know, how did I manage to get this error... *confused*

I can't find anything special in messages, i tried several other logs but wasnt able to find anything useful...

**/var/log/messages**


can i switch on extended logging somehow? thank you so far...

cheers

Are you up to date? It could be some bug in GDM that's fixed already, just guessing here..
```
sudo apt-get update
sudo apt-get upgrade
```
EDIT: Sorry.. you said you're up to date in your first post ;-)

------------------

It seems to be a message coming from GDM (your login manager), I'd be interested if switching login manager will bypass this issue.
Instead you could use KDM, this login manager is part of the KDE desktop environment so installing it will pull in some KDE related packages, besides filling some hd-space it won't have any effect on your system.

From terminal..
- Update repositories.
```
sudo apt-get update
```
- Install KDM.
```
sudo apt-get install kdm
```
- Set KDM as login manager (select KDM from the dialog box)
```
sudo dpkg-reconfigure gdm
```

-------------

If things don't work out you can issue the same command to revert back to GDM.
```
sudo dpkg-reconfigure gdm
```

If you want to remove KDM from the system again you can do..
```
sudo apt-get remove kdm
```
To remove unwanted dependencies.. (always check the list before hitting <ENTER>)
```
sudo apt-get autoremove
```
Not sure if all KDE-related packages will be removed but I think they will.

---

### Post by sirweber on 2008-04-15
thanks a lot for these tips

i successfully installed KDM and activated it. unfortunately, the shutdown-button in GNOME is now gone.
but when i log off and select shutdown from the KDM menu, everything seems to work fine, no more error messages! :)

so it's not yet the solution to disable GDM... can i try to reinstall GDM without crashing my Ubuntu?

---

### Post by kellemes on 2008-04-15
> **sirweber said:**
> thanks a lot for these tips

i successfully installed KDM and activated it. unfortunately, the shutdown-button in GNOME is now gone.
but when i log off and select shutdown from the KDM menu, everything seems to work fine, no more error messages! :)

so it's not yet the solution to disable GDM... can i try to reinstall GDM without crashing my Ubuntu?

```
sudo dpkg-reconfigure gdm
```
Choose GDM from the dialog should bring back things to normal.. Probably including error-message. ;-)
At least you now know it's a GDM-thing.

---

### Post by sirweber on 2008-04-15
allright, but is there a possibility to remove GDM and reinstall?
can i do such a thing over apt-get?

ty!
cheers

---

### Post by kellemes on 2008-04-15
> **sirweber said:**
> allright, but is there a possibility to remove GDM and reinstall?
can i do such a thing over apt-get?

ty!
cheers

Sorry, I misread your post.

Well, you can do..
```
sudo apt-get install --reinstall gdm
```
or
```
sudo apt-get --purge remove gdm
sudo apt-get install gdm
```

Hope it helps..

---

### Post by sirweber on 2008-04-15
okay, after reinstalling GDM, the error is gone! :)
why didn't i try this earlier... :mad:

thanks to you for helping me bashing this problem away ;)

cheers

---

### Post by kellemes on 2008-04-15
> **sirweber said:**
> okay, after reinstalling GDM, the error is gone! :)
why didn't i try this earlier... :mad:

Well, why didn't **I** think of this earlier... :mad:
Glad it works..

---

