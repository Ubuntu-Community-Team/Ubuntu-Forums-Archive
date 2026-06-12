---
title: "Upgrade from Dell Ubuntu 8.04+"
date: 2011-02-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drjoewebb on 2011-02-12
I have a Dell Mini 12, and would like to upgrade my 8.04+ so that I can get some of the newer software applications, and get the benefits of the various improvements in Ubuntu.

I know that Dell has a special video driver and has also bundled various codecs for media from Fluendo. I have read on some of the postings in the forum how to back up the codecs and reload them, but my impression is that getting the video working is almost impossible without the Dell-written driver.

I have searched all through the forums and product areas on Dell's site, and can't find anything about updating or buying a new Dell Ubuntu system disk for my Mini.

Any and all suggestions would be appreciated, including links to forum posts that might be of assistance.

---

### Post by snowpine on 2011-02-12
Your Dell Mini 12 has Intel GMA500 "Poulsbo" graphics, which means you'll have to be very careful which Linux distribution you choose. Here is some reading material to educate yourself on the topic:

[http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux](http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux)
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

Whichever option you choose, you'll need to back up all your data and do a fresh reinstall--there is no upgrade path from the custom "Dell Ubuntu" 8.04. Good luck! :)

---

### Post by drjoewebb on 2011-02-13
Thanks very much; it seems to confirm that updating is a real problem if you don't know what you're really doing. While I'm pretty good at much of basic Linux computing, when it comes to hardware setup, I do have problems.

Perhaps there is another approach. What if I did a clean install of 8.04+, updated as far as the repositories would take me, and then started to upgrade the software I needed, such as getting to OOo 3.3 instead of the packaged 2.4, latest Firefox, etc. In light of my hardware setup concerns and capabilities, would I be better off doing that knowing that the video driver would be in its intended state? Are there any specific repositories I should add to do so?

---

### Post by snowpine on 2011-02-13
You're welcome! :)

I don't recommend the "install 8.04 and update individual applications" approach, for two reasons:

1. The 8.04 release reaches its "end of life" in April 2011 and will be completely unsupported after that date.

2. The custom "Dellbuntu" that came preinstalled on the Dell Mini series was based on the rare and obsolete "lpia" (Low Power Intel Architecture) rather than the more common i386 architecture. It is unlikely you will find 3rd party applications or repositories compiled for lpia, so you'll have to jump through hoops to repackage i386 to lpia as described here: [http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835)

My Dell Mini 9 came with "Dellbuntu" 8.04 preinstalled, but to be honest with you, I replaced it with "regular" Ubuntu the same day I bought it. Unfortunately my Mini 9 has a different graphics card than your Mini 12, so I can't talk you through the specifics of GMA500-in-Linux. Hopefully the links in my previous post will help you find the information you need, good luck! :)

ps Updating Ubuntu is usually incredibly easy (click one button and type your password) but unfortunately Dell really dropped the ball with the Mini series. They had a real chance to push netbooks-with-Ubuntu into the mainstream but chose to use hardware with terrible Linux support and to use a crippled OEM Ubuntu rather than the real deal. I'm very happy with my Mini 9, but I got it just the way I like with no help or support from Dell, just friendly forum members like you and me. :)

---

### Post by drjoewebb on 2011-02-13
Thanks again very much. I don't use my Dell Mini12 that often, but when I do I've always been impressed by it, which made me wonder why "Dellbuntu" was so odd. I have called for tech support on some occasions, and they would always advise against changes to the system -- making it seem like it was a house of cards.... and it turns out that it was.

At least I know I can always do a full install from the factory CD. And I know one fallback is to use that "other" operating system from the Seattle area if I really had to.

I really appreciate your help and getting the whole issue in perspective.

Based on the links you had sent earlier, I assume that the "best" chance I have is with 9.10 for the hardware support, and then I just take it from there with all of the settings recommendations in the other posts. Am I interpreting that correctly?

---

### Post by snowpine on 2011-02-13
The problem with 9.10 is that is support also ends in April.

[Post #1 in this thread]("http://ubuntuforums.org/showthread.php?t=1229345") seems to have instructions for the current 10.10 release. I can't vouch for them personally but as you say, you can always revert to factory settings using the restore CD. :)

---

### Post by drjoewebb on 2011-02-14
Well, here's a different solution I was not expecting. I use PCLinuxOS on my desktop, and I loaded the latest edition onto my Dell Mini 12, and it detected everything without a problem, and without going through any hoops. My video resolution was detected automatically.

I had posted on the PCLinuxOS forum asking if anyone had success loading it, and got no response, which was unusual. But someone suggested that I just use the Live CD and see what happens, and success doing that was the reason that I continued to a full installation.

Thank you for your help, though. Your thorough and clear answers helped me get to this solution. Sorry to disappoint you that it was not an Ubuntu solution!

---

### Post by snowpine on 2011-02-14
Yay, that's great news! 

Don't worry about hurting my feelings by switching to another distro... I don't use Ubuntu on my Mini 9 any more either. :)

---

