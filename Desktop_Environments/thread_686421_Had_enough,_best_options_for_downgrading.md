---
title: "Had enough, best options for downgrading"
date: 2008-02-03
forum: Desktop Environments
---

### Post by speedway on 2008-02-03
Hi All

I am now totally sick of my 7.10 install. It continually locks up, gets slower and slower requiring a reboot (ala Windows), Firefox goes goodness knows where and either locks or just exits and so many other things I don't have space (or energy) to write then all down.

I also have a MythTv box on MythBuntu (7.10) that does these little lockups all the time so I know it just isn't one machine. This one is just about to become CentOS or something older in the Ubuntu range.

My desktop machine is not a speed demon by any means - AMD Sempron 2800, I GB Ram, 256Mb nVidia FX5500. However, I expect Ubuntu to outperform Windows on the same hardware. 

All these issue arrived when I upgraded to 7.10 from 7.04 so I decided to do a clean install. No change, actually worse.

I also went off and tried OpenSuse 10.3 but that was just too strange.

I would like to know what my options are? Is there any point in staying with Ubuntu (about my 5th year) or just pulling the plug and going back to the dreaded Windows - I am *that* frustrated. I always imagined that Linux would be runnable on lower spec machines but Ubuntu seems to be heading in the other direction...

Any suggestions would be more than welcome for thsi very frustrated Linux user.

Cheers
Bruce

---

### Post by ghandi69_ on 2008-02-03
I understand your frustration, but hopefully you can understand that you are in the minority, because for a lot of us, 7.10 has been an improvement over 7.04.  Now, given your situation, I would maybe try some of the following..

-> reinstall 7.10.  I do not now know when you upgraded to 7.10, but I do know that I did so immediately when it became available.  It had problems detecting my video card, would have frequent pauses where it would freeze for like 10 seconds, and other problems.  I didn't even mess with it, and the next night I re downloaded the iso and re installed.  I have not had any problems with 7.10 the 2nd time around, and, it has in fact been noticeably faster than 7.04 was for me.

-> Go lightweight with Fluxbox. This option, which would require some research, but can be very satisfying.  If you truly want your machine to run as fast as possible and to be very efficient, that is definitely the way to go.  Again, this would require you to probably do a lot of reading, but a lot of people who go that route never come back. (ps. they also have fluxubuntu available now as well, which would probably take a lot of the learning curve out of the equation.)

-> Go back to XP.  I have been an Ubuntu user for 3 years now, and I went to this option once in the middle of those 3 years for about 2 months.  Depending on what you desires are, this could be a good one.  If you are strictly using your computer for entertainment, such as videogames, web browsing, and so on, this could be for you.  However, if you are a tinkerer in anyway, and consider computing more of a hobby, and want to be in total control of what happens and when it happens, than windows might not be for you.

-> Try another Distro.  There are many Linux distributions available, and as you mentioned you already tried one of them (open suse).  There are many others to try that could suit your needs as well. 

-> This option, which would probably require the most time and effort, but would probably increase your understand of linux and ubuntu the most, would be to identify and fix the problems that are currently slowing your machine down.  While you have probably tried this a little already, the truth is, there is something somewhere that is going wrong and there is probably a way to fix it.  The knowledge required to fix these could very well currently be beyond your linux know how as well as mine, but if you were able to grasps these concepts and correct them, you would be all the better for it.

Again, there are other avenues you could take, but let us know what you decide and we as a community will always be here to help with any of your linux questions.

---

### Post by jaytek13 on 2008-02-03
I'd reiterate that the upgrade process has been known to be problematic for some people and that the best bet would be to back up your files and do a clean install of 7.10 and see how that works out for you.

---

### Post by speedway on 2008-02-03
Thanks Guys

I have actually done 2 clean installs and they were the same. All this only started with 7.10. When I was running 7.04 things ran alot more smoothly. I was going to downgrade to 7.04 again but read somewhere that updates would not be available for it.

I am not a Linux newbie as such. I have been around Linux and Ubuntu for a few years now after getting sick and tired of Windows and it's problems. If others are completely satisfied with 7.10 may I suggest they have far better equipment than I have. My point I suppose is that I am saddened by the fact that Ubuntu now needs almost as much horsepower as a Windows Vista machine!

I'll keep looking for a distro that works, especially a Debian based one. I have grown very accustomed to apt-get.

As I typed this the system went into another little lockup for 10 secs or so. So damn frustrating. :mad:

Cheers
Bruce

---

### Post by markharding557 on 2008-02-03
if 7:10 will not work properly stick with 7:04 given this worked for you 
7:04 will be supported untill oct/09 i think

---

### Post by ghandi69_ on 2008-02-03
> **speedway said:**
> Thanks Guys

 My point I suppose is that I am saddened by the fact that Ubuntu now needs almost as much horsepower as a Windows Vista machine!

As I typed this the system went into another little lockup for 10 secs or so. So damn frustrating. :mad:

Cheers
Bruce

Two things to note.  

One: If you have decided to move on to another Distro, you should let us know which one you choose, I have yet to try another (besides DSL linux on an old pc) and would like to hear about your experience.

Two: The only reason I still think there might be something wrong is because while yes, Ubuntu as time progresses does require more resources, there definitely should not be a noticeable difference from 7.04 to 7.10, and for me, 7.10 runs noticeably faster than 7.04 did.  During those 10 second pauses, check to see if the ksoftirq process is taking up 100% of your CPU.  A friend of mine was experiencing performance issues that sound similar to yours, and he found it was caused by a known bug that could be fixed from either switching to or from the generic kernel.  Hope this helps,

Gandhi

---

### Post by manimal347 on 2008-02-03
Well, if you're tired of putting up with unstable packages and cannot tolerate rolling updates, why not try Debian Etch. You'll need to be familiar with basic CLI system administration, however, and there is no GUI installer, hence why Ubuntu was forked. You may very well prefer the "mothership" of Debian, though, despite its significant attrition of users. Most of your knowledge will remain true, at least if you didn't do most of your work the "click and point" way. 

The only real issue is that Etch is already getting a bit old, and there probably won't be a new "stable" release for at least 18 months. Yes, Debian is quite conservative in its testing. The temptation to use a newer version like Lenny will be strong, but you'll find it probably won't be any more reliable than Gutsy Gibbon.

Also, due to all the things Ubuntu auto-installs, it will always be a pig on slow machines. Seriously, twenty minutes to boot from CD on an Athlon 850 with 256 megabytes of ram. Even when installed on the harddisk, I found it rather pointless. The base install (server install) is okay, though, but there's a lot less support for that route than a Debian base install.

---

### Post by Red Shift on 2008-02-03
Install Ubuntu 7.04 again.  It's supported until October 2008.  You may decide to try Hardy Heron at that time or move to a different distro.

---

