---
title: "Suspending when logging in"
date: 2005-07-17
forum: Desktop Environments
---

### Post by rezonatix3 on 2005-07-17
Help!

The suspend function of my Kubuntu system has gotten totally out of control. Every time I log in through KDM, the system suspends to disk (hibernation), and the computer powers off. Then, when I turn it back on, the system resumes and I am able to use my computer.

Well, at least the successful resuming indicates that the suspend function itself is working properly, but why on earth is it activated when I log in? Turning my computer on twice (!) every time is, naturally, quite frustrating.

The problem arose after I touched the Lid Switch Close settings in the Power Control -> Laptop Battery section in KDE Control Center (yes, I am using a laptop - a [G556E](http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?MenuID=18&LanID=0&detailid=404), to be precise). The only information about my problem that I found on the Net, is a [bug report](http://groups.google.no/groups?selm=3LVE5-o0-31%40gated-at.bofh.it) (cited below), describing it in detail:

> klaptopdaemon makes the system completely unusable when configuring the "LID switch close" option. I enabled suspend-to-ram feature for my notebook by passing the argument acpi_sleep=s3_bios, now when I reboot my computer, on the next startup as soon as ksplash shows "Starting Services" the machine goes to suspend. When I resume, things start working fine. Also if I configure something in klaptopdaemon and click "Apply", klaptopdaemon takes the notebook into an infinite loop of suspend. As soon as I resume, it again suspends. This leaves the notebook unusable with only the option to do a hard reboot. Well, I'll try to avoid the Lid Switch Close section in the future, but how do I rid my computer of the erratic behavior?

---

### Post by rezonatix3 on 2005-07-18
Okay, solution found - in [another post](http://ubuntuforums.org/showthread.php?t=19442#post91773) at this forum, actually. It seems that deleting the [FONT=Courier New]~/.kde[/FONT] directory or its contents (i.e., [FONT=Courier New]/home/*username*/.kde[/FONT]) will leave you with a "clean" system, although this also resets all of KDE's settings.

With a little knowledge of the structure of [FONT=Courier New]~/.kde[/FONT], which I don't have, it should be possible to devise a more elegant solution - an exercise which I can only leave to the more experienced of the users encountering this bug.

---

