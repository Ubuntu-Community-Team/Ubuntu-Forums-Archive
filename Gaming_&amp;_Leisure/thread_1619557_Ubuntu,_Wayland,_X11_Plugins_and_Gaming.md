---
title: "Ubuntu, Wayland, X11 Plugins and Gaming"
date: 2010-11-11
forum: Gaming &amp; Leisure
---

### Post by sakuramboo on 2010-11-11
I'm sure everyone has heard by now that Ubuntu plans on ditching X11 for Wayland by next year. Nvidia has already stressed that they do not plan on supporting Wayland (at least, in time for its inclusion into Ubuntu). Mention of an X11 plugin to enable Compiz effects in Unity was mentioned, but I think that all of this might have a slightly negative effect in regards to gaming in Ubuntu.

There have already been a lot of complaints with how Ubuntu removed oss support from the kernel, basically, breaking most third party games. And with the huge number of complaints of sound issues when using padsp, this already doesn't look good. And now, to have a plugin in Wayland that will supposedly enable Compiz effects, are we to believe that we will get proper 3D support by using a plugin?

Of course, I am using the term "plugin" the way it was mentioned in the initial post (found [here]("http://ostatic.com/blog/compiz-to-be-rewritten-for-ubuntu-wayland")). But, I don't think that it is going to be as easy as just writing a plugin. There would have to be some sort of wrapper that can translate the X11 system calls to Wayland. So, we would be creating yet another layer, creating more system lag. And what about those who use WINE? What is going to happen there?

Does anyone have any thoughts or maybe even some rather technical information on this topic?

---

### Post by juancarlospaco on 2010-11-12
nVidia are Stressed?

We got 14 Linux Sound sub-systems, so its a mess anyways.

And IPv6 will add more Lag too, but we need to move on...

---

### Post by Modplanman on 2010-11-12
This post is based on a whole lot of misinformation.

Nouveau FOSS drivers already provide 3D support for a range of nvidia cards, in fact I'm using it right now with compiz. It works with games, but not too well, but most of that work will be further optimisation that will no doubt take place during the 2 years (at least) it will take to transition to Wayland, without accounting for other changes that may make Nvidia itself change its plans like if more distributions use Wayland.

