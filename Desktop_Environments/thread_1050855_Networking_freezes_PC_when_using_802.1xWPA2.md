---
title: "Networking freezes PC when using 802.1x/WPA2"
date: 2009-01-26
forum: Desktop Environments
---

### Post by leiurus on 2009-01-26
I'm using ubuntu 804LTS workstation on a eeepc 900 and it works pretty well. I have noticed before some various instabilities in especially the networking section of the OS and I know some friends also using the same OS has too.

Now I have to switch to RADIUS authentication when using a specific wireless network and when trying to set that up I got repeated system freezes.

Nothing works, no mouse, not restarting X no nothing. I had to pull the power every single time. I tried to do things a bit differently and ended up with some 4 freezes in total before I did some googling.

I then found this: <https://bugs.launchpad.net/ubuntu/+source/linux/+bug/296578>

My problem seem pretty much identical to what some people have noticed there.

The problems starts when I try access an AP that has WPA2/enterprise as authentication mode and after a few moments the mouse pointer stops moving, that's about it.

I don't think it's a Gnome problem either, since I have tested the Fedora 10 Live CD with Gnome and that one had no problems swithing between authentication modes for wireless.

Basically this is turning in to a show stopper for me, I have to be able to use RADIUS, or any other networking settings I may encounter, after all it's not so funny with an off-line system..

So: does anybody know of a time-line for these bugs to be fixed?

TIA

---

