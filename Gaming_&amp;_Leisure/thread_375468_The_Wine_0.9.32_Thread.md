---
title: "The Wine 0.9.32 Thread"
date: 2007-03-03
forum: Gaming &amp; Leisure
---

### Post by YokoZar on 2007-03-03
Hi, I make the Wine packages for Ubuntu.

You can get them from the page I put up here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Note that I'm just a packager at this point: I don't write any actual Wine code. Bug reports should be filed at Wine's bugzilla after looking them up in the Application Database. I do however, maintain the APT repository and the website above, so you can post issues with that here and I'll read them.


Anyway, the purpose of this thread is to talk about the latest version of Wine (0.9.32), as well as how it's working in Ubuntu. I'll read everything here.

Alongside some performance improvements, last version had some big regression that broke CS:Source, however it was fixed within a few days.  Since we have biweekly releases, you can now enjoy all these changes making their way into 0.9.32 - "release early, release often".

There's been more Direct3D performance improvements to this version as well.  I'm curious if anyone has noticed a significant difference - benchmarks would be really cool.

So, what else have people been experiencing? Feel free to give thoughts on Wine in general.

---

### Post by Jarn on 2007-03-03
It didn't seem to affect the way Guild Wars runs for me. It runs about the same as it did before. I haven't tried the other game I play (CS:S) yet, because I don't play that much anyway.

---

### Post by conjur3r on 2007-03-03
Thanks for making it easier for us ubuntu users to install wine.  After an apt-get update, it doesn't realise that there's a new version of wine out.  It still thinks my wine-0.9.31 is the latest.

I am using the repos found in [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list)

---

### Post by yabbadabbadont on 2007-03-03
Weird, that same source gave me the newer version when I updated a couple of hours ago.

---

### Post by YokoZar on 2007-03-04
> **conjur3r said:**
> Thanks for making it easier for us ubuntu users to install wine.  After an apt-get update, it doesn't realise that there's a new version of wine out.  It still thinks my wine-0.9.31 is the latest.

I am using the repos found in [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list)You're using edgy, right?

It's possible apt-get update timed out while trying to get the repository file.  Traffic gets a bit busy on release days.  Try it again and tell me if it works.

Also, tell me if it's timing out.

---

### Post by conjur3r on 2007-03-04
Yes I'm using Edgy.

I don't think it's timing out but I've just noticed the following MD5Sum mismatch message:

> 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Get:10 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources [639B]
Fetched 32.2kB in 3s (10.7kB/s)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/main/source/Sources.gz](http://wine.budgetdedicated.com/apt/dists/edgy/main/source/Sources.gz)  MD5Sum mismatch


Earlier today, I signed it using:
 # wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Edit, I should mention that I normally don't sign and just accept when it asks to install from untrusted sources but I signed wine's to see if I could get the latest .32 version.

---

### Post by YokoZar on 2007-03-04
> **conjur3r said:**
> Yes I'm using Edgy.

I don't think it's timing out but I've just noticed the following MD5Sum mismatch message:



Earlier today, I signed it using:
 # wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Edit, I should mention that I normally don't sign and just accept when it asks to install from untrusted sources but I signed wine's to see if I could get the latest .32 version.That's weird, when I md5sum that file I get the same thing as is in the signed Release file in apt/dists/edgy.

Something else must be going on.

---

### Post by bastiegast on 2007-03-04
In Oblivion the sneak cursor no longer remains on and functions properly!
Also the menu's show up properly, the video's no longer make the game crash, sound still has a lot of static, and sound with video's doesn't work.

I've been experiencing some weird problems with source games and I've also had it once with Oblivion, it might be a problem with my setup. The problem is that sometimes(quite often actually) while loading a source game it stops loading and my harddisk starts reading/writing like crazy, then the game starts sucking up memory freezing everything even mouse and ctrl-alt f1, after a while it crashes with some out of memory error. After the game is crashed all my apps come out of freeze. It also happened once while in-game and changing weapons.

I wonder if there's a way too limit the resources wine can use so I can at least do a wineserver -k if it happens.

---

### Post by conjur3r on 2007-03-04
I found out why, it was my transparent proxy still returning the stale versions.  This pretty much explains why I get it a couple of days later than everybody else.  Had to force a reload in firefox before apt-get would get the latest :)

Installing now!

---

### Post by Namtellum on 2007-03-04
Wine just autoupdated to .32 this morning and now i get this error when trying to run it.

wine client error:1d: version mismatch 276/278.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

I tried rebooting, any ideas on how to fix this?

---

### Post by bastiegast on 2007-03-04
Did you try removing it and then reinstall wine?

---

### Post by Namtellum on 2007-03-04
> **bastiegast said:**
> Did you try removing it and then reinstall wine?

Yeah, says the same thing.

---

### Post by YokoZar on 2007-03-04
> **Namtellum said:**
> Wine just autoupdated to .32 this morning and now i get this error when trying to run it.

wine client error:1d: version mismatch 276/278.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

I tried rebooting, any ideas on how to fix this?Wine was still running when you upgraded it.  You need to close all Wine applications after an upgrade before you can launch a new one.

wineserver -k  or killall -9 wine-preloader should force quit all running Wine instances.

If that doesn't work the other explanation is that you have a hand-compiled version you installed from source somewhere confusing Wine.

---

### Post by Namtellum on 2007-03-04
> **YokoZar said:**
> Wine was still running when you upgraded it.  You need to close all Wine applications after an upgrade before you can launch a new one.

