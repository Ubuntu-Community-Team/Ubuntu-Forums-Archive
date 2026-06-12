---
title: "Potential need for a new sticky?"
date: 2014-07-15
forum: Forum Feedback &amp; Help
---

### Post by kansasnoob on 2014-07-15
I sure am getting to be a pain in the neck, eh :lolflag:


I've been preparing my test suite for the upcoming hectic round of testing (14.04.1 next week, 14.10 Alpha 2 the week after, followed by 12.04.5 the very next week) and decided to review the Precise hardware enablement stack EOL policy. I recalled seeing this on [the mailing list]("https://lists.ubuntu.com/archives/ubuntu-announce/2014-July/000186.html"):

> In an effort to support a wider variety of hardware within the 12.04
Ubuntu LTS release, the 12.04.2 and newer point releases in Precise
shipped with hardware enablement stacks composed of updated kernels and
graphics stacks. The intention has always been for these hardware
enablement stacks to only remain supported until the introduction of the
kernel and graphics stack derived from 14.04. On August 7, 2014, the 5th
and final point release for 12.04 (ie. 12.04.5) will deliver the kernel
and graphics stack derived from 14.04. At that time, security updates
and bug fixes for older hardware enablement stacks will no longer be
provided. All users of older hardware enablement stacks will be
encouraged to update to the 12.04.5 hardware enablement stack or fully
upgrade to 14.04 proper. For any 12.04 HWE stack users interested in
making this migration prior to the August 7, 2014 deadline, we have
provided a mechanism to assist with this process. First, please ensure
your system is up to date with the latest package updates for Precise.
Then, run the command below and follow the instructions which are output:

hwe-support-status --verbose

For further information and details, please see:
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

Thanks,
Leann Ogasawara

