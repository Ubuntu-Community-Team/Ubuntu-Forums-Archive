---
title: "Final year/course project for an undergraduate degree in CS, some advice needed"
date: 2011-10-04
forum: Education &amp; Science
---

### Post by xaviusxyz on 2011-10-04
Hi to all!

*[COLOR=Blue]Premise[/COLOR]*: I should start working at the final course project for my *_undergraduate degree course in Computer Science_*
[COLOR=SlateGray](I know... this is usually one of the most hated  kinds of topic, I'm sorry and I beg your pardon, but, please keep  reading... please)[/COLOR]

My field of interested is almost everything concerning *Linux/Unix* and *system administration* in general.
Firewall rules, system/server administration/configuration, hardening a system and so on.
In the future I'm looking forward to a job as a system administrator (with time, efforts, and job experience obvioiusly!)

Anyway, _I'm not very interested in coding and programming stuff (and I'm not so good at it, either)_.

So a project in the Linux/Unix/System Administration field will be useful for my future (I hope).
A project involving coding, programming will not.
Scripting and bash scripting is ok, though (the same for everything about CLI, editing configuration files.....).


*[COLOR=Blue]My ideas[/COLOR]*: hardening a Linux system; Snort; something about VPN; Linux Cluster; configuring some specific server/service
IMO they are useful topics (you can learn a lot working on these) but I feel they are too general and maybe a bit outdated


What I'm ***NOT*** looking for:
- I'm NOT looking for anyone else to do my "homeworks" (or job) for me

*[COLOR=Blue]What I'm looking for[/COLOR]*:
- some advice to "tune up", to narrow, and to update maybe, my ideas
- other ideas, suggestions (maybe related to more "up to date" topics)
- some help to avoid a silly/too easy or, on the other hand, impossible topic


[COLOR=SlateGray]I know that the quick response is always: talk  to you tutor/professor/whatsoever, the problem is that lots of  professors at my University currently work with temporary jobs for one  year only so they are not interested in this kind of things. The  tutoring system is almost non-existent.
(yeah... strange, odd, weird, almost unbelievable... I know, I know
but sadly true)[/COLOR]


Any serious help will be really really much appreciated. Thanks in advance!

---

### Post by Dangertux on 2011-10-04
Well -- you seem to have interest in security related topics.

Might I suggest, though something a little less broad. Server hardening is great, and if you want to write about it you could. However, a lot of times as I'm sure you're aware it's extremely service specific. IE: Writing about hardening a tomcat installation isn't going to help someone who is administering a mail server. So, depending on how large of a project you may need elaborating properly on all the points necessary may get very dull, and very long , very quickly.

My thought would be pick a relevant topic, and really demonstrate that you understand something about it, not just how to set it up. Let's be honest, you say you want to be a system administrator, but sysadmins who know how to install an IDS /IPS are a dime a dozen, and most don't even configure them properly.

Really analyze a topic in depth, be thorough, explain  it's relevance in terms of ACTUAL threats, not just theoretical threats. Make it relevant to current events even, build a hypothetical scenario, show it in action, be able to demonstrate why whatever system you choose to write about works, and how.

My thoughts on topics you could write about that I feel are relevant.

- Advanced IDS/IPS (not just how to install snort) make snort do something, or OSSEC or whatever your poison may be, if you can get your hands on a checkpoint type device even better.

- Virtualization security is always a hot one, you could demonstrate the effectiveness or ineffectiveness (depending on your stance) of virtual security appliances, how they can be implemented to compliance standards, and how they can be utilized to counter APTs.

- Discuss threat analysis, boring topic, but it's truly important. Yeah sure you can look at a log file and tell me yep I got owned. But can you disect the log file, tell me how, follow stack traces and tell me exactly what an attacker did? How can you implement tools such as HIDS and MAC to prevent/mitigate/control or otherwise monitor this?

- Cloud security, how are you going to protect your cloud one day? This will tie in a lot with virtualization sec, but is more specific to a shared, and open environment.

Those are just some ideas, run with one, or trash it and come up with your own. Just my thoughts.

---

