---
title: "nVidia closed source driver vs nouveau drivers"
date: 2010-09-07
forum: Gaming &amp; Leisure
---

### Post by alexandrius on 2010-09-07
Guys, can you please explain advantages and disadvantages of these drivers?

---

### Post by J.K.Makowka on 2010-09-07
The open source driver, is well open-source and can be therefore better integrated into the system, at least theoretically. I haven't checked it's status so far. It's also legally and "ideologically" the better solution.
Since it has to be written with out official documentations (only ATI/AMD suppled that recently) it is much behind features compared to the closed source official one. Therefore it is not usable of 3D gaming so far AFAIK (much too slow etc).

The official one supports almost every GPU and is much faster... is has integration issues however, like uncomfortable multi-monitor support, and no high resolution during boot etc. For gaming it's the only option currently.

P.S.: I recently discovered that the new OPTIMUS laptop GPU technology isn't supported by the closed source driver under Linux either :(

---

### Post by alexandrius on 2010-09-07
@J.K.Makowka i'm kinda gamer and i feel that games like nexuiz (hight graphics set) has lack of fps :(
Can you please give me a link about removing nouveau and properly installing offical nvidia driver on lucid 32bit?

---

### Post by Perfect Storm on 2010-09-07
Just install the restricted drivers and th open driver will be disabled.

---

### Post by alexandrius on 2010-09-07
> Just install the restricted drivers and th open driver will be disabled.
I guess this is stupid question, how do i do that?
you mean this?
[img]http://i52.tinypic.com/al43v4.png[/img]

---

### Post by Perfect Storm on 2010-09-07
System ---> Administration ---> Hardware Drivers

---

### Post by Cavsfan on 2010-09-07
Just a thought: I have an nVidia Geforce 9800 GT 512MB and have always used the restricted driver which was version 185.
The other day I installed version 256.53 (the absolute latest for Linux directly from Nvidia) and I have noticed much improvement.

