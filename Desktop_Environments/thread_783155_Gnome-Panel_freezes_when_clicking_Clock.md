---
title: "Gnome-Panel freezes when clicking Clock"
date: 2008-05-05
forum: Desktop Environments
---

### Post by WaddleDee on 2008-05-05
Hello, My Gnome-Panel always freezes when I click the Weather app/Clock, and I have to switch to a tty to kill it and it is fine when it starts again. 
Any ideas on how to fix? 

WaddleDee
(Anyone who helps gets :popcorn:.)

---

### Post by WaddleDee on 2008-05-06
Hi, I have not used these forums very much, and almost every problem I post here is ignored. (Exception of 1 problem) Am I required to pay canonical for tech support here? I think I read that somewhere...

---

### Post by 4Orbs on 2008-05-06
For me the problem stopped once I configured the location for weather info (my city). Right-click on clock for preferences. Hope it works for you also.

---

### Post by WaddleDee on 2008-05-06
I thank you for your reply.

I already have a location set. Do you think maybe if I change the location it will not freeze anymore?

---

### Post by 4Orbs on 2008-05-06
Setting the location did not fix it for me when I was running Gutsy, but it did fix the problem for me on Hardy. Matter of fact, upgrading from Gutsy to Hardy (using Synaptic) fixed the few problems I was unable to solve under Gutsy. A week after upgrading to Hardy I decided to do a fresh install of Hardy with the live cd which resulted in even better performance.

---

### Post by WaddleDee on 2008-05-06
Ok...

My Hardy is a clean install. (I never upgrade...)

Umm I changed locations and it still did not work

---

### Post by 4Orbs on 2008-05-07
One other point that may make a difference. When I configured the location, I had the desktop effects enabled because the panel would freeze when the effects were off. Also after configuring the location, if you can open the calendar without lock-up (even one time), there is an option on the bottom of the calendar to make that location the default location. I also set that option. Please understand that I am a Linux noob, so my advice might stink.

---

### Post by zzelinski on 2008-05-08
Same thing happens to me -- It worked fine, then I added two locations, set one as default, and now it freezes every time I click on the clock to open it. I have Hardy setup on another machine with basically the same settings and it works fine.

---

### Post by WaddleDee on 2008-05-08
Wow, Im still having the problem. Do you think we have to get on launchpad inorder for people to read this?

---

### Post by vrybas on 2008-05-10
I had the same problem only when i decided to set read-write synchronization with my Google calendar in Evolution. It began to freeze. I stopped to use Evolution "Google" plugin and began to use regular read-only Internet Calendar syncronization and that problem gone. Maybe you ned to make some magick with Evolution guys.

---

### Post by Netraam on 2008-05-19
> **vrybas said:**
> I had the same problem only when i decided to set read-write synchronization with my Google calendar in Evolution. It began to freeze. I stopped to use Evolution "Google" plugin and began to use regular read-only Internet Calendar syncronization and that problem gone. Maybe you ned to make some magick with Evolution guys.

I too only started having this problem after setting up evolution to sync with Google calendar...

---

### Post by pappfer on 2008-05-20
I had the same problem but since I've deleted my Google Calendar from Evolution it doesn't freeze anymore.

It worked great in Gutsy though.

---

### Post by hugmenot on 2008-05-20
This is fixed in the evolution-data-server package in hardy-proposed. This will come down through hardy-updates eventually.

---

### Post by Sparky222B on 2008-05-22
> **hugmenot said:**
> This is fixed in the evolution-data-server package in hardy-proposed. This will come down through hardy-updates eventually.

To get this update, go to System -> Administration -> Software Sources, go to Updates and check/enable Pre-released Updates.

Now use update manager, or use aptitude to update the evolution-data-server package.

---

### Post by hugmenot on 2008-05-23
Yes, I could have added that.

Besides, you may or may not be interested in this:
[http://ubuntuforums.org/showpost.php?p=5004498&postcount=7](http://ubuntuforums.org/showpost.php?p=5004498&postcount=7)

---

### Post by dextur on 2008-05-25
I have followed the instructions above but the issue is still present.

---

### Post by hugmenot on 2008-05-25
```
apt-cache policy evolution-data-server
```

---

### Post by Technophobia on 2008-06-16
I had this problem and I just went to synaptic looked for gnome-panel packages and picked reinstall on them. The problem is now gone for me.

Reinstalled the following packages:
gnome-panel (1:2.22.2-0ubuntu1)
gnome-panel-data (1:2.22.2-0ubuntu1)

---

### Post by goldenshale on 2008-07-07
Just to keep this going, it freezes for me also.  I am running Hardy on x86-64, and I don't have evolution installed, although I do still have the damn evolution data server because of various dependencies.  (Evolution would hang while maxing the CPU whenever I would compose a message, and it dealt horribly with my imap folders...)  When I was attempting to use evolution I also setup a google calendar.  Not sure what I can uninstall though, since I've since uninstalled evolution.

Setting the city and timezone didn't help anything.

---

### Post by pmorch on 2008-07-18
I was seeing the same problem. 

As I mentioned in [Going back to Gutsy : My Hardy experience]("http://ubuntuforums.org/showthread.php?t=743946&highlight=calendar+evolution+vpn") I had an account in Evolution that would connect to our Exchange server over a VPN connection. Because the calendar wants to display entries form the evolution accounts, opening the calendar would hang if the VPN wasn't up.

One place to look is to disable all Evolution accounts and see if this still happens.

Peter

---

### Post by boomsb on 2008-07-18
It appears as though the Google Calendars seem to slow it down considerably. When I disable them it pops up very quickly, otherwise it takes quite a few seconds to bring up the calendar.

---

