---
title: "gnome/firefox seem confused"
date: 2010-10-02
forum: Desktop Environments
---

### Post by discoross on 2010-10-02
Hi all,

I have a dual boot system. I previously had an fstab that mounted /dev/sda3 as /media/windows. I then linked my Desktop, Music, Videos, etc to /media/windows/Users/<me>/Desktop etc. so I shared a desktop and music and videos and firefox profiles. 
All was good, but I didn't like getting an icon on my desktop for the device mounted in /media. So I decided to move my mount point to /mnt/windows instead of /media/windows. 
First I changed my fstab to direct to the new /mnt/windows point and rebooted.
Then I changed all my links from Desktop->/media/windows/... to Desktop->/mnt/windows/...
Then I rebooted again. 

In the current state, my gnome desktop is full of icons from my home directory, not the Desktop directory even though the desktop directory exists and is full of the content it is intended to have.
When I try and start firefox, it complains that firefox is already running, which means it can't find it's profile directory. 
So something is messed up, although as far as I can tell, the links in my home directory point to the windows versions as they should.
When I was switching over, I noticed that in the middle reboot (when fstab was changed but the links weren't recreated), my Desktop and firefox were as they are now (buggy). But even though I re-created the links, the programs using them still don't work. It's almost as if they haven't been told of the second change.

Any suggestions? I feel like this has a simple fix...

---