[http://www.phoronix.com/scan.php?page=article&item=nouveau_mesa79&num=2](http://www.phoronix.com/scan.php?page=article&item=nouveau_mesa79&num=2)

---

### Post by sakuramboo on 2010-11-13
I never mentioned Nouveau. I'm talking about Ubuntu adding yet another layer that will hurt 3D performance. Already they killed plenty of games that rely on OSS. I'm sorry, but padsp is not the answer and has really hurt plenty of people already by creating 2+ second delays in audio.

This is 2010 and audio is just horrible in Linux. It just seems to me that Canonical should be focussing their efforts into making stable the problem areas that exist in Linux. And now, instead of fixing the issues with pulseaudio and getting other API's to utilise them, they are now going to make graphics take a big hit in performance by creating an X11 plugin for Wayland.

And where is the misinformation?

---

### Post by tommcd on 2010-11-13
Fedora also is interested in transitioning to Wayland:
[http://www.phoronix.com/scan.php?page=news_item&px=ODc4MA](http://www.phoronix.com/scan.php?page=news_item&px=ODc4MA)
So while it is true that nvidia has no current plans to support Wayland: 
[http://www.phoronix.com/scan.php?page=news_item&px=ODc2Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODc2Mg) 
If most of the popular linux distros begin transitioning to Wayland, then nvidia will have to choose between supporting Wayland, or not supporting linux at all. I believe they will choose to support Wayland if that is where linux is going.

---

### Post by tommcd on 2010-11-13
> **sakuramboo said:**
> 
This is 2010 and audio is just horrible in Linux. It just seems to me that Canonical should be focussing their efforts into making stable the problem areas that exist in Linux. And now, instead of fixing the issues with pulseaudio ...
I just remove pulseaudio. Therefore, I have no problems with pulseaudio.
I have always found that sound is just as good in linux as it is in Windows, if not better, and more easlily configurable. 
If your sound card is properly supported in linux, then sound should be fine. If the manufacturer of your sound card card does not support linux, this is hardly Canonical's fault.

EDIT:
Also, Canonical is not responsible for "*making stable the problem areas that exist in Linux*". Canonical is not responsible for the linux kernel, pulseaudio, Xorg, Wayland, or anything else that is developed upstream.
Linux is decentralized. This is it's greatest strength. There is no one (thankfully!!!) multinational corporation that controls it.

---

### Post by sakuramboo on 2010-11-13
I know that Canonical is not responsible for anything upstream. But, it just seems like better development efforts could be made, instead of incorporating gwibber into the gnome panel and stuff like that, that the development man power would be better spend on fixing the problem areas and sending the patches upstream.

I never had a problem with sound. My sound card is fully supported. That is, until 10.10 and OSS being excluded from the kernel. Sure, I can recompile the kernel, but that isn't the point. The point is, I shouldn't have to. Canonical is trying to make Ubuntu "just work" and yet they keep on doing things that pushes it backwards.

Also, is Fedora including Wayland a decision from the Fedora community or from RedHat? I honestly don't see nVidia supporting Wayland until a major player in Linux steps up and demands it from them. Now, if it was RedHat's decision, then we might actually get support from nVidia sooner than expected.

---

### Post by cgroza on 2010-11-13
> **sakuramboo said:**
> 

  Canonical is trying to make Ubuntu "just work" and yet they keep on doing things that pushes it backwards.


Again, Canonical did not remove OSS from the kernel. The kernel developers did nad OSS is already outdated.

---

### Post by sakuramboo on 2010-11-13
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=tree;f=sound/oss;h=a5d428db6dc494f65df472be5d9c390a45b64867;hb=f6f94e2ab1b33f0082ac22d71f66385a60d8157f](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.36.y.git;a=tree;f=sound/oss;h=a5d428db6dc494f65df472be5d9c390a45b64867;hb=f6f94e2ab1b33f0082ac22d71f66385a60d8157f)

It's still in the kernel. The kernel does not come precompiled. That means that Canonical compiled the kernel without OSS support.

And outdated or not, there are plenty of games and software that still rely on it. Seems like a rather foolish move to remove something that a good amount of software still relies on.

---

### Post by thatguruguy on 2010-11-14
> **cgroza said:**
> Again, Canonical did not remove OSS from the kernel. The kernel developers did nad OSS is already outdated.

Yes, they did.  Look at comment number 1 on [this thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300").

---

### Post by tommcd on 2010-11-14
> **sakuramboo said:**
>  But, it just seems like better development efforts could be made ... the development man power would be better spend on fixing the problem areas and sending the patches upstream.
I can agree with you there. I still question the decision to bring that resource hungry bloated mess that is pulseaudio into Ubuntu at this time. A quick search around these forums will find a boatload of problems, complaints, and confusion because of pulseaudio. There are similar problems and complaints about pulseaudio on the Fedora forums as well, by the way.
 I hope that the switch to Wayland does not cause as much grief as the switch to pulseaudio has caused. 

This is one of the great things about conservative distros like Slackware. Absolutely nothing is included in Slackware that does not have a proven track record of stability and reliability.
> **sakuramboo said:**
> 
Also, is Fedora including Wayland a decision from the Fedora community or from RedHat?
This is a good question. I do not have an answer to this though. I have only minimal experience with using Fedora, so I am not sure exactly how things work over there. 
I do know that Fedora is essentially a testing laboratory for Red Hat. So I would think that if Fedora is considering adopting Wayland, then Wayland is probably something that eventually may make it's way into Red Hat. That is, after all the bugs have been thoroughly squashed out of it.
> **sakuramboo said:**
> 
 I honestly don't see nVidia supporting Wayland until a major player in Linux steps up and demands it from them. Now, if it was RedHat's decision, then we might actually get support from nVidia sooner than expected.
Sure. As I said in post #5 in this thread, if most of the big guns in the linux community start adopting Wayland, then nvidia will have to support Wayland, or choose to drop their support for linux. I believe they will support Wayland if that is where the linux community is going.

---

### Post by psoulocybe on 2010-11-14
OSS outdated?

Where in the world do you get your information?

OSSv4 is a hell of a sound system. Extremely low latency, great quality, works fine with Jack.... 

Only drawback of OSSv4 I've found is ignorance of this community when the topic comes up, and no true MIDI support.

---

### Post by flying sheep on 2010-11-14
wikipedia says, oss does neither support multiprocessor architecture nor simultaneous recording and playing. that makes it obsolete if it was up to me&#8230;

---

