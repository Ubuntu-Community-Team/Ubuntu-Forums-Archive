---
title: "Several Problems with Ubuntu!"
date: 2009-04-23
forum: General Help
---

### Post by joeval on 2009-04-23
Hi guys

Been trying to get ubuntu set up and properly running on my netbook, and it just ain't working...  Running 8.04 remix

I can't seem to connect to my wireless internet (wired works fine).  It won't automatically detect any settings, so I've tried to do it manually.
Where do I find things like DNS, gateway, subnet mask, and the rest?
I figure if I can input all that, internet may work.

Also, I have no sound...  It was fine before I updated, so either one of the 148 ubuntu updates or one of the Gstreamer codecs is to blame.
I had to install the gstreamer codecs, as rhythmbox wouldn't add any of my music without (MP3's, all of them).

And lastly, I cannot upgrade to 8.10!  Having seen tutorials of how to do it by gui and terminal, none of them work.  I don't have an option for update manager under System/Admin, and running it via terminal just doesn't seem to do anything.

Wow, wall of text.  Sory bout that!  Hope someone can help, these little things are driving me crazy!

---

### Post by Sam Lars on 2009-04-24
Your gateway is the address of the router... probably 192.168.1.1
The subnet mask will be 255.255.255.0
I think it should be able to find DNS on its own... if not, try 208.67.222.222

As for sound, what do you get from
```
lspci | grep Audio
```
in a terminal?

And for the Update Manager... does it tell you anything in the terminal or just sit there?

---

