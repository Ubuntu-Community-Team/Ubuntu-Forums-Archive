---
title: "upstart or eInit? That is my question."
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by yookoala on 2007-10-17
I waited for a new booting process in Linux for a really long time.

Ubuntu is good, but it boot really slow. What "boot really slow" means the time I boot from BIOS to the time I see my desktop and bars loaded. I uses Ubuntu because I love the ideal side of the project, but I have problem convincing my friends to use it. Boot time is one of the bad experience that upset my friends.

When [the plan for upstart](http://upstart.ubuntu.com/) was announced more than a year ago, I was amazed. [The initial paper](http://upstart.ubuntu.com/misc/upstart.pdf) mentioned launchd/Mac OS, and I know Mac OS boot really fast. It also mentioned an event structure that could replace crond. I thought it would rock the linux world by both performance and utility.

Year after that, I am still waiting.

upstart is not ready yet. The boot time is faster, but not as fast as I expected. There is, so far, no new function provided by upstart yet. There was a plan for upstart 0.5 on ubuntu 7.10 and it is still version 0.3.9 today.

Meanwhile, another init-replacement called [eInit](http://www.einit.org/) is out there. Users report that it starts linux in about 30s. Their [official site mentioned number of points that may make eInit faster than upstart](http://www.einit.org/node/11). Should I use it instead? And should ubuntu use it instead?

What do you think?

---

### Post by vemon on 2007-12-14
Ping!

I have the same question in mind now that I'm building a music player out of a 800Mhz Tablet PC. In the end I'm hoping to see a boot time at least under 10 seconds. The GUI would be Feevo running on bare X server (no window manager).

I've been able to get my 1,1Ghz laptop running Gutsy to start in 29secs (grub -> gdm login) by the means of "profile" (kernel parameter), removing unnecessary services and disabling file access timestamping (noatime hd parameter to /etc/fstab) but that's not nearly enough. The initial boot time before applied optimizations was 35-40secs.

So has anyone been able to install eInit to Ubuntu and was it any good? I'm probably going to try it and it would be nice to know how much hacking is involved when replacing Gutsy's upstart with eInit and does it speed up the boot.

- Jaakko

---

