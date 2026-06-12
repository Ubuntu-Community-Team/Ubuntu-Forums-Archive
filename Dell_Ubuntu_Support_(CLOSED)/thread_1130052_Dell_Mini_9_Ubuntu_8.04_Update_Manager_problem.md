---
title: "Dell Mini 9 Ubuntu 8.04 Update Manager problem"
date: 2009-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JEBB on 2009-04-19
I run Update manager and it tries to download 115 files but stops at about 110 and gives me an error message "Could not download all repository indexes".  In that window it gives a list of sites that failed beginning with: 

[http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/bianary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/bianary-lpia/Packages.gz) 404 Not found

There are 6 more all ending with 404 Not found.

What do I do next?

Thanks.

---

### Post by superm1 on 2009-04-19
You've added the wrong repositories.

All you should have in /etc/apt/sources.list are repositories for **dell-mini.archive.canonical.com**

---

### Post by JEBB on 2009-04-19
I didn't add them, that's how it came equipped from Dell.  I went to Software Sources and uncheck all but the one you said and ran update manager again and it told me my system is up-to-date.  

That it is up-to-date disagrees with some earlier information I got when I inquired about why Sunbird 0.9 as a deb file wouldn't install.  There I was told I needed to have my system up-to-date for it to work.  

(Sunbird 0.7 was installed from the depository, but it freezes if I try to import a file with my calendar data from another source.  I did get Sunbird 0.9 installed another way and got my calendar data imported.)

---

### Post by superm1 on 2009-04-19
> **JEBB said:**
> I didn't add them, that's how it came equipped from Dell.  I went to Software Sources and uncheck all but the one you said and ran update manager again and it told me my system is up-to-date.  

That it is up-to-date disagrees with some earlier information I got when I inquired about why Sunbird 0.9 as a deb file wouldn't install.  There I was told I needed to have my system up-to-date for it to work.  

(Sunbird 0.7 was installed from the depository, but it freezes if I try to import a file with my calendar data from another source.  I did get Sunbird 0.9 installed another way and got my calendar data imported.)
It doesn't come equipped like that, likely some action of yours enabled them - not necessarily you going to do it yourself.  Maybe when you were trying to install the sunbird deb.

---

### Post by amazon_jane21 on 2009-04-19
My Mini 9 is having the same problem...and that is how it was set up out of the box before I did anything. Is there perhaps an update that runs when you first run update manager that adds these repositories? The suggestion to uncheck all but the dell mini repositories worked perfectly. Thanks so much.

---

### Post by snowpine on 2009-04-19
> **superm1 said:**
> It doesn't come equipped like that, likely some action of yours enabled them - not necessarily you going to do it yourself.  Maybe when you were trying to install the sunbird deb.

The Dell Minis are definitely shipping with broken source lists. Search the forums; there have been a ton of threads on this over the past couple of weeks. I had this same error as well until I replaced 8.04 with 9.04.

---

### Post by JEBB on 2009-04-19
Snowpine:  
I'm happy to hear that the problem isn't my fault.  I've used Ubuntu  a little bit on an old Thinkpad but never had so many problems as I've had with Ubuntu on this Dell Mini 9.  

Your statement about 9.0.4 sounds really promising.  I had begun to believe I needed to buy and install Mac OSX to have a useful netbook.  I had hoped to avoid that expense.  

How did you install 9.04, which is still a beta, so that everything works.  Thanks.

---

### Post by superm1 on 2009-04-19
> **snowpine said:**
> The Dell Minis are definitely shipping with broken source lists. Search the forums; there have been a ton of threads on this over the past couple of weeks. I had this same error as well until I replaced 8.04 with 9.04.

I'm fairly confident this is not the case.  The image that ships with them has not changed since they started shipping.  The things that have changed however are the web updates.

You can restore using the recovery media and see that everything is fine.  If something is wrong with the web updates however, it would be best that the update causing problems is identified.  This also would be surprising however, since everything has an in depth QA process before it's released.

---

### Post by roob47 on 2009-04-20
Well i bought two mini's in the past 4 month's both with ubuntu one "previously ordered new" and one Brand Spankin new and both are updating fine , Even the latest and longest software update. So i have to think these are isolated incident's, hope this help's

---

### Post by snowpine on 2009-04-20
> **superm1 said:**
> I'm fairly confident this is not the case.  The image that ships with them has not changed since they started shipping.  The things that have changed however are the web updates.

You can restore using the recovery media and see that everything is fine.  If something is wrong with the web updates however, it would be best that the update causing problems is identified.  This also would be surprising however, since everything has an in depth QA process before it's released.

