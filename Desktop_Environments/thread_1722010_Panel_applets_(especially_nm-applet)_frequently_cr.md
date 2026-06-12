---
title: "Panel applets (especially nm-applet) frequently crashing"
date: 2011-04-05
forum: Desktop Environments
---

### Post by drs86 on 2011-04-05
Hi,

In the last week or two, nm-applet has started crashing a lot. It's been a little bit random so it's difficult to nail down when it happens, but it especially seems to crash when my network status changes (i.e. if I unplug the LAN cable and go to wireless) and/or when I return from system suspend. It's really annoying because if I want to use wireless then I have to open a terminal and run nm-applet from there, or else reload it on the panel. What's really baffling is that I've run this system (Lucid x86 on my laptop) for a long time now and it never used to do this, and I haven't made any big system changes recently that I can remember, except I did install Firefox 4 when it was released. I can't figure out what could be going wrong.

I did manage to catch it crashing once when I was running it in the terminal, and it printed a message to the terminal saying it caught signal 15 (that's SIGTERM, right?).

I also lost the gnome-power-manager applet from my panel a few days ago, although I haven't noticed the problem recurring.

Can anybody give me some advice on how to figure out where the problem is? Or has anyone seen this before? I'm wondering if Firefox 4 is somehow sending SIGTERM to the network manager, although that sounds pretty crazy.

Thanks,

David

---

### Post by ryokea on 2011-04-19
> **drs86 said:**
> Hi,

In the last week or two, nm-applet has started crashing a lot. It's been a little bit random so it's difficult to nail down when it happens, but it especially seems to crash when my network status changes (i.e. if I unplug the LAN cable and go to wireless) and/or when I return from system suspend. It's really annoying because if I want to use wireless then I have to open a terminal and run nm-applet from there, or else reload it on the panel. What's really baffling is that I've run this system (Lucid x86 on my laptop) for a long time now and it never used to do this, and I haven't made any big system changes recently that I can remember, except I did install Firefox 4 when it was released. I can't figure out what could be going wrong.

I did manage to catch it crashing once when I was running it in the terminal, and it printed a message to the terminal saying it caught signal 15 (that's SIGTERM, right?).

I also lost the gnome-power-manager applet from my panel a few days ago, although I haven't noticed the problem recurring.

Can anybody give me some advice on how to figure out where the problem is? Or has anyone seen this before? I'm wondering if Firefox 4 is somehow sending SIGTERM to the network manager, although that sounds pretty crazy.

Thanks,

David
I've actually been having this problem as well. Can't figure out any sort of warning signs before it exits either. Running nm-applet with this logger script I found to catch any relevant data and see if I can track down the culprit.

I suppose a temporary solution would be to wrap nm-applet in an infinite loop until the problem is solved so you don't have to worry about your network manager vanishing.

---

### Post by SnappyU on 2011-04-28
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/664763](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/664763)

---

