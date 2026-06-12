---
title: "Overheating problem slowing down my Dell E6400"
date: 2013-12-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 7dogtrainer on 2013-12-20
I read in an old thread that someone came up with a solution by downloading Bio`s A32....which is no longer available
Now unlike all you folks this is all Greek to me.
If anyone could be so gracious as to please walk me through what I need to do to install and where I might find an upgrade to A32 I would be really appreciative
I went to Dells site to try to find a upgrade to this driver but to me no information is available for a layman like me to sort through

Below find all the information I came across on a previous closed thread



[LIST]
[*][INDENT]This is a known problem for a few Dell models. The problem is not the machine getting hot, but the protection system to engage too early and throttle the cpu, gpu, memory and about everything. The protection system is working at the BIOS level. The present A20 (for E6400) somewhat alleviates the problem and already in A19 some thermal tables were rewritten in the BIOS.

Please have a look at the very extensive discussion in these two threads:
Dell forum: [http://en.community.dell.com/forums/.../19502938.aspx]("http://en.community.dell.com/forums/p/19247293/19502938.aspx")
Notebookreview: [http://forum.notebookreview.com/showthread.php?t=348221](http://forum.notebookreview.com/showthread.php?t=348221)

The solution should be provided by dell with BIOS updates. Here is the first semi-official note from dell:
[http://en.community.dell.com/blogs/d...hrottling.aspx]("http://en.community.dell.com/blogs/direct2dell/archive/2009/12/02/dell-on-laptops-and-throttling.aspx")
(This was apparently an attempt by dell to recover from the issue hitting first to some tech web pages and then to slashdot.)

So my advise is to
1. Update to the latest BIOS
2. Make sure that there is no dust blocking airflow (if you haven't opened the case and cleared the dust, there _definitely_ will be a thick layer of stuff blocking the flow! It makes a difference.).

I registered here to write this, because I noticed that not everybody knows this issue by now. So the issue is not a hot laptop, but the system throttling too early, as you can read from the the threads above. Here should be an extensive test report pdf by a user which shows the anatomy of the throttling and that the issue is not high temperatures: [http://www.sigmirror.com/files/44490...rottlegate.pdf]("http://www.sigmirror.com/files/44490_iweoz/throttlegate.pdf") (the report is 59 pages!)

I notice this issue in my E6400 while playing assault cube (in both Kubuntu jaunty and karmic). Very annoying effect is also the huge latency every time when the system goes through the next step in throttling, since that efects very much online gaming... :wink: With the latest bios the notebook is not throttling so easily, and I'm not sure if it has actually throtteld. I've used A20 only a couple of days now. I've got intel GPU, and what I've read, the issue is more prominent with the Windows users. This was actually first post that I saw where linux users were discussing about this (in one of the threads there were also one linux user apparently).

Hope this helps, guys![/INDENT]
[INDENT]Last edited by jartsa; February 7th, 2010 at [COLOR=#3E3E3E]04:34 AM[/COLOR]. **Reason:** add test report link[/INDENT]

[B][RIGHT][[IMG]http://ubuntuforums.org/clear.gif[/IMG]Adv Reply]("http://ubuntuforums.org/newreply.php?p=8787132&noquote=1")  [/RIGHT]
   
[/B]
[*]May 16th, 2011[RIGHT][#8]("http://ubuntuforums.org/showthread.php?t=1114378&p=10824474#post10824474")[/RIGHT]
[[COLOR=#000000]davehamptonusa[/COLOR]]("http://ubuntuforums.org/member.php?u=509609") 
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]**First Cup of Ubuntu**


[RIGHT]Join DateFeb 2008Beans8DistroUbuntu 9.04 Jaunty Jackalope[/RIGHT]


**Re: Dell Latitude e6400 system slowdown(over heat?) on 9.04Beta(x64) and 8.10(x32)**
[INDENT]The problem is that the nvidia integrated card/chipset is not properly cooled. This was the case with its predecessor, the d630 as well. 

No matter how much you engage the fans, they just dont give the nvidia chip the coverage that it needs. Although a great computer, don't spend too long in any graphic intensive environment. It just won't hack it.[/INDENT]



[B][RIGHT][[IMG]http://ubuntuforums.org/clear.gif[/IMG]Adv Reply]("http://ubuntuforums.org/newreply.php?p=10824474&noquote=1")  [/RIGHT]
   
[/B]
[*]April 20th, 2012[RIGHT][#9]("http://ubuntuforums.org/showthread.php?t=1114378&p=11858990#post11858990")[/RIGHT]
[[COLOR=#000000]allsteel[/COLOR]]("http://ubuntuforums.org/member.php?u=1619139") 
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]**First Cup of Ubuntu**


[RIGHT]Join DateApr 2012Beans1[/RIGHT]


**Re: Dell Latitude e6400 system slowdown(over heat?) on 9.04Beta(x64) and 8.10(x32)**
[INDENT]I've been using a Dell E6400 with a docking station for close to three years now. I'm currently running Debian Squeeze with backports. The Intel Speedstep, fan control and Nvidia graphics have always had issues. I finally nailed the problems using the following:

Use the latest BIOS - version: A32 (02/09/2012)
Use the latest NVidia drivers - version 295.40
Load kernel module needed to enable cpufreq scaling - acpi-cpufreq
IMPORTANT - Disable any script that calls /usr/bin/cpufreq-set

I found that invoking /usr/bin/cpufreq-set will cause the cpus to step down to 800MHz! If you do not invoke cpufreq-set, the default governor (ondemand) works properly.

Lastly, I highly recommend using an external cooling fan. I'm using the Thermaltake Mobile Fan II External USB Cooling Fan P/N - A1888[/INDENT]
[INDENT]Last edited by allsteel; April 20th, 2012 at [COLOR=#3E3E3E]02:40 PM[/COLOR].[/INDENT]

[B][RIGHT][[IMG]http://ubuntuforums.org/clear.gif[/IMG]Adv Reply]("http://ubuntuforums.org/newreply.php?p=11858990&noquote=1")  [/RIGHT]
   
[/B]
[*]May 1st, 2012[RIGHT][#10]("http://ubuntuforums.org/showthread.php?t=1114378&p=11896430#post11896430")[/RIGHT]
[[COLOR=#000000]yell0w[/COLOR]]("http://ubuntuforums.org/member.php?u=261938") 
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]**First Cup of Ubuntu**


[RIGHT]Join DateMar 2007Beans5DistroUbuntu 7.04 Feisty Fawn[/RIGHT]


**Re: Dell Latitude e6400 system slowdown(over heat?) on 9.04Beta(x64) and 8.10(x32)**
[INDENT]Bios A32 fixed the issue for me. (released 4/26/2012)

[http://www.dell.com/support/drivers/...eId=2944386393]("http://www.dell.com/support/drivers/us/en/555/DriverDetails?driverId=909TW&fileId=2944386393")

This version got an updated thermal table which fix the cpu over-throttling issue.

Now my computer temperature runs up to 59oC without any freezing, whereas 45oC+ slowed it down to a crawl before.[/INDENT]
[/LIST]
Please Help as my machine is getting slower daily it seems
Wishing you all a Great Holiday season

---

### Post by mörgæs on 2013-12-20
[http://www.dell.com/support/drivers/us/en/19/Product/latitude-e6400](http://www.dell.com/support/drivers/us/en/19/Product/latitude-e6400)

---

