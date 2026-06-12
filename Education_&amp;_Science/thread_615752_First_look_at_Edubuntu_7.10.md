---
title: "First look at Edubuntu 7.10"
date: 2007-11-17
forum: Education &amp; Science
---

### Post by rich.bradshaw on 2007-11-17
Just written my first blog post about Edubuntu - what do you think?

[http://richbradshaw.wordpress.com/2007/11/17/first-look-at-edubuntu-710/](http://richbradshaw.wordpress.com/2007/11/17/first-look-at-edubuntu-710/)

---

### Post by kesomir on 2007-11-18
The Killer point for edubuntu is easy LTSP setup and the educational package selection. The educational packages are on a second cd, which make initial selection of the packages for you.

```
In other words, why not just use Ubuntu?
```

1. LTSP setup
2. Package selection done for you

I guess you can ask the same question for using one Linux distro over another. it comes down to time saved / technical skill possessed.

My <harsh> opinion of your blog is that it's a superficial; focusing on colours of the default  theme and ignoring the main features of the distro.

I would heartily recommend* thoroughly using* edubuntu and writing another review.

---

### Post by por100pre1 on 2007-11-20
> **kesomir said:**
> The Killer point for edubuntu is easy LTSP setup and the educational package selection. The educational packages are on a second cd, which make initial selection of the packages for you.

```
In other words, why not just use Ubuntu?
```

1. LTSP setup
2. Package selection done for you

I guess you can ask the same question for using one Linux distro over another. it comes down to time saved / technical skill possessed.

My <harsh> opinion of your blog is that it's a superficial; focusing on colours of the default  theme and ignoring the main features of the distro.

I would heartily recommend* thoroughly using* edubuntu and writing another review.

+1 here. Sorry RB, but Edubuntu is not just Ubuntu with a different theme.

---

### Post by rich.bradshaw on 2007-11-21
I was surprised that there wasn't any educational software preinstalled - I expected that it would not need another CD.

I didn't test the ltsp side of things, which I realise is a key part of the distro.

I just felt that I would install Ubuntu, then use the addon CD, rather than using Edubuntu.

Is there a metapackage  to install the software on the add on cd without burning one?

---

### Post by LaserJock on 2007-11-21
> **rich.bradshaw said:**
> I was surprised that there wasn't any educational software preinstalled - I expected that it would not need another CD.

I didn't test the ltsp side of things, which I realise is a key part of the distro.

I just felt that I would install Ubuntu, then use the addon CD, rather than using Edubuntu.

Is there a metapackage  to install the software on the add on cd without burning one?

For Edubuntu 7.04 and 7.10 we had to split Edubuntu into two CDs. We ship everything that Ubuntu does plus LTSP server and infrastructure on the first CD. The Addon CD is where all the Educational apps are. Edubuntu 7.04 still had some educational apps, but there's just not enough room anymore.

Your point about just install Ubuntu and then using the addon CD is a good one. For Hardy we will be doing exactly that. We used to maintain enough differences from Ubuntu that we needed a separate installation CD, but now we want to focus more on educational applications and shift LTSP over to Ubuntu. So, Edubuntu will become more focused on being an educational addon for Ubuntu (and possibly in the future Kubuntu).

As far as metapackages, yes, I built some metapackages that will install the same packages that are on the addon cd. Do a search for edubuntu-addon in synaptic or whatever package manager you're using. To get a full set of educational applications edubuntu-addon-legacy is really good. It's the set we used to install by default in the pre-7.04 days.

Hope this helps and feel free to drop by #edubuntu on irc.freenode.net or edubuntu-users / edubuntu-devel mailing lists (at [http://lists.ubuntu.com](http://lists.ubuntu.com))

-LaserJock

---

### Post by rich.bradshaw on 2007-11-23
Thanks for your reply - that sounds like a good roadmap. I felt that the LTSP stuff shouldn't be exclusively Edubuntu, as the current Edubuntu release doesn't actually have much to do with education. (Well without the add-on cd anyway!)

I agree that LTSP should be part of Ubuntu as standard, really looking forward to Hardy!

Shame internet speeds still aren't fast enough to have a live-dvd  by default...

---

### Post by luvdemheels on 2007-12-05
Does edubuntu block unwanted web sites (ex adult sites) by default after install or is there something that needs to be enabled???

---

### Post by Dragonbite on 2007-12-06
> **luvdemheels said:**
> Does edubuntu block unwanted web sites (ex adult sites) by default after install or is there something that needs to be enabled???
As far as I know, there is no auto-blocking.
I think there are some blocking apps you can get (Dan's Guardian?) but I don't know enough about them (yet.. that's next on my list once I get LTSP working).

---

### Post by kesomir on 2007-12-06
I use the commercial version - Smoothwall's School Guardian

---

### Post by Dragonbite on 2007-12-07
> **kesomir said:**
> I use the commercial version - Smoothwall's School Guardian Is that an application you install on the server, or a stand-alone firewall you put on some other machine (w/2NICs)?

---

