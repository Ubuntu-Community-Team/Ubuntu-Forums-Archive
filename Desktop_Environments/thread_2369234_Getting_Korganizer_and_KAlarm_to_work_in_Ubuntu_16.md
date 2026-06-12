---
title: "Getting Korganizer and KAlarm to work in Ubuntu 16.04 LTS"
date: 2017-08-20
forum: Desktop Environments
---

### Post by vineyridge on 2017-08-20
I need a good scheduler with alarms and reminders and snoozes.  Korganizer is supposed to be that, especially with the KAlarm module installed.  I got both from the plain vanilla Ubuntu app store, installed both, and discovered that I cannot set my time zone.  They are stuck on UTC.  There is a message from the author that they will remain stuck on UTC unless and until the module Ktimezoned is installed.  It is not in the app store, and I wonder if, since it is so primal, that it would in Ubuntu.  I found an old thread here that suggested a workaround--https://ubuntuforums.org/showthread.php?t=2330246&highlight=KDE+time+zones--but I don't quite understand what the fixes are, and no one responded.

In the Ubuntu KDEPIM bug forum, there was a post from April 2017 that this bug had been fixed.> [TABLE="class: bug-activity"]
[TR]
[TD="colspan: 2"]Changed in kdepim (Ubuntu):[/TD]
[/TR]
[TR]
[TD="align: right"]         **status**:[/TD]
[TD]         Confirmed &#8594; Fix Released[/TD]
[/TR]
[/TABLE]


I just installed the 16.04 last night for a retry, and I updated on the install and again today.
  There is nothing from search that indicates this computer has kdelib or kdepim installed.  The Ubuntu Help Guide doesn't make sense to me.  I'm in the process of installing Synaptic Manager, and it says that I have kdelib modules installed.  It also says that I do not have plain kdepim installed, but I do have kdepim-doc, kdepim-runtime, kdepimlibs-data, kdepimlibs-kio-plugins, and three different packages beginning in lib for kdepim,two of which end in the number 5.  All were sourced from 0ubuntu1, and all are version 4:15.12.3.

The Ubuntu Help Guide doesn't make sense to me and wouldn't address this issue anyhow.

As of today, the bug wasn't fixed for me.

So, how can I make these two KDE bits work properly in regular Ubuntu?

---

