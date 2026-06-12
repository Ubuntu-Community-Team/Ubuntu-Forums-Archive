---
title: "Panel missing on startup - does anyone know what causes this?"
date: 2016-10-31
forum: Desktop Environments
---

### Post by zx6r1033 on 2016-10-31
Allow me to preface this by saying I am not stuck or anything like that. I have found a temporary solution... which I am hoping can help with figuring out what the cause is. 

The issue: once in a while, when the DE loads, I have a background, but no panel on the bottom of the screen. I can right click and access settings. This has happened twice already

The fixes - according to google:  Most searches end with solutions such as deleting or renaming the .cache folder, or taking ownership via chown. Removing the folder works, but resets the settings. chown doesn't work at all. 

My workaround:

The first thing I noticed was that I could still bring up the search box (alt + F2) and launch programs that way. 

Then I realized I installed ksuperkey a few days ago, so I hit the super key, and the panel launched, but it was on the right side of the screen. 


My temporary fix: I went into System Settings> Startup and Shutdown > Desktop Session, and selected "Start with an empty session". On reboot, the issue was resolved.


I am thinking at this point that it has something to do with restoring the prior session. I will note - when I shut it down, there were no open programs. 


I am hoping to get two things out of this post. 1) an explanation of what is happening and why, and 2) potentially helping someone else with the same issues (though I am sure someone else has already gotten this far before me.)

---

