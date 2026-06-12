---
title: "Best version of Evolution e-mail to use with Ubuntu 14.04 64-bit"
date: 2015-01-12
forum: Desktop Environments
---

### Post by cigtoxdoc on 2015-01-12
I am having problems with evolution 3.10.4 crashing when I open some html messages.  I have reported the problem to [email]bugzilla@gnome.org[/email]. and I have been told that I am using an outdated version of evolution.  However, synaptic says I am using the correct version.  What is the best (and correct?) version of evolution that I should be using?

Thank you,

John

---

### Post by kerry_s on 2015-01-12
try geary for mail client

---

### Post by buzzingrobot on 2015-01-12
It would have useful if someone had responded to your bug report with something definitive about whether your bug was fixed in subsequent releases.  No use installing a newer version if it won't fix things.

In any case, 3.10.4 is the current version offered by Canonical for 14.04. It's the version in the Ubuntu repos for 14.04, which is why you see it in Synaptic.  Someone else, perhaps, will chime in about whether newer versions can be run on 14.04.

The version currently in Vivid 15.04, the development release, is 3.12.9.  Meanwhile, I see that the Evolution project released 3.12.10 today.

Evolution is complex program suite. In my experience, trying to update it from unofficial sources, like a PPA, was often more trouble than it's worth, and was often unsuccessful. A bit of Googling will point you in that direction, if you choose to.

Thunderbird is the default mail client that ships with Ubuntu.

---

### Post by ian-weisser on 2015-01-12
> **cigtoxdoc said:**
> I have reported the problem to [EMAIL="bugzilla@gnome.org"]bugzilla@gnome.org[/EMAIL]. and I have been told that I am using an outdated version of evolution.

Looks like you have been busy: [http://askubuntu.com/questions/572587/e-mail-with-html-causing-evolution-3-10-4-to-crash-or-hang-ubuntu-14-04-64-bit](http://askubuntu.com/questions/572587/e-mail-with-html-causing-evolution-3-10-4-to-crash-or-hang-ubuntu-14-04-64-bit)

First, I would enable Apport on your system. Apport catches crashes and generates a big file of useful information about the crash...including exactly what crashed and the proximate cause. It's probably on your system, but disabled.
The .crash file will tell you if it's really an Evolution issue or not.

If it is an Evolution issue, then I would next open a new thread in Ubuntu +1, and ask the Vivid (15.04) testers to try to reproduce the problem. If a tester _is_ able to get their much newer version of Evolution to crash, Apport should automatically generate a .crash file. Attach that .crash file to the bug report.

---

### Post by cigtoxdoc on 2015-01-13
Thank yoiu to all for your replies.  Evolution 3.13.7 appears to have the same problem based on an almost complete database that I transferred to another PC, but it was not current enought to permit download of new messages.  Apport is installed on all my PC's.  On my laptop, (DELL Vostro 3500 with 8 GB RAM and nVidia graphics), Apport crashes in response to an evolution problem clainimg not enough free memory.  On my desktop PC's (home-built with MSI motherboards and Intel Haswell graphics, Apport will run at least with a known problem downloaded message.  The problem I am facing is that this problem is "intermittent" in that some html e-mail will always cause a problem, some will cause only a problem on initial loading of the message, some with a graphical signature will casue a problem when a reply is attempted.  I am beginning to think that the problem is triggered by something related to how the graphical message is prepared.  Html message from some organizations never cause a problem.

The Apport report from the crash with the webex message said, "Title: evolution crashed with SIGSEGV in _int_malloc()
UnreportableReason: This is not an official Ubuntu package. Please remove any
third party package and try again.
UpgradeStatus: No upgrade present (probably fresh install).

John

---

