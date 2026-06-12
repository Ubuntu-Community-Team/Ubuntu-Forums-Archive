---
title: "XP Pro under VMware - network problem"
date: 2009-02-19
forum: General Help
---

### Post by staple on 2009-02-19
Hi,

I have convinced my girlfriend to try Ubuntu for her graphics machine which was running Vista and now I am in trouble :-(

It is a Dell XPS 1330 and Ubuntu 8.10 installed perfectly, wow. So far so good. She needs to run her Adobe programs so we installed VMware player all fine and then set up a XP Pro machine from another license she had.

XP works ok except I can not for the life of me get it to talk to the internet. I think the problem is that the Ethernet card does not have the right driver...I downloaded one I found for XP on the 1330 which installed fine but no luck yet. 

Questions for gurus..

1. Does the XP VM need an ethernet card driver to access the net through the VMPlayer?

2. Is there a device manager in Ubuntu which would tell me the exact Ethernet hardware information I need to find an XP driver for it?

Any and all advice most welcome,

Staple

---

### Post by Mercury_Alpha on 2009-02-19
I don't know of any easy answer, but I am able to run XP Pro via VirtualBox without any issues. It was able to connect to the 'Net right away, no tweaking needed. Might want to give that a shot.

If you do go that route, I recommend removing VirtualBox OSE and grabbing the Sun xVM version [over here]("http://www.virtualbox.org/wiki/Linux_Downloads") instead. It's a pretty straightforward install. Once you have everything up and running, add the Guest Additions so that you can smoothly move the mouse pointer between your host and the virtual machine.

I recommend giving XP at least 15GB of hard drive space and 512MB of RAM. But if you're doing a lot of heavy lifting with those Adobe apps, you're going to want to give XP as much RAM as you can afford.

---

