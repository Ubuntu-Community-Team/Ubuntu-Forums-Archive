---
title: "I lost some of my Dapper configuration when restoring from backup"
date: 2007-01-07
forum: Desktop Environments
---

### Post by greymoose58 on 2007-01-07
I recently did something stupid and messed up the permissions in my home directory. At least that's what it looked like I had done.

Having learnt the hard way (as do many people) I had a complete copy of my home directory (less a few easily replaced bits and pieces) as a backup. When I copied the original files into my home directory I found that I had lost my desktop settings as well as some of my Evolution settings.

So, now I have all of my Bookmarks in Firefox, my mail (whew) in Evolution but not my filters or e-mail accounts. 

I definitely restored ~/.evolution, ~/.gnome2_private/Evolution and ~/.gconf/apps/evoltuion and my e-mail account details are in the file ~/.gnome2_private/Evolution but aren't being used when Evolution starts up.

I have actually restored all of the files in ~/.gconf including the desktop files.  

I guess I've missed some configuration file(s) somewhere. Does anyone have any idea what I may have done wrong? I could manually set it all up again but I'd like to know what happened so that I can get things working properly in the future. 

Cheers.

**Update:** I've found that I'm also missing calendars and contacts from Evolution but the data seems to be where I'd expect to see it in my home folder.  The data for the launchers for my desktop panels all seem to be in my home folder too. I'm wondering if I've done something to stuff up the permissions or left out a file that directs the system to the config info.  ](*,)

This is beyond my understanding of the inner workings of Ubuntu. 

Thanks in advance for your help

---

