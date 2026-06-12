---
title: "Which desktop manager to chose?"
date: 2011-04-09
forum: Desktop Environments
---

### Post by djetch on 2011-04-09
Hey everyone!

I'm going to be switching my media server to Ubuntu from Win7.  I have decided that I don't need all of what Ubuntu's server has to offer.  So, I'm going with the desktop version and now I'm wondering which desktop manager to go with.  I'm think I have a basic understanding:

GNOME - Main desktop manager
KDE - Main alternative
Xubuntu - fancier Xfce
Xfce - Light weight desktop manager
(and that's about where I stopped)

The media server will have a fair amount of stuff running on it but nothing insane.  No virtual servers, just applications and services.  (SSH, NXserver, XBMC, VPN, some newsgroup apps, etc.)

It really comes down to this: Will it really matter which one I chose?  Do I really need to slim down the desktop manager (Xfce)?

Oh, almost forgot to post the specs of the server:
Quad-core AMD64 (can't remember specific chip right now)
4GB RAM
1TB HD

Thanks,
Mat

---

### Post by Frogs Hair on 2011-04-09
You want to look at this.[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by djetch on 2011-04-09
I'm starting to think that it really shouldn't make a difference.  I think I might just start with GNOME (because I won't have to install anything additional) and it memory or something becomes an issue then I'll switch out to something like Xfce.

---

### Post by djetch on 2011-04-09
> **Frogs Hair said:**
> You want to look at this.[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

I'm guessing that either you're assuming that I was going with Ubuntu Server or that you think I should.

Either way I learned something, I didn't realize that Ubuntu Server did not have a GUI.  Makes perfect sense though now that I think about it.

While just about everything that I want to do with it would be fine without the GUI, I have a user requirement...my wife.  She's not a CLI type of user.  Hmmm... :confused:

---

### Post by Copper Bezel on 2011-04-09
Right, it's not like this is a "production server." 

XFCE is going to make a lot of things harder on you - a lot of configuration options that Gnome and KDE provide GUIs for have to be done by editing text files and such. Plus, those are some *really* nice specs for something that's just going to be a home server, and it'd be a *damn* shame not to even run a GUI on it.

If you're not familiar with any of the environments, Gnome is default for a reason - KDE is comparable in speed and functionality but considered slightly less stable.

---

### Post by ~Plue on 2011-04-09
> **Copper Bezel said:**
> Gnome is default for a reason - KDE is comparable in speed and functionality but considered slightly less stable.
 considered less stable? care to elaborate?

---

### Post by Copper Bezel on 2011-04-09
I mean that every time I see a debate on one against the other, of which there are perpetually well enough in Café, there's a *general perception*, most probably inaccurate, that KDE is less stable, in part I understand because of one much-hyped but initially unstable release that's since been much improved upon. I've had almost no experience with KDE and can't speak to whether or not this perception is accurate.

I suppose that saying "Gnome is the default for a reason" was exactly wrong, because the reality is exactly the opposite: assuming there is no reason, Gnome's default status is an advantage. There *is* more support for Gnome than KDE versions of Ubuntu, and that might be a consideration here. 

> I think I might just start with GNOME (because I won't have to install anything additional)

Well, it wouldn't actually make any difference to your initial install process, because if you did intend to use KDE, you'd probably want to install from a Kubuntu disk to start with.

---

### Post by Frogs Hair on 2011-04-09
> **djetch said:**
> I'm guessing that either you're assuming that I was going with Ubuntu Server or that you think I should.

Either way I learned something, I didn't realize that Ubuntu Server did not have a GUI.  Makes perfect sense though now that I think about it.

While just about everything that I want to do with it would be fine without the GUI, I have a user requirement...my wife.  She's not a CLI type of user.  Hmmm... :confused:

I misunderstood , yes , I did think you were installing the sever edition.

---

### Post by djetch on 2011-04-09
> **Copper Bezel said:**
> Right, it's not like this is a "production server." 

XFCE is going to make a lot of things harder on you - a lot of configuration options that Gnome and KDE provide GUIs for have to be done by editing text files and such. Plus, those are some *really* nice specs for something that's just going to be a home server, and it'd be a *damn* shame not to even run a GUI on it.

If you're not familiar with any of the environments, Gnome is default for a reason - KDE is comparable in speed and functionality but considered slightly less stable.

Thanks for the compliment on the box, built her myself.  I'm not genius at it but I know what I like and how to meet my requirements.

You know while I **LOVE** the command line and using Vi.  Yeah that's right I'm a Vi *****!  I have it installed on any and all boxes I work on, regardless of OS.  Having said all that it is nice to have a GUI to work in for config'ing.

Alright!  Decision is made: Ubuntu Desktop 10.10 running GNOME.

Thanks all! :D

---

### Post by KegHead on 2011-04-09
Hi!

I'm using 11.04b w/classic.

It's the absolute best. (for me)

Backup distro...Xubuntu.

KegHead

---

### Post by djetch on 2011-04-09
> **Frogs Hair said:**
> I misunderstood , yes , I did think you were installing the sever edition.

To be honest I hadn't really decided when I wrote that, I was thinking that I would just decide on the desktop environment first.  Clearly not realizing that Server has no DE.

Once again thank you for helping to realize that!

---

### Post by djetch on 2011-04-09
> **KegHead said:**
> Hi!

I'm using 11.04b w/classic.

It's the absolute best. (for me)

Backup distro...Xubuntu.

KegHead

So you went for the 11.04b huh?  I was reading about it and was a little unsure about running it as a "server" (note: not talking about the actual Server edition).  I am worried about the hardware support and what not.

What are you're thoughts now that you're using it?

---

### Post by KegHead on 2011-04-09
Hi!

I can't answer you about the server, but 11.04/classic is running perfectly for me on two atom basede machines.

It's fast and simple to use.

Kernel: 2.6.39

KegHead

---

### Post by irv on 2011-04-09
I have one web server running and it has served me well for almost 4 years now. I can tell you what I am running because I do run a DE on it. I do so I can xvnc into it from home and make changes from my laptop in a GUI.
I had a hard drive crash a few months ago and I installed 10.04 with gnome 2.32.0. When I am on the road I can FTP into it and still do things.
I has served me well and I like the setup. If your server box is fast and you have much memory there should be no problem what you run on it. No need to you a cut down DE if you have the power.
Just my opinion.

---

### Post by KegHead on 2011-04-09
Hi!

Thanks for the info on servers.

KegHead

---

### Post by djetch on 2011-04-09
Thanks to everyone for all of the info.  I feel that I'm on the right path now it's all down to finalizing the plans, making sure I'm not missing any details and then commiting the time to the change.  Fun, fun, fun!

---

