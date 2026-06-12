---
title: "How can I disable automatic booting into X windows?"
date: 2012-06-28
forum: Desktop Environments
---

### Post by youknowme on 2012-06-28
I want to set my system to boot to a console so then i can optionally start X by typing 'startx'. Please tell me how to go about this.
thnaks

---

### Post by BBQdave on 2012-06-28
> **youknowme said:**
> I want to set my system to boot to a console so then i can optionally start X by typing 'startx'. Please tell me how to go about this.
thnaks

Not sure I follow :confused:

You can start up in recovery mode and enter commands to start up your windowing system...

or you can boot into your windowing system and type commands in your favorite CLI :D

---

### Post by SpeedyGonsales on 2012-06-29
I fully understand your question as I worked that way in Ubuntu from Breezy Badger until recently (and in some other distributions before Ubuntu, for that matter :)).

Reason is simple - if you had problems with drivers for your graphics card (and that occured often, whichever card you used), it wouldn't take much to type startx after you login to your PC, and that would save you trouble with booting from rescue CD's and manually mounting disk etc if something went wrong in system upgrade or .... something.

Recently (read last 2 or 3 years) graphic card drivers for Linux got better, so I gave up on startx after Ubuntu started using Upstart and gdm/kdm and recently lightdm.

But, you can make it happen if you want!

First way is written above - during booting choose rescue mod which will drop you in runlevel 1 where you in console can type startx and get to X.
You would be in runlevel 1 (no services), but that can be easily solved if you wanted to.
Other solution would be to edit two files in /etc/init:

In /etc/init/gdm.conf

change lines

##ubuntu 11.04##
```

start on (filesystem
          and started dbus

```
with
```

start on (filesystem and runlevel[245]
          and started dbus

```

##ubuntu 12.04##
```

start on ((filesystem
           and runlevel [!06]

```
with
```

start on ((filesystem
           and runlevel [!036]

```

In /etc/init/rc-sysinit.conf

change line

> env DEFAULT_RUNLEVEL=2

with

env DEFAULT_RUNLEVEL=3


Only you have to have in mind that if you use metacity instead of compiz but if you have both of them installed startx will start compiz as it is default wm since 11.04.
In that case you could deinstall compiz or tweak your config files a bit more, but that is out of the scope of question asked in first post. :D

---

