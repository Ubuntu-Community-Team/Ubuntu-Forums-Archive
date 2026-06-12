---
title: "organizing my system"
date: 2012-11-15
forum: Desktop Environments
---

### Post by rmcellig on 2012-11-15
Here is a screenshot of my Lubuntu 12.04 desktop. You will notice that I added a panel to the bottom with apps that I use every day. I find that this looks kind of junky and would like a better way to present the icons. I also need to add folders that I frequently access as well.

What would you recommend as a low resource solution? I know about Docky and Cairo-Dock but it seems that they need composting to work properly and require valuable resources. I am trying to keep this as simple as possible because the machine I am running this on isn't the fastest, if you know what I mean.

It's a Dell 3000 desktop. Intel Celeron 2.66GHZ. 2GB RAM.

Aside from using Puppy Linux, I am looking for an alternate OS that can approach the speed of Puppy Linux. So far Lubuntu seems to be the closest yet. Ny other ideas for a snappy distro that would fit nicely with my computer, please let me know.

Thanks!!

---

### Post by Mr_JMM on 2012-11-15
I would be tempted to add an expanded separator at the ends to position the icons in the center, auto hide the bar and set it so it's not 100% wide. That way you'll get something that more closely resembles a Cairo dock.

---

### Post by LewisTM on 2012-11-15
Did you try Xubuntu, since you have experience with it? 2 GB RAM should be enough to run it. Xfce can be blazing fast with enough RAM (> 1 GB). You can also try out package zram-config, a RAM compression scheme for those heavy tasks.

Cairo-Dock can be made to run without compositing by enabling 'Fake Transparency'. Don't know if it makes the system any slower but it looks fine.

Alternate fast OS: Bodhi Linux, Crunchbang.

Cheers!

---

### Post by vasa1 on 2012-11-15
You could try setting up a panel with Alignment: Left (like Unity) or Right if you wish. Add whatever apps you want there.
Then, in the Advanced tab, you could choose "Automatic hiding": minimize panel when not in use.

Re. folders, you could have logical links to folders on your desktop.

---

### Post by rmcellig on 2012-11-15
> **Mr_JMM said:**
> I would be tempted to add an expanded separator at the ends to position the icons in the center, auto hide the bar and set it so it's not 100% wide. That way you'll get something that more closely resembles a Cairo dock.


I thought about doing that but I don't think those options are available in LXPanel, unless I am missing something?

---

### Post by rmcellig on 2012-11-15
> **LewisTM said:**
> Did you try Xubuntu, since you have experience with it? 2 GB RAM should be enough to run it. Xfce can be blazing fast with enough RAM (> 1 GB). You can also try out package zram-config, a RAM compression scheme for those heavy tasks.

Cairo-Dock can be made to run without compositing by enabling 'Fake Transparency'. Don't know if it makes the system any slower but it looks fine.

Alternate fast OS: Bodhi Linux, Crunchbang.

Cheers!

I did try Xubuntu and found it sluggish on my machine. I never tried zram-config. I will check the repos and see if I can use it in Lubuntu. When I use Audacity for my audio editing, things really slow down.

Thanks for the Cairo-Dock tip. I will check it out.

I tried Bodhi Linux and found it interesting. I just didn't seem to wrap my head around all the config options in E17. As far as Crunchbang is concerned, I tried it a while back. Maybe can can try the Live CD and see how I like it.

---

### Post by vasa1 on 2012-11-15
> **rmcellig said:**
> I thought about doing that but I don't think those options are available in LXPanel, unless I am missing something?
Not sure about the expandable separator (which Xfce does have) but the rest is available from a careful look at the lxpanel options.

---

### Post by Mr_JMM on 2012-11-15
> **rmcellig said:**
> I thought about doing that but I don't think those options are available in LXPanel, unless I am missing something?

Try this:
Add a separator. If no options appear at this time (such as type) then once added, right click on it (if it's invisible this will take some careful clicking, it defaults to being placed far right) and select "expanded".

---

### Post by rmcellig on 2012-11-15
OK. Thanks.

---

### Post by ankspo71 on 2012-11-16
You would want to add 2 "Spacer" applets in lxpanel because those are the applets that can be expanded.

---

### Post by rmcellig on 2012-11-16
Thanks for the tip!!

---