Here is the link for the driver [[COLOR=blue]_pick the one that matches your card. _[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
And once you have downloaded the executable here are [[COLOR=blue]_instructions on how to install it._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
Just start at step 2 as you already will have the driver.
Note: Do not un-blacklist the files that it says to blacklist after you install the driver.
If you read farther down the page, you will see that that will cause problems.

I downloaded and installed the latest driver and it went flawlessly.

---

### Post by Perfect Storm on 2010-09-07
> **Cavsfan said:**
> Just a thought: I have an nVidia Geforce 9800 GT 512MB and have always used the restricted driver which was version 185.
The other day I installed version 256.53 (the absolute latest for Linux directly from Nvidia) and I have noticed much improvement.

Here is the link for the driver [[COLOR=blue]_pick the one that matches your card. _[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
And once you have downloaded the executable here are [[COLOR=blue]_instructions on how to install it._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
Just start at step 2 as you already will have the driver.
Note: Do not un-blacklist the files that it says to blacklist after you install the driver.
If you read farther down the page, you will see that that will cause problems.

I downloaded and installed the latest driver and it went flawlessly.

Downside - you need to re-install the driver everytime the kernel get updated.

---

### Post by Cavsfan on 2010-09-07
One **note** though: I printed those instructions or you can write them down because after 
you uninstall the driver, you need the commands on that page to complete the task.

---

### Post by Cavsfan on 2010-09-07
> **Artificial Intelligence said:**
> Downside - you need to re-install the driver everytime the kernel get updated.

Thanks for that information! I will keep a back up of the driver and these printed out instructions!

Will it just boot up in limited video mode or will it not boot up at all when a new kernel is updated?
Thanks!

---

### Post by Perfect Storm on 2010-09-07
> **Cavsfan said:**
> Thanks for that information! I will keep a back up of the driver and these printed out instructions!

Will it just boot up in limited video mode or will it not boot up at all when a new kernel is updated?
Thanks!

It have been awhile I used nvidia drivers from nvidia's site, but back then you end up in CLI (commandline interface). I'm not sure what ubuntu does now.

---

### Post by Cavsfan on 2010-09-07
> **Artificial Intelligence said:**
> It have been awhile I used nvidia drivers from nvidia's site, but back then you end up in CLI (commandline interface). I'm not sure what ubuntu does now.

Thank you very much for that very valuable information! I would have been ready to kill something probably if the 
kernel was updated and I was left in CLI mode not having any idea what went wrong! I had deleted the driver after 
I installed it, but just re-downloaded it. I believe I will be good to go. I get emails from Lucid Changes and there 
is a new kernel 2.6.32-25-generic coming down the line soon.
Thanks again! :D

---

### Post by Perfect Storm on 2010-09-07
My pleasure.

---

### Post by Cavsfan on 2010-09-07
> **Artificial Intelligence said:**
> My pleasure.

This is exactly why I love this forum! Many friendly people willing to share knowledge and help others. :)

---

### Post by psoulocybe on 2010-09-08
[http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573")

sdennie shows how to automatically rebuild the modules after kernel updates.   Best post on these forums if you ask me!

---

### Post by Cavsfan on 2010-09-08
> **psoulocybe said:**
> [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

sdennie shows how to automatically rebuild the modules after kernel updates.   Best post on these forums if you ask me!

Man, I sure appreciate that! Thanks a lot! :D

---

### Post by Cavsfan on 2010-09-08
After looking over the script and setting everything up as it says, I noticed that it has not been updated since December 2008.
Has **sdennie** not been on in that long and does it still work? I have nVidia driver 256.53 64 bit.

[[COLOR=blue]_I did see this post in that tutorial about how to get by needing to enter "y" to give it the OK to install._[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7854902&postcount=51")

And I made the suggested change. I hope that was the right thing to do.

We'll see next kernel, which should be not too long as I am subscribed to Lucid Changes email list. I seen a new 
kernel coming down the line soon.

I don't see why it wouldn't work, but 2 ½ years is a long time in Ubuntu time! :p

---

### Post by Perfect Storm on 2010-09-08
It's around 17,5 years in human life :popcorn:

---

### Post by psoulocybe on 2010-09-08
I've used it through the last two kernel updates, and have not had to do anything to my drivers, so it should be fine.

---

### Post by Cavsfan on 2010-09-08
So, since that tutorial says I would need to run it once and then after that it will run auto.
I just enter this correct? **sudo ./usr/src/nvidia-driver** where nvidia-driver is the name of the script.

---

### Post by Cavsfan on 2010-09-17
I just updated the kernel to 2.6.32-24.43 and had to reboot and everything came up just fine. I didn't have to 
re-install the nVidia driver. I didn't have to do anything. Has anything changed or is it just when a new kernel is 
installed and not just updated. I did add that script, so that probably helped right?
Thanks! :D

PS I was wrong about seeing the 2.6.32.25 kernel coming in the future like I posted before. Guess it was just this update.

---

### Post by soldier1st on 2010-09-18
for installing the drivers i would just go to system/administration/hardware drivers, it's alot easier.

---

### Post by Cavsfan on 2010-09-18
> **soldier1st said:**
> for installing the drivers i would just go to system/administration/hardware drivers, it's alot easier.

You would need to read this entire thread. The default best driver is version 185 and I installed 256.53 from nVidia...

---

### Post by ilovelinux33467 on 2010-09-19
I prefer the closed source drivers as they seem to work better.

---

### Post by efikkan on 2010-09-20
If you want performance or features, the open source drivers cannot match the proprietary ones. The difference in performance is approx. by a factor of 8, wich means a high end graphics card like GTX 480 will perform lower than low-end graphics cards (like GT 240) with the proprietary drivers. To run a powerful graphics card with the open source drivers is a waste of money, and the open source drivers draw more power as well.

Unless you are running a workstation where graphics performance does not matter or anything similar, I would recommend staying away from the open source drivers, speaking as a developer and gamer.

---

### Post by Cavsfan on 2010-09-20
> **ilovelinux33467 said:**
> I prefer the closed source drivers as they seem to work better.

> **efikkan said:**
> If you want performance or features, the open source drivers cannot match the proprietary ones. The difference in performance is approx. by a factor of 8, wich means a high end graphics card like GTX 480 will perform lower than low-end graphics cards (like GT 240) with the proprietary drivers. To run a powerful graphics card with the open source drivers is a waste of money, and the open source drivers draw more power as well.

Unless you are running a workstation where graphics performance does not matter or anything similar, I would recommend staying away from the open source drivers, speaking as a developer and gamer.

Are you sure? How can version 185 be better than 256.53 :confused:
I haven't had any problems that I have noticed. How would I go about re-installing the closed source drivers - through Synaptic?
Thanks!
EDIT: I think I got confused and you are saying the later driver from nVidia is better right?

---

### Post by barney385 on 2010-09-20
> **Cavsfan said:**
> Just a thought: I have an nVidia Geforce 9800 GT 512MB and have always used the restricted driver which was version 185.
The other day I installed version 256.53 (the absolute latest for Linux directly from Nvidia) and I have noticed much improvement.

Here is the link for the driver [[COLOR=blue]_pick the one that matches your card. _[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
And once you have downloaded the executable here are [[COLOR=blue]_instructions on how to install it._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
Just start at step 2 as you already will have the driver.
Note: Do not un-blacklist the files that it says to blacklist after you install the driver.
If you read farther down the page, you will see that that will cause problems.

I downloaded and installed the latest driver and it went flawlessly.

Well thanks. I followed the instructions and I now have the 256.53 driver installed...

Took all of 5 minutes of my time and I'm here and posting so I assume it's working.

:guitar:

---

### Post by Cavsfan on 2010-09-20
> **barney385 said:**
> Well thanks. I followed the instructions and I now have the 256.53 driver installed...

Took all of 5 minutes of my time and I'm here and posting so I assume it's working.

:guitar:


Good! Open up nVidia X server settings and it will show the version.
Make sure you follow the instructions starting on post #15 on page 2 of this thread.
When a kernel is updated you have to reinstall the driver, but that can be setup 
automatically with the instructions **psoulocybe** provided. I didn't have any problem whatsoever 
when the kernel was updated a few days ago.  I do notice a difference.
I have Cairo-Dock and Compiz and when I open or close a window it burns and it looks fantastic!

---

### Post by barney385 on 2010-09-20
> **Cavsfan said:**
> Good! Open up nVidia X server settings and it will show the version.
Make sure you follow the instructions starting on post #15 on page 2 of this thread.
When a kernel is updated you have to reinstall the driver, but that can be setup 
automatically with the instructions **psoulocybe** provided. I didn't have any problem whatsoever 
when the kernel was updated a few days ago.  I do notice a difference.
I have Cairo-Dock and Compiz and when I open or close a window it burns and it looks fantastic!

I added sdennie's(sp) script also for the automatic kernel build update. That does correct the issue from what I understand. I also made not of the symlink just in case I run into an X-org problem.

I think that covers it?

Where are the nvidia x-server settings?

---

### Post by Cavsfan on 2010-09-20
> **barney385 said:**
> I added sdennie's(sp) script also for the automatic kernel build update. That does correct the issue from what I understand. I also made not of the symlink just in case I run into an X-org problem.

I think that covers it?

Where are the nvidia x-server settings?

System > Administration > nvidia x-server settings
But, I think when I updated my driver nvidia x-server settings went away.
I got it back via System > Preferences > Main Menu. I found it there and put the check mark beside of it.
But, today noticed that there was 2 and the one I added had a different icon, but did the same. I just 
removed from Main Menu and now have the original looking one.

You should be good to go. I already had one kernel update and I didn't have to do a thing. :)

---

### Post by Cavsfan on 2010-09-21
Wow! Something cool just happened! I installed the updates a while ago via CLI and noticed there 
were some nVidia stuff in there. When it finished installing I had to reboot. I looked back at 
NVIDIA X server settings and instead of version 256.53 installed I have 260.19.06!!!
Whooo Hooo! I didn't have to do anything either! Is that sweet or what?

:popcorn:

---

