---
title: "Are Optimus Notebooks working properly on Ubuntu 14.04?"
date: 2014-04-30
forum: Gaming &amp; Leisure
---

### Post by renato3 on 2014-04-30
Hey guys, I'm a long term Debian/Ubuntu user, but recently I aquired an Optimus Notebook (which has 2 video cards: an Intel integrated video card + a Nvidia dedicated video card) and I find out that it simply won't work properly on Debian Jessie and Ubuntu 13.10, even with Bumblebee. I finally got it working on OpenSUSE 13.1 + Bumblebee, I can play any game I want directly from Steam - which is kind of a dream comming true lol. But I like .deb distros :/

What about the recently launched Ubuntu 14.04? Do Optimus Notebooks work properly now? Could someone who have an Optimus Notebook tell your experience using it to play games in this new Ubuntu release? Does Bumblebee or Nvidia-prime work properly?

---

### Post by pabloandnene on 2014-04-30
I am running 14.04 on an Acer Aspire V3-571G with Optimus (Nvidia GT 630M) and I haven't had any problems using nvidia-prime. I tried bumblebee, but I couldn't get it to work. Nvidia-prime was installed by default. I'm using prime-indicator (google it) to switch cards. The only bummer about nvidia-prime is the need to log out/log in for the settings change to take effect. It seems to work fine, but if I could use bumblebee, I would.

---

### Post by renato3 on 2014-04-30
> **pabloandnene said:**
> I am running 14.04 on an Acer Aspire V3-571G with Optimus (Nvidia GT 630M) and I haven't had any problems using nvidia-prime. I tried bumblebee, but I couldn't get it to work. Nvidia-prime was installed by default. I'm using prime-indicator (google it) to switch cards. The only bummer about nvidia-prime is the need to log out/log in for the settings change to take effect. It seems to work fine, but if I could use bumblebee, I would.

Thank you very much for posting, I hope other Optimus users tell their experience too. This is such a rich report. Why couldn't you use Bumblebee? And is the proprietary driver doing fine? I mean, can you play games normally with a good performance?

---

### Post by pabloandnene on 2014-04-30
I played Portal 2 with no problems in graphics or performance, but I didn't do any extensive testing. I couldn't run bumblebee due to having problems accessing the Nvidia GPU. It's like bumblebee was trying to use the Intel GPU for some reason. This person had the same problem:

