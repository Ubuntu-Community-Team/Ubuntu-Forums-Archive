---
title: "When will the groupdav Akonadi resource be included"
date: 2011-05-24
forum: Desktop Environments
---

### Post by IngoRatsdorf on 2011-05-24
Hi.

There has been a groupdav resource available in KDE for quite some time. It moved up from the playground more than half a year ago and is now part of KDE.
According to the maintainer, the last remaining fix to Akonadi itself in order for it to run was made in 4.6.3.

I have been testing this resource for over half a year and it's great. Does not block any desktop activity, runs smoothly in the background as KIO job....

Works well with eGroupware and DaviCal.
Just cannot find updates to existing caldav entries at the moment because of the bug in Akonadi. itself.

When will this resource be included in Kubuntu? Will it be available in Kubuntus KDE 4.6.3?

---

### Post by IngoRatsdorf on 2011-06-08
Right, I am going to give an update on myself:

It would appear that [Kubuntu 11.10]("http://cdimage.ubuntu.com/kubuntu/daily/current/") has all the required libraries to allow the use of [akonadi_davgroupware_resource]("https://projects.kde.org/projects/kde/kdepim-runtime/repository/revisions/master/show/resources/dav").
I believe the requirement is to have the serialisers for KCalCore in place.

The test I have done works with that configuration.
Update to [Oneiric]("http://cdimage.ubuntu.com/kubuntu/daily/current/"), download [sources]("https://projects.kde.org/projects/kde/kdepim-runtime/repository/revisions/master/show/resources/dav") from projects.kde.org and compile and install.

You will have a fully working group-/cal-/carddav resource.

What I still do not understand though, is, why Kubuntu is still not shipping that resource by default.

Cheers,
Ingo

---

