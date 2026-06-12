---
title: "Drivers from Windows?"
date: 2009-03-30
forum: General Help
---

### Post by Kami Seraph on 2009-03-30
I just installed Ubuntu 8.04 on a partition of my hard drive to play around with it and start learning my way around.

Anyway, I have a Trendnet TEW-643PI networking card, and I'm not quite sure how to get a driver for it over on Ubuntu.

I thought, not too long ago, I read something along the lines of being able to use drivers that are already installed on another partition.

Is it possible to somehow get that done without having to move my modem to install these drivers, or can anyone sort of brief me on how I should get things like this done in the future?

---

### Post by jocko on 2009-03-30
> **Kami Seraph said:**
> I just installed Ubuntu 8.04 on a partition of my hard drive to play around with it and start learning my way around.

Anyway, I have a Trendnet TEW-643PI networking card, and I'm not quite sure how to get a driver for it over on Ubuntu.

I thought, not too long ago, I read something along the lines of being able to use drivers that are already installed on another partition.

Is it possible to somehow get that done without having to move my modem to install these drivers, or can anyone sort of brief me on how I should get things like this done in the future?

You can probably get it working by installing the windows driver with ndiswrapper (I've never needed to do this, so I can't help you very much on this. [This]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") looks like a place to start). But [this thread]("http://www.linuxquestions.org/questions/linux-newbie-8/trendnet-tew-643pi-wireless-n-card-not-working-695256/") looks like something you may need to look at *after* you manage to install the driver, in case you have problems connecting.
Good luck.

---

