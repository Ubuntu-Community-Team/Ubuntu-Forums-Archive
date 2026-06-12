---
title: ".xsession Entries Failing to Start"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Tsuki on 2005-10-18
Not really GNOME desktop support I'm afraid - rather, I'm using GDM and launching into "Default Session" - which, I believe, should execute my ~/.xsession.

In the last couple of days (I don't recall changing anything related to this, so possibly it got broken by an update?) two of the programs mentioned in my .xsession - pypanel and xscreensaver - haven't been running.  When I run them later through a console, they run fine.

Any idea what's up?  Here's my .xsession:

```
eval `cat $HOME/.fehbg` &
pypanel &
gkrellm &
xscreensaver --no-splash &
amarok &
gaim &
azureus &
exec openbox
```

Like I said, everything's running fine except pypanel and xscreensaver.  I can't see anything about them in any logs (there's a lot of gconf stuff mentioned in the syslog but I wouldn't have thought that was related).

So... anyone?

Thanks in advance!

---

### Post by phen on 2005-11-06
hello all!

i have got the same problem. pypanel does not start automatically after boot. when i restart x and kdm with ctrl-alt-"<-", it does startup though! any help would be greatly appreciated!

cheers

---

### Post by drewbie on 2005-11-08
Tsuki, try 

xscreensaver -no-splash &

I don't think that --no-splash is a vaild option, so xscreensaver won't start

---

