---
title: "Firefox weird problem"
date: 2005-12-16
forum: General Help
---

### Post by DarkAngel88 on 2005-12-16
I allready posted this thread in the "Other application support" section without any success, so I'm trying here.



> Hi there,

First time poster here, I've been reading you since a while and I found most of the info needed here, thanks to all the ubuntu experts helping this communauty !

But this time, I got a weird looking problem with firefox 1.5. The thing is that after a fresh install I get firefox running without any problem. I installed all my extensions and start customizing Firefox. After, let say 5-10 startup, I get a different firefox from the version I'm used to work with. For example, I can't use the google search box..all I get is a magnifying glass and I cannot add any search engine. I looked on the forum and tried the few examples how to get it back without any success. Also, I always lose my saved session (saved with Tabmixplus). I don't lose my extensions or my bookmarks but everything else I customize before. I tried different ways to get my settings back like reinstalling Firefox using the wiki page without any success. Even tried a firefox script here but I still got the same problems... First it works... and then, after like 10 minutes of closing and restarting firefox (for test issues), I get this annoying problem.

Now... I'm quite sure I'm not the only one with this problem. Looks like a permission problem to me but hey.. it's only been 1 week since I use ubuntu. I really like this distro, but I found this problem really annoying If someone can help me I'll be greatfull !!

PS : Sorry for my english... it's not my native language !

Thank you very much !

---

### Post by DarkAngel88 on 2005-12-19
Anyone ??  :)

Still got the same problem...

Thanks

---

### Post by canadianwriterman on 2005-12-19
It sounds like you are getting the default Firefox 1.0.7 that comes with Ubuntu in your subsequest startups. If you installed Firefox 1.5 as in the Wiki, it leaves the existing default Firefox in place and installs Firesfox 1.5 as an addition. The Wiki has a procedure for creating new links so that only the new Firefox opens, but I found it a bit erratic. As a first step, I'd go into **Preferences > Default **Programs and set the new Firefox as your new default browser. If it says the default browser is **mozilla-firefox**, then you have the old version still set. Change it to simply **firefox **to set the new version.

**EDIT: Wow... sorry for the triple post. My internet connection is doing strange things right now.**

---

### Post by canadianwriterman on 2005-12-19
It sounds like you are getting the default Firefox 1.0.7 that comes with Ubuntu in your subsequest startups. If you installed Firefox 1.5 as in the Wiki, it leaves the existing default Firefox in place and installs Firesfox 1.5 as an addition. The Wiki has a procedure for creating new links so that only the new Firefox opens, but I found it a bit erratic. As a first step, I'd go into **Preferences > Default **Programs and set the new Firefox as your new default browser. If it says the default browser is **mozilla-firefox**, then you have the old version still set. Change it to simply **firefox **to set the new version.

---

### Post by canadianwriterman on 2005-12-19
It sounds like you are getting the default Firefox 1.0.7 that comes with Ubuntu in your subsequest startups. If you installed Firefox 1.5 as in the Wiki, it leaves the existing default Firefox in place and installs Firesfox 1.5 as an addition. The Wiki has a procedure for creating new links so that only the new Firefox opens, but I found it a bit erratic. As a first step, I'd go into **Preferences > Default **Programs and set the new Firefox as your new default browser. If it says the default browser is **mozilla-firefox**, then you have the old version still set. Change it to simply **firefox **to set the new version.

---

### Post by DarkAngel88 on 2005-12-19
Thanks for your answer canadianwriterman !!

I looked in the default browser and it was allready set to firefox.  Should I completly remove the ubuntu version of firefox ??

Thanks, and greets from Montreal ! ;)

---

### Post by canadianwriterman on 2005-12-19
No, don't remove it. It's required for some other functionality in the Ubuntu system. 

When you're opening Firefox 1.5, are you using an icon on the desktop or panel, or do you sometimes open it from the Applications menu? Perhaps if you are opening it from two different locations, one is set to open the old version and one the new version.

---

### Post by kingsidy on 2005-12-19
just follow the wiki. You migh have forgotten to link the new firefox 1.5 so that your computer uses the new one only. double check on that. Or there is some script that install firefox 1.5 for you and does the necessary changes also. You can look around the forum for that.

---

### Post by DarkAngel88 on 2005-12-19
I tried the wiki multiple times without any success.  I also tried the .sh file to install firefox.  The problem is really that after a fresh install of firefox, everything is working fine.  After a couple of "open" of firefox I get this weird problem.  Like if I was loosing the rights on the /.mozilla directory without any specific reasons...

---

### Post by canadianwriterman on 2005-12-19
DarkAngel, you might try going to Synaptic and uninstalling Firefox 1.5 (I'm assuming it will show up in Synaptic) and then downloading and installing the latest version of Automatix, which now includes Firefox 1.5 as an installation option. Automatix is a wonderful script that handles the complete installation automatically. Perhaps that would work better for you.

Also, I forgot to send greetings back to you from Toronto, where we're freezing our butts off!

---

### Post by DarkAngel88 on 2005-12-19
Interresting canadianwriterman, I never tried the Automatix script.  I'll do a little search on that on the forum.  Thank you very much for this info, I'll try it when I'll get back home.  I'll post the result here !

PS : Pretty cold in here too !!  But hey, this is what winter looks like in Canada I guess !! :P

---

### Post by canadianwriterman on 2005-12-19
I just got thinking that the uninstall may not be as easy as going to Synaptic, since the Wiki instructions included backing up and renaming files so that the two versions could remain on your system Check the Wiki for instructions of reverting to the original version of Firefox first. Even if you can't "uninstall" the Wiki version of Firefox, I don't think it could hurt to reinstall 1.5 using Automatix and see what happens. Good luck!

---

### Post by DarkAngel88 on 2005-12-19
I just remember that I tried running firefox as root and everything was working fine (sudo firefox).  I was able to use the google search box in firefox without any problems.. but I'm quite sure that there must be a way to work with firefox without being root...

Anyway... like I said.. I'll try this tonight and get you back with the (good !?!?) results !

thanks again !

---

### Post by DarkAngel88 on 2005-12-20
Good morning everybody !!

I tried what we have talked about yesturday without any good results.  But I might have found out something related to this problem.  I completly erased the /.mozilla folder to restart with a "like new" install and my problem wasn't there.  So I started installing all my extensions except forecastfox cause I didn't have a recent version in my backups.  Everything was workin' fine until I decied to install the famous forecastfox.  So it seems that my problem was related to .... a simple extension :confused: 

Now I don't know for how long I should test firefox without forecastfox but if it turns out that it was really the problem... well I cannot imagine that I'm the only one in the linux communauty using forecastfox.  So looks like that in my config, forecastfox is the actual problem (for now...)

Don't know what to think right now...

---

