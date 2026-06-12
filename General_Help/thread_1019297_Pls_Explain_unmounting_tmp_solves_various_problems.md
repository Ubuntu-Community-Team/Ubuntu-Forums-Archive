---
title: "Pls Explain: unmounting /tmp solves various problems"
date: 2008-12-23
forum: General Help
---

### Post by joltvolta on 2008-12-23
If you don't want the whole story, please scroll down the summary. 


Backstory:

Couple days ago I turned off my computer as there were high winds in my area and didn't wish to risk a power outage while it was on. When I turned on my computer it went through a normal boot-up. 

When opening firefox 3.0.5, link buttons were missing, and the bookmarks drop down menu didn't show anything, although I was still able to goto sites. 

File browser (nautallis?) was missing the quick links to frequently used directories (example: downloads). There were also other random issues that I bumped into. 

I realized the partition that ubuntu sits on was full. The system didn't have room to operate correctly. Moved large video and music files to a secondary HD, freeing up 18gigs. Things returned to normal, sorta. Flash embedded movies (example: youtube) would only play for about 10sec and cease up. There were other issues with saving files for configurations in KAlarm, and for monitor resolution settings (/X11/xorg.conf). 

After some forum searching (I recommed using google.com [<search text> site:ubuntuforums.com]) I found people having issues with /tmp only having a small size to start with and being completely full. One solution, and the solution I choose, was to unmount the *******. After that, things were running smoothly. I could save configurations and such. Flash video played without problem, etc. 

Question is, why did this happen? 

summary: 

Filled up the HD partition that ubuntu is installed on. 
Caused programs like firefox not to load correctly
Freed up space, most issues resolved
Flash movies (youtube.com) wouldn't play past ~10sec
Couldn't save changes to config files
Saw that /tmp directory was allowed a small amount of space & full
Unmounted /tmp directory
Solved issues of not being able to save to config files or watch video via Flash

Question: Why did this solve the problem? Why was /tmp only allowed a small amount of room?

Thanks.

---

### Post by dcstar on 2008-12-23
> **joltvolta said:**
> 
........
Question: Why did this solve the problem? Why was /tmp only allowed a small amount of room?


/tmp is usually not a separate filesystem, but part of the root filesystem.

If you had a separate /tmp, then it can fill up (no matter how big it is) and cause the problems you described, if you unmounted it then the /tmp files will then go into the /tmp directory which is on your root filesystem (until the next reboot if /tmp is in your /etc/fstab).

/tmp should be automatically cleaned up as part of the boot process, so old files (> 1 day) that may have clogged up things are deleted.

It is actually better to have a separate /tmp for greater system stability, but you can end up wasting a bit of disk space (which isn't such a problem these days with massive drive sizes).

---