[http://ubuntuforums.org/showthread.php?t=1124631](http://ubuntuforums.org/showthread.php?t=1124631)
[http://ubuntuforums.org/showthread.php?p=7102213](http://ubuntuforums.org/showthread.php?p=7102213)
[http://ubuntuforums.org/showthread.php?t=1115650](http://ubuntuforums.org/showthread.php?t=1115650)
[http://ubuntuforums.org/showthread.php?t=1104644](http://ubuntuforums.org/showthread.php?t=1104644)
[http://ubuntuforums.org/showthread.php?t=1107460](http://ubuntuforums.org/showthread.php?t=1107460)
[http://ubuntuforums.org/showthread.php?t=1105595](http://ubuntuforums.org/showthread.php?t=1105595)
[http://ubuntuforums.org/showthread.php?t=1107541](http://ubuntuforums.org/showthread.php?t=1107541)

---

### Post by ugm6hr on 2009-04-20
> **snowpine said:**
> I had this same error as well until I replaced 8.04 with 9.04.

Of course, the simpler solution is just to correct the repository list.

My (default) Mini 9 works just fine with the original Dell Ubuntu.

---

### Post by superm1 on 2009-04-20
> **snowpine said:**
> [http://ubuntuforums.org/showthread.php?t=1124631](http://ubuntuforums.org/showthread.php?t=1124631)
[http://ubuntuforums.org/showthread.php?p=7102213](http://ubuntuforums.org/showthread.php?p=7102213)
[http://ubuntuforums.org/showthread.php?t=1115650](http://ubuntuforums.org/showthread.php?t=1115650)
[http://ubuntuforums.org/showthread.php?t=1104644](http://ubuntuforums.org/showthread.php?t=1104644)
[http://ubuntuforums.org/showthread.php?t=1107460](http://ubuntuforums.org/showthread.php?t=1107460)
[http://ubuntuforums.org/showthread.php?t=1105595](http://ubuntuforums.org/showthread.php?t=1105595)
[http://ubuntuforums.org/showthread.php?t=1107541](http://ubuntuforums.org/showthread.php?t=1107541)
Maybe not all of  those threads, but several of them people are "trying" to update to 8.10, which is not supported.  I agree this should be blocked out somehow.

Any of them that are *not* that, it's possible there is a bug at play.

---

### Post by lswartz on 2009-04-21
JEBB

I thought it was something you did until a few minutes ago. I just downloaded 185 updates going from about 500 MB free space to 162 MB free :(. I only have a 4GB HD.

The only thing I changed before those updates was to remove Bluetooth Analyzer using add/remove applications by unchecking it. Lots of things changed, wireless & battery icon at the top of the screen. The software sources changed too, still dell-mini.archive.cononical.com/updates hardy-dell-mini but there are only 2 now & there were at least 6 before.

Not too sure what to do now - duct tape maybe :P.

---

### Post by superm1 on 2009-04-21
> **lswartz said:**
> JEBB

I thought it was something you did until a few minutes ago. I just downloaded 185 updates going from about 500 MB free space to 162 MB free :(. I only have a 4GB HD.

The only thing I changed before those updates was to remove Bluetooth Analyzer using add/remove applications by unchecking it. Lots of things changed, wireless & battery icon at the top of the screen. The software sources changed too, still dell-mini.archive.cononical.com/updates hardy-dell-mini but there are only 2 now & there were at least 6 before.

Not too sure what to do now - duct tape maybe :P.
Try to clean up the old downloaded packages maybe.  They're kept in /var/cache/apt/archives

---

### Post by lswartz on 2009-04-21
> **superm1 said:**
> Try to clean up the old downloaded packages maybe.  They're kept in /var/cache/apt/archives

Wow! You are fast. I found the files exactly where you said & they match the names of the updates. Now what do you mean by "clean up".

Please take your time, I am going to eat some lunch :).

By the way, thanks.

---

### Post by superm1 on 2009-04-21
> **lswartz said:**
> Wow! You are fast. I found the files exactly where you said & they match the names of the updates. Now what do you mean by "clean up".

Please take your time, I am going to eat some lunch :).

By the way, thanks.
I think actually just running:

```
sudo apt-get clean
```

Will handle it for you

---

### Post by lswartz on 2009-04-21
> **superm1 said:**
> I think actually just running:

```
sudo apt-get clean
```

Will handle it for you

Nice fix. :KS

I was thinking of just putting them in the trash can but I didn't want to assume clean = delete. I really need to finish reading that Ubuntu pocket guide that I downloaded. I'm up to 2 commands now with the 2d being ```
df -h
```

Thanks again.  I hope JEBB gets his fixed too

---

### Post by JEBB on 2009-04-21
> **superm1 said:**
> I'm fairly confident this is not the case.  The image that ships with them has not changed since they started shipping.  The things that have changed however are the web updates.

You can restore using the recovery media and see that everything is fine.  If something is wrong with the web updates however, it would be best that the update causing problems is identified.  This also would be surprising however, since everything has an in depth QA process before it's released.

As I just asked at another thread, would you please give us a complete list of the correct sources that should be included.  Thanks.

---

### Post by Cowchip7 on 2009-04-21
> **lswartz said:**
> JEBB

I thought it was something you did until a few minutes ago. I just downloaded 185 updates going from about 500 MB free space to 162 MB free :(. I only have a 4GB HD.

The only thing I changed before those updates was to remove Bluetooth Analyzer using add/remove applications by unchecking it. Lots of things changed, wireless & battery icon at the top of the screen. The software sources changed too, still dell-mini.archive.cononical.com/updates hardy-dell-mini but there are only 2 now & there were at least 6 before.

Not too sure what to do now - duct tape maybe :P.

Sounds about right. I also had 185 or so updates. The battery and wireless icon changed... and so did my repositories. As you mentioned, now there are only 2 Dell repositories. Also, I remembered having the option to check the normal Ubuntu repos (like multiverse)... however, if you were to do this, it wouldn't work. Seems like Dell took finally took those repos away... which is a good thing because it seemed to confuse people using the Dell lpia version.

---

### Post by duckfeet on 2009-04-22
I had to go into synaptic and just remove any non-canonical repositories...I think they got added when we updated apps or something, but now it's all cool, and works fine...and I've removed all kinds of stuff I don't use, cheese, and printer drivers and even openoffice...for me it really is just a cool little netbook...and I'm down to 1.5gb available disk space(out of 4 gb)  after cleaning up and removing old kernel mirrors...

works fine, happy as can be...I know some are getting discouraged, and loading up other os's...but this dell/canonical version is designed for this little cpu, and I find it works fine...you put in other ubuntu versions, you'll just be trading in one set of complications for another...

I had a day or two of getting used to using the forums again...as I realized the futility of getting thru to Dell for anything...but once I got back into 'self-reliant' mode, I've been real happy w/my setup...well, as long as you guys are here, anyway... :-)

---

### Post by lswartz on 2009-04-22
> **Cowchip7 said:**
> Sounds about right. I also had 185 or so updates. The battery and wireless icon changed... and so did my repositories. As you mentioned, now there are only 2 Dell repositories. Also, I remembered having the option to check the normal Ubuntu repos (like multiverse)... however, if you were to do this, it wouldn't work. Seems like Dell took finally took those repos away... which is a good thing because it seemed to confuse people using the Dell lpia version.

You are right, the options in Software Sources, Updates, were removed. 

It seems as though the updates are timed so you don't get them all on the 1st day. Mine checks updates daily & I remember getting 5 updates the 1st day, about 15 updates about a week ago. The 185 updates came on the 38th day. 

Thanks to superm 1 I now know what file to clean & what clean means :).

---

### Post by lswartz on 2009-04-22
> **duckfeet said:**
> I'm down to 1.5gb available disk space(out of 4 gb)  after cleaning up and removing old kernel mirrors...

I know some are getting discouraged, and loading up other os's...

I had a day or two of getting used to using the forums again...as I realized the futility of getting thru to Dell for anything...but once I got back into 'self-reliant' mode, I've been real happy w/my setup...well, as long as you guys are here, anyway... :-)

1.5 GB free, I am impressed. I'll remove some more as I need space. My wife wanted Picasa so I guess I don't need Gimp & I am thinking of adding VLC player. Guess I better make some more space soon.

I think it is easy to quit & go back to an OS that you know. I've read the apple guys threads & while they are having fun installing X, I don't see any advantage worth the price of that OS. Half the fun is learning something new. The Mini 9 has been flawless & the OS has never locked up. When something does look a little weird, this forum helps a lot.

---

### Post by lswartz on 2009-04-22
> **JEBB said:**
> As I just asked at another thread, would you please give us a complete list of the correct sources that should be included.  Thanks.

Is this what you are looking for?

---

### Post by Kensoi on 2009-04-23
Sorry Didn't Mean To Confuse Issues.

@ JEBB These Are The Links In My Source List.

---

### Post by duckfeet on 2009-04-23
Well, I'm laughing a little--at myself--on reading this, as I had a really long night, over one of my removals...I had gone into Synaptics and removed all of the installed Evolution Files, and when I rebooted, my desktop, all the gnome stuff, was gone, and it looked just like a Unix deskstop server in the old days: just a bash shell, I think...and I spent hours in embarrassed misery on here, trying to get everything back--I did, but I had to reload desktop...

But I went back in today, and installed Thunderbird, and removed Evolution again...but this time I paid attention, and realized that it was Evolution-data-server-common, that also removed the gnome and desktop stuff I wanted....

Oh, I also went into /boot/grub/menu.lst so I could put a couple seconds space in the bootup, so I can hit "escape" when it's booting, and get the recovery kernels...as, knowing me, I'll be there again ;-)

So I still have what I wanted: a nice little webbook without any of the OpenOffice, or Cheese, or Games, or silly Yahoo toolbars, that I don't use, and I've got 1.3 gb of free space on a 4gb ssd, rather than 1.5gb...but it was steep learning curve haha...

Best wishes...

> **lswartz said:**
> 1.5 GB free, I am impressed. I'll remove some more as I need space. My wife wanted Picasa so I guess I don't need Gimp & I am thinking of adding VLC player. Guess I better make some more space soon.

I think it is easy to quit & go back to an OS that you know. I've read the apple guys threads & while they are having fun installing X, I don't see any advantage worth the price of that OS. Half the fun is learning something new. The Mini 9 has been flawless & the OS has never locked up. When something does look a little weird, this forum helps a lot.

---