wineserver -k  or killall -9 wine-preloader should force quit all running Wine instances.

If that doesn't work the other explanation is that you have a hand-compiled version you installed from source somewhere confusing Wine.

Yes that worked, thank you very much.

---

### Post by bastiegast on 2007-03-04
> **Namtellum said:**
> Yes that worked, thank you very much.

I wanted to  suggest that too, but i figured it wasn't neccesary since you already rebooted, weird.

---

### Post by timjayko on 2007-03-04
what games are worth trying out with wine?

---

### Post by YokoZar on 2007-03-04
> **timjayko said:**
> what games are worth trying out with wine?Whatever you want to play, unless it's known not to work in the latest version.

---

### Post by nicnocquee on 2007-03-05
please heeeelp....
i used wine 0.9.5 and it was working just fine. then i upgraded to wine 0.9.32 on edgy but wine's not working. i ran winecfg and i got this error:
```
err:ntdll:RtlpWaitForCriticalSection section 0x7ea71160 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
```
can anyone tell me what's wrong?thanks..

---

### Post by Shay Stephens on 2007-03-05
I am happy to report that Photoshop 7 continues to work.  No regressions I can find using .9.32 :-)

I also installed and played a little bit of Jedi Knight Outcast.

---

### Post by YokoZar on 2007-03-05
> **nicnocquee said:**
> please heeeelp....
i used wine 0.9.5 and it was working just fine. then i upgraded to wine 0.9.32 on edgy but wine's not working. i ran winecfg and i got this error:
```
err:ntdll:RtlpWaitForCriticalSection section 0x7ea71160 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
```
can anyone tell me what's wrong?thanks..Whoa, 0.9.5 is really, *really* old.  As in, there wasn't even a 0.9.5 package made for *Breezy* it was so old.

Anyway, try moving your ~/.wine folder to something else:

mv ~/.wine ~/.wine.backup

Then try winecfg again.  If you get it working, this means that you'll be able to at least get things working by reinstalling your windows apps - what we've done is basically recreated the entire Wine environment from scratch.  It wouldn't suprise me if the reason things got broken is from some very, very old cruft.

---

### Post by 45362457247 on 2007-03-05
Any chance of Solidworks working in wine on Ubuntu soon?

---

### Post by conjur3r on 2007-03-05
> **Shay Stephens said:**
> I am happy to report that Photoshop 7 continues to work.  No regressions I can find using .9.32 :-)

But what about Photoshop CS2!!  :D  I can dream!

That is the only windows app I still use.

---

### Post by yabbadabbadont on 2007-03-05
Total Annihilation installs fine and the intro movie plays but, as has been noted in the appdb, the cd music is not audible.  Also, when trying to change the screen resolution to be larger than the default 640x480, the resolution displayed becomes some insane set of numbers like 11123268x blah blah blah.  You get the idea.  Leaving it at the default res for testing, it then locked up while loading the terrain data.  I was able to switch workspaces and kill it though.  I can't tell if this is a regression as I've never tried to use it under wine before, but it has a gold listing in the appdb from a gentoo user for wine version 0.9.27.

---

### Post by dundern on 2007-03-05
umm i have a small/big problem i have installed my edubuntu and now i am seeking for ie. labasound2 update couse i have version 1.0.10 and package manager says that it is the lastest version of it so can someone send a list of those servers you use to check updates, or must i DL a new version of ubuntu i have 6.10 now but do i need to take x/k or desktop ubuntu???¨

thank you in foward

---

### Post by Mongoose on 2007-03-05
Yeah, 0.9.32 does introduce a new Oblivion bug however -- speedtree impostors sometimes enlarge to the point they fill the skybox.   Only happens in daylight shader.   Kind of funny, because this release fixed almost all the 'overlay issues'.  Sneak cusor and the cursor color codes work.

---

### Post by YokoZar on 2007-03-05
> **dundern said:**
> umm i have a small/big problem i have installed my edubuntu and now i am seeking for ie. labasound2 update couse i have version 1.0.10 and package manager says that it is the lastest version of it so can someone send a list of those servers you use to check updates, or must i DL a new version of ubuntu i have 6.10 now but do i need to take x/k or desktop ubuntu???¨

thank you in fowardSorry it's a bit hard to read your English, but I think I understand the problem you're getting at.

Are you sure you aren't using the edgy Wine repositories but the Dapper version of Edubuntu?

Try using the dapper repositories for Wine and see if that lets you install.

---

### Post by nicnocquee on 2007-03-06
it's still not working..still the same error,,ugh, what to do..?

---

### Post by dundern on 2007-03-06
it ssays that i miss some packages it requires higher version that i have and my package management says that the package i have installed is the latest one so where can i find a newer package list to add into that file wich it uses to check updates.....

---

### Post by cpk1 on 2007-03-08
same problem as nicnocquee here, purged wine and nuked .wine and I am still getting the error. however wine will work fine with a different user.

---

### Post by cpk1 on 2007-03-08
an update to my problem here.  It seems that the test user I have setup can run wine fine in his own X session but when I try to have the test user run wine through my X session I get the same (or similar) error.  If I try to run wine as my user in the test users X session it works... I guess my question is does this mean that this isn't a wine problem but rather PEBKAC problem or something went wrong with my X?

the short version of the error is:

err:ntdll:RtlpWaitForCriticalSection section 0x7ea91160 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)

---

