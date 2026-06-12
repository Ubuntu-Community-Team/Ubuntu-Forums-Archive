---
title: "Need way to autoshutdown Beryl on Switch User"
date: 2007-05-01
forum: Desktop Effects &amp; Customization
---

### Post by narnie on 2007-05-01
I would like a way to killall beryl-manager/emerald when I switch user so I don't have to remember to kill it myself and then forget and another user logs and, tries to run Beryl, and boom: the crash begins.

I've found the scripts before for sleeping, hibernating, and resuming that I had to edit to kill and resume NetworkManager or I would have problems.

Can't find a similar script for switch users (and hopefully one that runs when the user resumes).

Are there such animals? Or other thoughts to accomplish this? Can't find a script that is called to perform the switch (or an executable).

TIA,
Narnie

---

### Post by kidders on 2007-05-03
Hi there,

Your post is interesting. How secure would your implementation need to be?

You could, for instance, create login scripts that checked the number of logged-in users before starting the graphical session. By explicitly allowing a certain user group to kill beryl processes (regardless of their owners), you could ensure that no more than one was running on your system at any one time.

The trouble with such a policy would be that users could easily circumvent it (to deliberately provoke problems) or arbitrarily invoke the "kill" script from a remote location (to upset a local user). I'm having trouble thinking of another way to go about it though, that would kill duplicate beryl processes quickly enough. Do your problems start right away, or would a few seconds' lag time between the initiation of a second beryl & the termination of the first one be acceptable?

I can't say I've ever needed to make such tweaks (for networking *or* beryl), but it's an interesting problem.

**Edit:** Something obvious just occurred to me! How about replacing /usr/bin/beryl with a shell script that detected & terminated running instances and *then* launched the real binary (that you could rename /usr/bin/beryl-real)? You would still need to make some sort of tweak (perhaps to /etc/sudoers) that would allow unprivileged users to invoke **sudo kill** or **sudo killall** passwordlessly under certain circumstances.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by narnie on 2007-05-05
that last part is a good idea, but I'm not sure how to grant those killall privilages (or if I really want to). I don't have an /etc/sudoers or anything like /etc/sudoXXXX

I was hoping that some script was run on switchuser that I could edit to kill automatically like I was able to do in the sleep.sh and resume.sh scripts under /etc/acpi

narnie

---

### Post by kidders on 2007-05-05
Hey again,

> **narnie said:**
> that last part is a good idea, but I'm not sure how to grant those killall privilages (or if I really want to). I don't have an /etc/sudoers or anything like /etc/sudoXXXXThat's odd. Check out **man sudoers** ... just to see if you're *supposed* to have one.

What you would do is grant any user that could log in locally (eg members of "video") the right to execute a specific command, that you would craft in such a way as to be practically useless for any other purpose. Users would never have to actually *type* it ... although they could, if they knew what it was. You would use /etc/sudoers to do it (which you could presumably create, if **man sudoers** works).

In security terms, you will probably have to open an exploitable hole of *some* sort, in order to allow unprivileged users to terminate processes that don't belong to them. It's just a question of which hole is most palatable, I suppose.

> **narnie said:**
> I was hoping that some script was run on switchuser that I could edit to kill automatically like I was able to do in the sleep.sh and resume.sh scripts under /etc/acpiThere are quite a lot of these. Most of them are executed using unprivileged accounts though, since it is generally considered wildly unsafe to use the root account in conjunction with X. The problem is finding one that (a) Ubuntu won't ever try to replace during a system update, and (b) can't be modified by the user that's causing it to run.

The reason sleeping/resuming are so easy is because these actions are associated with ACPI calls. Unfortunately, there is no hardware involvement in switching user.

**Edit:** I've just re-read my post, and realised how completely unhelpful it is! (Sorry for that.) I just haven't thought of anything smarter to suggest :-( I'm happy to help with any solution you feel like using though ... even if it isn't mine! :P

---

