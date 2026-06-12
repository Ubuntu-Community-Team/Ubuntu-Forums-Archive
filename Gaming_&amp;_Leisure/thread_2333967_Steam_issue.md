---
title: "Steam issue"
date: 2016-08-15
forum: Gaming &amp; Leisure
---

### Post by thekbb on 2016-08-15
Hello everyone - 

Full disclosure, I'm new to linux and new to Ubuntu, but finally made the switch from Windows today. upon trying to open steam I get  

Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
[2016-08-15 01:09:43] Startup - updater built Jul  8 2016 21:43:51
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)


I saw some other threads here mentioning installing the proprietary drivers for my GPU, which is a Radeon R7 250, but I am unsure how to go about doing that. Is there a specific command I run to uninstall my current drivers first? The AMD webpage only shows a driver listed for Ubuntu 15.04, and I was unsure if that will run on 16.04. Sorry if this has been answered before, I looked around and was unable to find it. I look forward to hearing from yall.

Thanks, 

J

---

### Post by howefield on 2016-08-15
You might want to read the release notes for 16.04

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Graphics_and_Display](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Graphics_and_Display)

To install proprietary drivers, one would normally look in the Additional Drivers application for anything that is offered.

---

### Post by thekbb on 2016-08-15
> **howefield said:**
> You might want to read the release notes for 16.04

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Graphics_and_Display](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Graphics_and_Display)

To install proprietary drivers, one would normally look in the Additional Drivers application for anything that is offered.


Hey, thanks for the response. I looked in Additional Drivers right away and nothing came up(which I thought was kind of odd). Not too sure why. 

[http://imgur.com/a/gcgOs](http://imgur.com/a/gcgOs)

^^ there is a screenshot of what comes up 

Thanks, 

J

---

### Post by howefield on 2016-08-15
Not so odd for an AMD graphics card on 16.04 as per the release notes.

Someone more knowledgeable about Steam and its requirements will most likely come into the thread, but it could be that your best bet would be to use Ubuntu 14.04 in order to get the proprietary drivers installed.

---