[http://askubuntu.com/questions/450097/problem-with-optirun-bumblebee](http://askubuntu.com/questions/450097/problem-with-optirun-bumblebee)

---

### Post by renato3 on 2014-05-01
> **pabloandnene said:**
> I played Portal 2 with no problems in graphics or performance, but I didn't do any extensive testing. I couldn't run bumblebee due to having problems accessing the Nvidia GPU. It's like bumblebee was trying to use the Intel GPU for some reason. This person had the same problem:

[http://askubuntu.com/questions/450097/problem-with-optirun-bumblebee](http://askubuntu.com/questions/450097/problem-with-optirun-bumblebee)

Have you tryed using **virtualgl** instead of **primus**? [A guy on Debian's forum]("http://forums.debian.net/viewtopic.php?f=10&t=113994") told me he was able to put Bumblebee to work using virtualgl.

---

### Post by pabloandnene on 2014-05-01
Good to know. I'll check it out later.

---

### Post by renato3 on 2014-05-01
How do I tell bumblebee to use virtualgl instead of primusrun?

---

### Post by Jon Hanna on 2014-05-02
> **renato3 said:**
> How do I tell bumblebee to use virtualgl instead of primusrun?

Use optirun instead of primusrun, and have virtualgl set as your bridge in the config file for bumblebee, or use the -b virtualgl setting in your call to optirun to override whatever is in that config.

That said, I got primus to work fine in 14.04 with the latest nvidia drivers (and indeed, with nouveau prior to that), and it gave better performance than virtualgl, at least as far as judging based on comparing glxsphers with vblank_mode=0 set goes.

---

### Post by renato3 on 2014-05-02
> **Jon Hanna said:**
> Use optirun instead of primusrun, and have virtualgl set as your bridge in the config file for bumblebee, or use the -b virtualgl setting in your call to optirun to override whatever is in that config.

That said, I got primus to work fine in 14.04 with the latest nvidia drivers (and indeed, with nouveau prior to that), and it gave better performance than virtualgl, at least as far as judging based on comparing glxsphers with vblank_mode=0 set goes.

Me too. I installed Ubuntu 14.04, went to *Unity Settings --> Softwares & update --> Additional Drivers* and clicked on the proprietary driver option. Then everything was working already, no bumblebee nor primus nor virtualgl needed. To switch between Intel and Nvidia cards, I installed *prime-indicator* applet. **Ubuntu 14.04 is the best distro I tested so far for Optimus Notebook users!**

---

### Post by daaxwizeman on 2014-05-02
Hi,

I don't know about you guys that are using nvidia-prime, but I noted on my laptop that when I switch form nividia to Intel with the prime-indicator switch, I only have to log out/log in and the switch takes effect. The other way is not true though for me. if I click the prime-indicator and select the option to switch and log out/log in, I am not running under nvidia driver. I have to reboot the laptop for the switch (form Intel to nvidia) to take effect. 

Someone else have this behavior ? Is it a bug or a feature ?

---

### Post by Jon Hanna on 2014-05-02
Yeah, nvidia-prime needs you to log in and out. Maybe it'll be useful some day, but I'd definitely recommend trying to fix whatever problems one was having with bumblebee before resorting to it.

---

### Post by renato3 on 2014-05-02
> **daaxwizeman said:**
> Hi,

I don't know about you guys that are using nvidia-prime, but I noted on my laptop that when I switch form nividia to Intel with the prime-indicator switch, I only have to log out/log in and the switch takes effect. The other way is not true though for me. if I click the prime-indicator and select the option to switch and log out/log in, I am not running under nvidia driver. I have to reboot the laptop for the switch (form Intel to nvidia) to take effect. 

Someone else have this behavior ? Is it a bug or a feature ?

I had a similar, but worse, bug here. When I switch from nvidia to intel, some configuration is messed up and I can't go back to nvidia card, even when using nvidia-settings. Here is a screenshoot:

[IMG]http://s9.postimg.org/5m2ilzwdr/Screenshot_from_2014_05_02_00_19_28.png[/IMG]

In order to solve the problem, I have to purged and reinstalled nvidia related packages. Are you experiencing this issue too?

---

### Post by pabloandnene on 2014-05-02
You have to have an administrator account for prime-indicator quick switch to work properly. A regular user account will do nothing when using the quick switch. The only work around I've found is to go into nvidia-settings to change it there.

---

### Post by renato3 on 2014-05-03
> **pabloandnene said:**
> You have to have an administrator account for prime-indicator quick switch to work properly. A regular user account will do nothing when using the quick switch. The only work around I've found is to go into nvidia-settings to change it there.

Even in nvidia-settings, there is a bug that when you switch to intel card you can't switch back to nvidia card. More information, bug track and workaround here:

[http://ubuntuforums.org/showthread.php?t=2221573](http://ubuntuforums.org/showthread.php?t=2221573)

---

### Post by daaxwizeman on 2014-05-16
> **renato3 said:**
> I had a similar, but worse, bug here. When I switch from nvidia to intel, some configuration is messed up and I can't go back to nvidia card, even when using nvidia-settings. Here is a screenshoot:

[IMG]http://s9.postimg.org/5m2ilzwdr/Screenshot_from_2014_05_02_00_19_28.png[/IMG]

In order to solve the problem, I have to purged and reinstalled nvidia related packages. Are you experiencing this issue too?

Hi, nope, I don't have similar issues.

I presume there will be some improvements over time for this nvidia-prime tool.

---

