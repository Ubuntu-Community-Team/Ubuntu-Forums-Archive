---
title: "Variety Wallpaper Changer - still maintained?"
date: 2021-08-07
forum: Desktop Environments
---

### Post by heatopher2 on 2021-08-07
What is in the title is all I really wanted to ask, really!

I wrote [this post]("https://github.com/varietywalls/variety/issues/440") on GitHub, which to be honest is a place that I still don't really understand, and so maybe it's not the kind of thing that anyone on there would ever respond to :confused: Hopefully someone on here will be kind enough to help out, and if Variety is on the way out (which would be a horrible shame, as I really like it), could anyone let me know of any equally cool alternatives?

---

### Post by guiverc on 2021-08-07
Yes there is still evidence of maintenance (5 commits week of 25-July)

[https://github.com/varietywalls/variety/graphs/commit-activity](https://github.com/varietywalls/variety/graphs/commit-activity)

It's just not as active as it was

[https://github.com/varietywalls/variety/graphs/contributors](https://github.com/varietywalls/variety/graphs/contributors)

Sorry I have no experience with it. If you're using KDE have you tried KDE's wallpaper changer?

---

### Post by kc1di on 2021-08-08
Last I knew variety was still being maintained and updated.  But had not looked in awhile.  This page lists 10 of the most used wallpaper changers. [https://www.ubuntupit.com/best-linux-wallpaper-changer/]("https://www.ubuntupit.com/best-linux-wallpaper-changer/")

---

### Post by heatopher2 on 2021-08-08
> **guiverc said:**
> Yes there is still evidence of maintenance (5 commits week of 25-July)

[https://github.com/varietywalls/variety/graphs/commit-activity](https://github.com/varietywalls/variety/graphs/commit-activity)

It's just not as active as it was

Aaaah, not even close. What a shame!


> **guiverc said:**
> Sorry I have no experience with it. If you're using KDE have you tried KDE's wallpaper changer?

Eh, no, I'm just on vanilla Ubuntu as is. Anyway, it's not the changing part that isn't working on Variety/ It still does that as it's supposed to. It's just not downloading from most of the sources, as far as I can tell. I assume that there's some setting that needs sorting out, but no idea what :~) Also some of the quotes display incorrectly. Well, it's all in that post that I put on GitHub.

---

### Post by heatopher2 on 2021-08-08
> **kc1di said:**
> Last I knew variety was still being maintained and updated.  But had not looked in awhile.  This page lists 10 of the most used wallpaper changers. [https://www.ubuntupit.com/best-linux-wallpaper-changer/](https://www.ubuntupit.com/best-linux-wallpaper-changer/)

Yes, I think I might have looked at that page before. I'm sure that most of them do a perfectly good job, but Variety has so many nice features that I doubt any of the others can top.

---

### Post by ActionParsnip on 2021-08-08
[https://linuxconfig.org/set-wallpaper-on-ubuntu-20-04-using-command-line/](https://linuxconfig.org/set-wallpaper-on-ubuntu-20-04-using-command-line/)

It's just gettings so you can cron a script to pick a random file from a directory and set the wallpaper easily. I used to have 4 wallpapers which were morning, noon, evening and night which set at times of the day using something similar. Now I just have a solid black background (no wallpaper)

---

### Post by logix2 on 2021-08-12
> **heatopher2 said:**
> What is in the title is all I really wanted to ask, really!

I wrote [this post]("https://github.com/varietywalls/variety/issues/440") on GitHub, which to be honest is a place that I still don't really understand, and so maybe it's not the kind of thing that anyone on there would ever respond to :confused: Hopefully someone on here will be kind enough to help out, and if Variety is on the way out (which would be a horrible shame, as I really like it), could anyone let me know of any equally cool alternatives?

In the ticket, I see that you're using Ubuntu 18.04, which has a ancient Variety version in its repositories. Did you install the version from the repositories? If so, try to install a recent build, like from this PPA: [https://launchpad.net/~variety/+archive/ubuntu/daily](https://launchpad.net/~variety/+archive/ubuntu/daily)

---

### Post by heatopher2 on 2021-08-24
> **logix2 said:**
> In the ticket, I see that you're using Ubuntu 18.04, which has a ancient Variety version in its repositories. Did you install the version from the repositories? If so, try to install a recent build, like from this PPA: [https://launchpad.net/~variety/+archive/ubuntu/daily](https://launchpad.net/~variety/+archive/ubuntu/daily)

Hi, sorry for delayed response - I don't mind trying this, but do I stand to lose a lot from the fact that it's an "untrusted PPA"? I'm still building up my understanding of how things work.

---

### Post by Holger_Gehrke on 2021-08-24
A PPA is a **P**ersonal **P**ackage **A**rchive. Basically Canonical offers developers and packagers a place to put their work. Since they can't constantly check all PPAs and guarantee the packages to work as intended, they put up that warning about PPAs being untrusted sources of software and leave it up to the user to decide whether they want to use these packages or not. In this case it looks good: the package in the repositories show a James Lu as the original maintainer of the Debian package and gives the original homepage of the program as peterlevi.com. The PPA is owned by the variety-team, which is made up of Peter Levi and James Lu. So it looks like it's as official as it gets, unless we have a case of stolen identities ...

Holger

---

### Post by heatopher2 on 2021-08-24
OK, that sounds fine. I'll try it out some time soon :~)

T'anks ):P

---

### Post by ActionParsnip on 2021-08-25
Remember to mark as solved if the issue is sorted

---

### Post by heatopher2 on 2021-08-26
> **logix2 said:**
> In the ticket, I see that you're using Ubuntu 18.04, which has a ancient Variety version in its repositories. Did you install the version from the repositories? If so, try to install a recent build, like from this PPA: [https://launchpad.net/~variety/+archive/ubuntu/daily](https://launchpad.net/~variety/+archive/ubuntu/daily)

Well, I've just tried this, and it made no difference to the issues that I've been having. Still no response to my github comment, so I guess there's not a lot more that I can do now :(

It's OK - there are much worse things happening in the world.

---

### Post by heatopher2 on 2021-09-04
Well, you know what.... I just noticed yesterday that the two main problems that I was having with this application have gone away. Maaaaaybe that's because of adding the ppa, which finally updated properly just now, but honestly I didn't do anything specific to this in the last week or so. I had kind of just given up for the time being, as there were plenty of other things to worry about :~)

---

