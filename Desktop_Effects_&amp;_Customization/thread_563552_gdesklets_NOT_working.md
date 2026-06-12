---
title: "gdesklets NOT working"
date: 2007-09-30
forum: Desktop Effects &amp; Customization
---

### Post by Chymera on 2007-09-30
ok, so i want to get some desklets on my desktop.... but this damn proggy just doesnt want to start... i click it, it opens a blank window and then becomes unresopnsive.

When trying to run it from a terminal i get the following message:

> Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
 
Im pretty sure i would not be able to make much out of the log files content.... but then again, it doesnt even say where to find it in teh first place.

EDIT: ok so i found a log under home/.gdesklets/logs

here's what it says:

> Log messages of /home/chymera/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[09/30/07-12:05:10]===
Could not import tiling module!

---

### Post by Chymera on 2007-10-10
bump...

---

### Post by hvc123 on 2007-10-12
try runing 
#  gdseklets start

then 
 
# gdesklets

---

### Post by Chymera on 2007-10-12
lol ofcourse i already tried that.... the terminal just closes

---

### Post by LinuxIsInnovation on 2007-12-15
Bump.
Same problem with me..

---

### Post by Rui Pais on 2007-12-15
Hi,
see this [launchpad entry here]("https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/83922").
Apparently a fix it's committed for feisty (but not for gutsy?...)

Another bug report related:
[https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103)


Check for workaround on one of the entries, with [this package]("http://launchpadlibrarian.net/7542161/gdesklets_0.35.4-1ubuntu1_amd64.deb").

It works either by install it, or replace the original Ubuntu /usr/lib/gdesklets by the one that it's contained on package (open with file-roller or alike and extract package data.tar.gz, it's inside)

hth

---

