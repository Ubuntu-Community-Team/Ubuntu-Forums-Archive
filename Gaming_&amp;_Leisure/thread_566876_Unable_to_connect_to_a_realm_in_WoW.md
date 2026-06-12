---
title: "Unable to connect to a realm in WoW"
date: 2007-10-04
forum: Gaming &amp; Leisure
---

### Post by prammy on 2007-10-04
Hello everyone,

As of today, I am unable to connect to WoW at all. I can start WoW and login successfully, but when I connect to the realm, the progress bar moves very slowly and at the end, I get disconnected.

I have Windows installed on the same machine and WoW works fine there.

Also this started happening today, I was playing fine under Linux last night.

Just wondering if anyone else has experienced this issue.

Using:
Feisty
Wine 0.9.46
nvidia driver 100.14.19

---

### Post by keeper-of-the-real on 2007-10-14
I have the EXACT same problem.  It has been increasing in frequency for the past few weeks.  

I played last night with no problem and then today I can not get it.  I can't figure it out.  Unfortunately I've migrated to playing Wow on my Vista machine (which is killing me).  

If you find a way to fix this please share!

---

### Post by keeper-of-the-real on 2007-10-14
I checked the log folder and found the following:

10/14 14:20:39.269 Error loading WTF\Account\k33p3rs\SavedVariables.lua

10/14 14:20:39.269 Error loading WTF\Account\k33p3rs\Azshara\Vanhoffak\SavedVariables.lua


by the way I'm running the same wine as you and I have a GeForce7600GS AGP.  

I don't believe this has anything to do with a video card though, this is something with WoW and/or wine. 

It seems to work at random.  I'm contimplating whether my permissions  had something to do with it.  I'm not a linnux expert, but the game seemed to run fine as a user, but many of the contents of the World of Warcraft folder were set with root permissions.  I manually tried to set them to user, but that doesn't seem to help. 

I haven't quite grasped the whole concept of what should be root or user for wine or wow.  I just don't get it.  I don't think any of the tutorials covered that and I think permissions are partly to blame for this error.

---

### Post by keeper-of-the-real on 2007-10-14
Ok minutes later I was able to get inside the realm.

This is what I did:

I located my WTF folder and found another folder labelled WTF.20070710...etc  

something like that anyway.  I wish I wrote it down now.  It appears to be a backup saved file of a WTF files and its contents that worked on October 7th.

I renamed the current NON working WTF to WTF.broken and renamed the WTF.20071007 or whatever to just plain old WTF.

I started Wow from the icon on my desktop and BOOM.. I went straight into the realm.

The lau file seems to be the problem.  I'm thinking, perhaps I was running Wow as root at some point, which saved the game at logout with root permissions. screwing up the lau files?  

Either way, it works now.  How long though?  I guess I'll find out.

---

