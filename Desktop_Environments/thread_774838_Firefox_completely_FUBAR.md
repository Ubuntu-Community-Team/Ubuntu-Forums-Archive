---
title: "Firefox completely FUBAR"
date: 2008-04-29
forum: Desktop Environments
---

### Post by dracovich on 2008-04-29
Firefox has been a complete pain for me ever since i tried to upgrade to FF3B5 (B4 was my first beta and was fine), basically it was crashing a LOT, as in every 5-10 minutes, at seemingly random things. I had hoped it'd get better with an update to Hardy, but no such luck.

I googled it and found out that some peopel had been having similar problems, so i used some guide on how to downgrade back to ff2, which i did and it worked fine the first couple of hours, and then started getting extremely slow. Now it's slow every time i use it regardless of how long it's been used or how long the computer has been on. It's hogging my resources like crazy, as in constantly at at least 15% CPU and if i'm loading a page it goes up to about 50% (on a 2Ghz core2duo), the memory usage is fairly low though, less then 100 which seems weird for ff2.

I've tried marking everything i found in synaptics related to firefox for uninstallation and then reinstalling only ff2, but it's still the exact same and i'm seriously getting annoyed with it, as browsing is 95% of what i do. I'd switch to Opera or whatever if i wasn't so dependant on the plugins like firebug etc.

Any help would be greatly appreciated.

---

### Post by parkar on 2008-04-30
I'm running to the same problem which sucks (with FF3B5). It's really sad that Ubuntu's version runs terribly slower than my Vista's version. 

I had 3 tabs open and it slowed the entire system down. Not sure what do at this point. I'm trying to get into Linux and Ubuntu distro but this is a major turn off. When I can have Vista running everything and doing everything quickly (C2D 2ghz, 4GB ram, 7900GS) I don't know why I really need Ubuntu if it's going to be like this...this sucks.

---

### Post by cdude on 2008-04-30
It's a bug in firefox [urlclassifier3.sqlite]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728"), there is a workaround.


Edit>preferences>security

un-check
"tell me if the site I'm visiting is suspected attack site"
"tell me if the site I'm visiting is suspected forgery"

backup your urlclassifier3.* files from .mozilla/firefox/<yopur profile>. then remove all urlclassifier3.* files. (they'll be recreated)

rm  urlclassifier3.*

Restart firelfox.



**Another way of doing it:**
[COLOR="Red"][B]
Back up your files, such as bookmarks, passwords, cookies, etc.[/B][/COLOR]
delete your old profile, create a new profile
firefox -profilemanager

Edit>preferences>security
un-check
"tell me if the site I'm visiting is suspected attack site"
"tell me if the site I'm visiting is suspected forgery"

delete all urlclassifier3.* files in you new profile. (they'll be recreated)

rm urlclassifier3.* 


This way you will have a clean start, the down side is that you'll have to reinstall all your extension again.

---

### Post by dracovich on 2008-04-30
Sweet, i'll try that out, although for some reason today firefox is behaving nicely.

---

