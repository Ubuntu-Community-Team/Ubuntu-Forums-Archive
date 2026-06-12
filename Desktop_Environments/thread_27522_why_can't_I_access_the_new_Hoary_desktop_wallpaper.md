---
title: "why can't I access the new Hoary desktop wallpaper?"
date: 2005-04-16
forum: Desktop Environments
---

### Post by darkfox on 2005-04-16
On my home desktop I've been using Hoary since I upgraded from Warty in December. I have kept it up to date regularly. On a spare desktop at work I've just installed Hoary from new, from a downloaded 5.04 image.

The new install has the new artwork (blue calendar for april etc).
My home PC cannot get this. I have reinstalled ubuntu-base and ubuntu-calendar, but I still only get the brown monthly calendars up to and including March.

What do I need to do to get fully up to date (I have done apt-get upgrade periodically)? Are there other aspects of my system that may be lagging behind? I think I've noticed some differences in the presentation of Synaptic also during package installation?

Thanks in advance - and great work Ubuntu devs as ever - on the strength of demo'ing Hoary at work I have been given the go-ahead to do a feasibility study on full migration from WinXP/2003 to Ubuntu :)

---

### Post by kassetra on 2005-04-16
[QUOTE=darkfox]The new install has the new artwork (blue calendar for april etc).
My home PC cannot get this. I have reinstalled ubuntu-base and ubuntu-calendar, but I still only get the brown monthly calendars up to and including March.
[/QUOTE]

Ok, on your home pc, is your repository list different from the new install pc?

---

### Post by darkfox on 2005-04-16
I don't *think* so, although I don't have access to my office desktop at the moment.
My home PC has the following entries in /etc/apt/sources.lst:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse

I believe these are appropriate for Hoary?

---

### Post by Klimax on 2005-04-16
Try 'sudo apt-get dist-upgrade', I had to do something like that after getting whined at by both synaptic and the update application.

---

### Post by darkfox on 2005-04-16
No good unfortunately - I have already tried that.

---

### Post by darkfox on 2005-04-28
In addition on the 'upgraded' desktop I appear to have a different look and feel to the fresh install. The old warty black-backgrounded console remains.

Any ideas what I may have done wrong, or indeed if there is a catalogue of resultant differences between a Hoary upgraded from warty and a Hoary installed from scratch? I had assumed that they would be 100% identical?

I should add that I upgraded by following the release notes instructions exactly.  Furthermore I have searched but have not found answers about such differences on the forums before posting (although I am not a regular forum user and maybe my searching could be improved)

---