Really important info at that link, but I anticipate a lot of confusion 8-[

Something I don't see mentioned there is the ability to use the archived 12.04.1 images since the original Precise kernel and X-stack will be supported throughout the Precise life cycle:

[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

Any thoughts :confused:

I was just thinking that the mods should be prepared in advance for a potential onslaught of confusion.

---

### Post by sudodus on 2014-07-15
Please excuse a stupid question. Does the quoted message mean that compatibility for old hardware will be lost, so that users (of old hardware) should avoid update/dist-upgrade and stay with a previous point release using only update/upgrade?

---

### Post by bapoumba on 2014-07-15
> All users of older hardware enablement stacks will be
encouraged to update to the 12.04.5 hardware enablement stack or fully
upgrade to 14.04 proper. 
This is what I read here.

---

### Post by sudodus on 2014-07-15
> **bapoumba said:**
> This is what I read here.

Yes, I know, and that is what I do with our own computers, but I'm waiting for kansasnoob's reply. He has a lot of experience of old hardware and how to keep Ubuntu working with it.

---

### Post by bapoumba on 2014-07-15
I'll follow the conversation :)
You know, when I saw the mail on the -devel list, I thought it was going to be important and moved to other things as I did not see all the implications. Learning times.

---

### Post by deadflowr on 2014-07-15
As per a sticky, well it is an Announcements right now.

> Please excuse a stupid question. Does the quoted message mean that  compatibility for old hardware will be lost, so that users (of old  hardware) should avoid update/dist-upgrade and stay with a previous  point release using only update/upgrade? 				

You'll be totally fine, if running pre 12.04.2, from an installation means.
(Meaning if you installed from either 12.04, 12.04.1 iso)

I think in terms of compatibility though, it will probably be of the same kind of thing that happened with 10.04.
In 10.04 some packages still got updates but others didn't, eventually something was bound to break.
This time the direction would be different, where as the kernel wouldn't be updated, but various packages would, so the end result might be the same.
Yet different.
If that makes sense.

---

### Post by sudodus on 2014-07-15
> **deadflowr said:**
> As per a sticky, well it is an Announcements right now.

> Please excuse a stupid question. Does the quoted message mean   that  compatibility for old hardware will be lost, so that users (of old    hardware) should avoid update/dist-upgrade and stay with a previous    point release using only update/upgrade?                 

You'll be totally fine, if running pre 12.04.2, from an installation means.
(Meaning if you installed from either 12.04, 12.04.1 iso)

I think in terms of compatibility though, it will probably be of the same kind of thing that happened with 10.04.
In 10.04 some packages still got updates but others didn't, eventually something was bound to break.
This time the direction would be different, where as the kernel wouldn't be updated, but various packages would, so the end result might be the same.
Yet different.
If that makes sense.

I see your point, and I agree that this is a problem if I don't dist-upgrade. But if drivers for old hardware are dropped, there is another problem, so there might be a "damn if you do, and damn if you don't" situation.

---

### Post by sudodus on 2014-07-15
Hi *kansasnoob*,

I hope you can help me with this question:

It doesn't *say*, but does the quoted message *mean* that compatibility for old hardware will be  lost, so that users (of old hardware) should avoid update/dist-upgrade  and stay with a previous point release using only update/upgrade?

What  about the drivers, that work with some very old hardware, will they be  replaced with drivers, that do not work with that hardware? What is  your experience?

In other words, in what way (if at all) are the  new point releases maintaining compatibility compared to the new  versions, in this case 12.04.5 versus 14.04.1 (and versus 12.04,  12.04.1, 12.04.2 ...?

What is your advice?

Best regards
sudodus

---

### Post by Elfy on 2014-07-15
If we start having stickies each and everytime something happens then we'll end up in a position where there is no front page for support threads.

I see no reason why this is any different than any other update/upgrade. 

If there ends up being a thread which covers the issue people can link to it whether it is on page 1, page 100 or page 1000 - in addition you can do that from anywhere.

---

### Post by kansasnoob on 2014-07-15
> **sudodus said:**
> Hi *kansasnoob*,

I hope you can help me with this question:

It doesn't *say*, but does the quoted message *mean* that compatibility for old hardware will be  lost, so that users (of old hardware) should avoid update/dist-upgrade  and stay with a previous point release using only update/upgrade?

What  about the drivers, that work with some very old hardware, will they be  replaced with drivers, that do not work with that hardware? What is  your experience?

In other words, in what way (if at all) are the  new point releases maintaining compatibility compared to the new  versions, in this case 12.04.5 versus 14.04.1 (and versus 12.04,  12.04.1, 12.04.2 ...?

What is your advice?

Best regards
sudodus

I've personally gone out of my way to keep all of my Precise production machines on the original Precise kernel and X-stack, performing any fresh installs or reinstalls with the archived 12.04.1 images. Basically everything I know ATM is in these two links:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

---

### Post by kansasnoob on 2014-07-15
> **Elfy said:**
> If we start having stickies each and everytime something happens then we'll end up in a position where there is no front page for support threads.

I see no reason why this is any different than any other update/upgrade. 

If there ends up being a thread which covers the issue people can link to it whether it is on page 1, page 100 or page 1000 - in addition you can do that from anywhere.

I sort of thought the same thing. In fact, after this crazy round of testing, I may start a thread in Chat to the effect of "Which Ubuntu should I install". If and when it becomes complete enough then we could decide move it or just link to it or whatever :)

But my better angels told me it was worth mentioning here.

---

### Post by Elfy on 2014-07-15
>  But my better angels told me it was worth mentioning here. Continue to listen to them :)

---

### Post by bapoumba on 2014-07-16
[http://ubuntuforums.org/newreply.php?p=13074574](http://ubuntuforums.org/newreply.php?p=13074574)

---

### Post by kansasnoob on 2014-07-16
> **bapoumba said:**
> [http://ubuntuforums.org/newreply.php?p=13074574](http://ubuntuforums.org/newreply.php?p=13074574)

That opens the reply window so:

[http://ubuntuforums.org/showthread.php?t=2234653](http://ubuntuforums.org/showthread.php?t=2234653)

But **yikes!** I'd hoped for a little more time before these began to appear :(

Since Trusty testing is first in this three week test cycle I'm mostly focused on setting up my Trusty test suite, which is going to be comprehensive because I was asked to test standard upgrades from each Precise;

12.04      w/Precise HWE  -> Trusty
12.04.2   w/Quantal HWE -> Trusty
12.04.3   w/Raring HWE   -> Trusty
12.04.4   w/Saucy HWE    -> Trusty

I did try an installation of Edubuntu Precise 20140714 daily last night and it just didn't work, but I've been in contact with Edubuntu dev:

[http://ubuntu.5.x6.nabble.com/Intro-and-LTS-point-release-question-td5072548.html](http://ubuntu.5.x6.nabble.com/Intro-and-LTS-point-release-question-td5072548.html)

So, while typing this I was thinking ............................. :-k

I wonder if they have the proposed updates enabled?

I don't think they should be seeing that yet unless they have proposed enabled which is never a good idea unless you really know what you're doing (and you're prepared for the possibility of total borkage).

I'll know more in a day or two as I set up these test installs for Precise -> Trusty upgrade testing, in fact I'll move those installations to the top of the list.

---

### Post by deadflowr on 2014-07-16
> 12.04      w/Precise HWE  -> Trusty

What stack is that?

---

### Post by sudodus on 2014-07-16
> **kansasnoob said:**
> I've personally gone out of my way to keep all of my Precise production machines on the original Precise kernel and X-stack, performing any fresh installs or reinstalls with the archived 12.04.1 images. Basically everything I know ATM is in these two links:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

Thank you for making things clear. So "keep the old kernels" and revert back to them, if there are problems with new point releases.

---

### Post by kansasnoob on 2014-07-16
I just finished installing and updating 12.04.2 with the Quantal HWE stack, then enabled proposed and did some checking:

```
lance@lance-desktop:~$ sudo apt-get upgrade -s
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic-lts-quantal linux-image-generic-lts-quantal
The following packages will be upgraded:
  appmenu-gtk appmenu-gtk3 apt apt-transport-https apt-utils indicator-appmenu
  jockey-common jockey-gtk libapt-inst1.4 libapt-pkg4.12 libjpeg-turbo8
  linux-generic-lts-quantal linux-libc-dev python-ubuntuone-storageprotocol
14 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Inst libapt-pkg4.12 [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf libapt-pkg4.12 (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst apt [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf apt (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst libapt-inst1.4 [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst appmenu-gtk [0.3.92-0ubuntu1.1] (0.3.92-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Inst appmenu-gtk3 [0.3.92-0ubuntu1.1] (0.3.92-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Inst libjpeg-turbo8 [1.1.90+svn733-0ubuntu4.3] (1.1.90+svn733-0ubuntu4.4 Ubuntu:12.04/precise-proposed [i386])
Inst apt-utils [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst apt-transport-https [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst indicator-appmenu [0.3.97-0ubuntu1] (0.3.97-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Inst jockey-gtk [0.9.7-0ubuntu7.14] (0.9.7-0ubuntu7.15 Ubuntu:12.04/precise-proposed [all]) []
Inst jockey-common [0.9.7-0ubuntu7.14] (0.9.7-0ubuntu7.15 Ubuntu:12.04/precise-proposed [all])
Inst linux-generic-lts-quantal [3.5.0.52.57] (3.5.0.54.59 Ubuntu:12.04/precise-proposed [i386])
Inst linux-libc-dev [3.2.0-65.99] (3.2.0-67.100 Ubuntu:12.04/precise-proposed [i386])
Inst python-ubuntuone-storageprotocol [3.0.2-0ubuntu1] (3.0.2-0ubuntu1.1 Ubuntu:12.04/precise-proposed [all])
Conf libapt-inst1.4 (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf appmenu-gtk (0.3.92-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Conf appmenu-gtk3 (0.3.92-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Conf libjpeg-turbo8 (1.1.90+svn733-0ubuntu4.4 Ubuntu:12.04/precise-proposed [i386])
Conf apt-utils (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf apt-transport-https (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf indicator-appmenu (0.3.97-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Conf jockey-common (0.9.7-0ubuntu7.15 Ubuntu:12.04/precise-proposed [all])
Conf jockey-gtk (0.9.7-0ubuntu7.15 Ubuntu:12.04/precise-proposed [all])
Conf linux-generic-lts-quantal (3.5.0.54.59 Ubuntu:12.04/precise-proposed [i386])
Conf linux-libc-dev (3.2.0-67.100 Ubuntu:12.04/precise-proposed [i386])
Conf python-ubuntuone-storageprotocol (3.0.2-0ubuntu1.1 Ubuntu:12.04/precise-proposed [all])

```

```
lance@lance-desktop:~$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.5.0-54 linux-headers-3.5.0-54-generic
  linux-image-3.5.0-54-generic
The following packages will be upgraded:
  appmenu-gtk appmenu-gtk3 apt apt-transport-https apt-utils indicator-appmenu
  jockey-common jockey-gtk libapt-inst1.4 libapt-pkg4.12 libjpeg-turbo8
  linux-generic-lts-quantal linux-headers-generic-lts-quantal
  linux-image-generic-lts-quantal linux-libc-dev
  python-ubuntuone-storageprotocol
16 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Inst libapt-pkg4.12 [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf libapt-pkg4.12 (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst apt [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf apt (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst libapt-inst1.4 [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst appmenu-gtk [0.3.92-0ubuntu1.1] (0.3.92-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Inst appmenu-gtk3 [0.3.92-0ubuntu1.1] (0.3.92-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Inst libjpeg-turbo8 [1.1.90+svn733-0ubuntu4.3] (1.1.90+svn733-0ubuntu4.4 Ubuntu:12.04/precise-proposed [i386])
Inst linux-image-3.5.0-54-generic (3.5.0-54.80~precise1 Ubuntu:12.04/precise-proposed [i386])
Inst apt-utils [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst apt-transport-https [0.8.16~exp12ubuntu10.17] (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Inst indicator-appmenu [0.3.97-0ubuntu1] (0.3.97-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Inst jockey-gtk [0.9.7-0ubuntu7.14] (0.9.7-0ubuntu7.15 Ubuntu:12.04/precise-proposed [all]) []
Inst jockey-common [0.9.7-0ubuntu7.14] (0.9.7-0ubuntu7.15 Ubuntu:12.04/precise-proposed [all])
Inst linux-image-generic-lts-quantal [3.5.0.52.57] (3.5.0.54.59 Ubuntu:12.04/precise-proposed [i386])
Inst linux-headers-3.5.0-54 (3.5.0-54.80~precise1 Ubuntu:12.04/precise-proposed [all])
Inst linux-headers-3.5.0-54-generic (3.5.0-54.80~precise1 Ubuntu:12.04/precise-proposed [i386])
Inst linux-headers-generic-lts-quantal [3.5.0.52.57] (3.5.0.54.59 Ubuntu:12.04/precise-proposed [i386])
Inst linux-generic-lts-quantal [3.5.0.52.57] (3.5.0.54.59 Ubuntu:12.04/precise-proposed [i386])
Inst linux-libc-dev [3.2.0-65.99] (3.2.0-67.100 Ubuntu:12.04/precise-proposed [i386])
Inst python-ubuntuone-storageprotocol [3.0.2-0ubuntu1] (3.0.2-0ubuntu1.1 Ubuntu:12.04/precise-proposed [all])
Conf libapt-inst1.4 (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf appmenu-gtk (0.3.92-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Conf appmenu-gtk3 (0.3.92-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Conf libjpeg-turbo8 (1.1.90+svn733-0ubuntu4.4 Ubuntu:12.04/precise-proposed [i386])
Conf linux-image-3.5.0-54-generic (3.5.0-54.80~precise1 Ubuntu:12.04/precise-proposed [i386])
Conf apt-utils (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf apt-transport-https (0.8.16~exp12ubuntu10.18 Ubuntu:12.04/precise-proposed [i386])
Conf indicator-appmenu (0.3.97-0ubuntu1.2 Ubuntu:12.04/precise-proposed [i386])
Conf jockey-common (0.9.7-0ubuntu7.15 Ubuntu:12.04/precise-proposed [all])
Conf jockey-gtk (0.9.7-0ubuntu7.15 Ubuntu:12.04/precise-proposed [all])
Conf linux-image-generic-lts-quantal (3.5.0.54.59 Ubuntu:12.04/precise-proposed [i386])
Conf linux-headers-3.5.0-54 (3.5.0-54.80~precise1 Ubuntu:12.04/precise-proposed [all])
Conf linux-headers-3.5.0-54-generic (3.5.0-54.80~precise1 Ubuntu:12.04/precise-proposed [i386])
Conf linux-headers-generic-lts-quantal (3.5.0.54.59 Ubuntu:12.04/precise-proposed [i386])
Conf linux-generic-lts-quantal (3.5.0.54.59 Ubuntu:12.04/precise-proposed [i386])
Conf linux-libc-dev (3.2.0-67.100 Ubuntu:12.04/precise-proposed [i386])
Conf python-ubuntuone-storageprotocol (3.0.2-0ubuntu1.1 Ubuntu:12.04/precise-proposed [all])

```

Guess I'll have to check some changelogs to figure out what's up :redface:

---

### Post by kansasnoob on 2014-07-16
> **deadflowr said:**
> What stack is that?

Original Precise stack with the 3.2* kernel which will be supported until April 2017.

---

### Post by kansasnoob on 2014-07-16
> **sudodus said:**
> Thank you for making things clear. So "keep the old kernels" and revert back to them, if there are problems with new point releases.

Because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643") I tried downgrading the Saucy kernel and X-stack to the original Precise kernel and X-stack but things blew up so I just reinstalled with the archived 12.04.1 image.

Since downgrading is not included in the official documentation I assume that it's just not supported.

---

### Post by kansasnoob on 2014-07-16
Another:

[http://ubuntuforums.org/showthread.php?t=2234693](http://ubuntuforums.org/showthread.php?t=2234693)

I guess a lot of people run with proposed updates enabled :(

I have a doctors appointment this AM, then must clean stock pens, so I'll get back to it when I can.

---

### Post by sudodus on 2014-07-16
> **kansasnoob said:**
> Because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1205643") I tried downgrading the Saucy kernel and X-stack to the original Precise kernel and X-stack but things blew up so I just reinstalled with the archived 12.04.1 image.

Since downgrading is not included in the official documentation I assume that it's just not supported.

So it is best to play safely and keep good backup copies of the system to ensure that old hardware like VIA graphics will still work.

---

### Post by kansasnoob on 2014-07-16
> **sudodus said:**
> So it is best to play safely and keep good backup copies of the system to ensure that old hardware like VIA graphics will still work.

The Trusty HWE stack has worked on everything I've tested it on, but it forces llvmpipe via Gallium on some graphics chips which actually seems to reduce performance so I'm mostly sticking with the original Precise kernel and X-stack on most older hardware for now.

---

### Post by kansasnoob on 2014-07-17
Errm, Canonical really dropped the ball on this one:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341324](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341324)

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341320](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341320)

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264)

It seems they failed to test the process before dropping it into standard releases :(

My greatest fear is that a lot of users will choose to reinstall which could result in a huge uptick in the number of dual-booters reporting loss of Windows/data due to this ignored bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

