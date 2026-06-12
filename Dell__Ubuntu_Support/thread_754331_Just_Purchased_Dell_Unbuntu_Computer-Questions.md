---
title: "Just Purchased Dell Unbuntu Computer-Questions"
date: 2008-04-13
forum: Dell  Ubuntu Support
---

### Post by WBL on 2008-04-13
Hi.  Sorry for all the questions, but I haven't used Ubuntu in quite a while, and just purchased a Dell Ubuntu computer (should arrive in early May).  I bought the Inspiron 1525n (with extra memory).  I basically have 5 questions (sorry for the list :().

1.  By the time my computer arrives, Ubuntu 8.04 will be out.  But Dell is installing 7.10.  Will it be easy to upgrade to 8.04?

2.  Do I need to do anything upon receiving the computer?  Should I download anything (such as the LiveCD or drivers or anything)?

3.  Do I need to change my sources.list to get access to all software, including non-free software?  Would somebody with a similar setup to mine (Inspiron 1525n) mind giving me a sources.list?

4. Will Compiz run at all on the computer I just purchased?

5.  I've been reading these forums and there's lots of talk about hibernation/suspend issues.  Will I be affected, and what should I do?

 Thanks a whole lot in advance for any answers to any of these questions.  I'll bookmark this thread so I'll have it handy when my computer arrives.  :)

-WBL

---

### Post by fragos on 2008-04-13
> **WBL said:**
> Hi.  Sorry for all the questions, but I haven't used Ubuntu in quite a while, and just purchased a Dell Ubuntu computer (should arrive in early May).  I bought the Inspiron 1525n (with extra memory).  I basically have 5 questions (sorry for the list :().

1.  By the time my computer arrives, Ubuntu 8.04 will be out.  But Dell is installing 7.10.  Will it be easy to upgrade to 8.04?

2.  Do I need to do anything upon receiving the computer?  Should I download anything (such as the LiveCD or drivers or anything)?

3.  Do I need to change my sources.list to get access to all software, including non-free software?  Would somebody with a similar setup to mine (Inspiron 1525n) mind giving me a sources.list?

4. Will Compiz run at all on the computer I just purchased?

5.  I've been reading these forums and there's lots of talk about hibernation/suspend issues.  Will I be affected, and what should I do?

 Thanks a whole lot in advance for any answers to any of these questions.  I'll bookmark this thread so I'll have it handy when my computer arrives.  :)

-WBL

1. An 8.04 iso will be available for free download when Dell creates it. It will be DVD size and burnable as a Live CD but on a DVD.

2. don't need to download anything to get started. The laptop will self install when you power it up -- my 1420n did.

3. Click System-> Administration-> Software Sources. You'll want to make sure universe, restricted and multiverse are checked.

4. With the 1420n COMPIZ only directly worked with Nvidia video. It may be different with 8.04 and the Intel video will also work. There is a workaround if you want it.

5. The answer is to shutdown rather than hibernate. You can tell the system to restart with the same aps running even when you shutdown. I've heard the issue was solved in 8.04.

---

### Post by WBL on 2008-04-13
Thank you so much fragos-that really helped.  You're awesome.  :)

I'll make sure to download Dell's 8.04  iso and burn it to a DVD.  Do I just put the DVD in and it will upgrade?

Is the "workaround" for Compiz very complicated?  What all is involved with this "workaround?"

Thanks again.

-WBL

---

### Post by fragos on 2008-04-13
Here's the work around -- all instructions included:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

I haven't tried this myself but by all accounts it works and is easily undoable if it doesn't.

The DVD is what's called a "Live CD." All you need to do is to place the DVD in your drive and boot up the machine. It will boot onto the DVD and give you an option to install. A couple of simple questions and that's all there is to it. Note that your disk will be overwritten and all data will be lost unless you'd saved it to restore after the install.

---

### Post by LeoSolaris on 2008-04-13
Another note that when 8.04 is officially released, you should be able to do an upgrade totally from within Ubuntu with the update manager. (It will let you know that there is a new distribution out and ask if you wish to upgrade.)

Best of luck with the pre-installed Ubuntu unit. I didn't know about them when I got my Dell 1520 back in Dec, otherwise I would have looked at them.

Leo

---

### Post by WBL on 2008-04-13
> **LeoSolaris said:**
> Another note that when 8.04 is officially released, you should be able to do an upgrade totally from within Ubuntu with the update manager. (It will let you know that there is a new distribution out and ask if you wish to upgrade.)

Leo

> **fragos said:**
> Here's the work around -- all instructions included:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

So I don't even need to download and use a DVD to upgrade?  That 's great information...thanks LeoSolaris!  Is the (non-DVD) upgrade easy?        

And thanks for the link, fragos!     

You guys were very helpful, and I appreciate it.  :)

-WBL

---

### Post by notwen on 2008-04-14
> 
1. By the time my computer arrives, Ubuntu 8.04 will be out. But Dell is installing 7.10. Will it be easy to upgrade to 8.04?

2. Do I need to do anything upon receiving the computer? Should I download anything (such as the LiveCD or drivers or anything)?

3. Do I need to change my sources.list to get access to all software, including non-free software? Would somebody with a similar setup to mine (Inspiron 1525n) mind giving me a sources.list?

4. Will Compiz run at all on the computer I just purchased?

5. I've been reading these forums and there's lots of talk about hibernation/suspend issues. Will I be affected, and what should I do?


First off, congratulations on your purchase.  I personally own a Inspiron 1420n and am a very happy w/ my experiences in the past 8 months or so.   

1.  I've seen mixed reviews about upgrading from Feisty to Gutsy on the N series models, some upgrades went flawless while some others had issues.  I personally had issues w/ upgrading my existing install.  I however corrected this issue by d/l and installing the custom Ubuntu images provided by Dell [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO").  I recommend you backup your data and use the custom image released by Dell, it is released a month or so after Ubuntu's official release and it will implement all the bugs/fixes that have been discovered in the new version(Hardy Heron) on their supported systems.  This is just my opinion.  =]

2. This depends, they have added DVD playback to the Gutsy machines, this was not the case back when they first started offering these pre-installed systems.  Depending on if you want mp3 playback and some other proprietary codecs needed to play certain things(ie. flash on the web) you'll need to install some additional packages to enable playback.  The majority of these will be installed if you add the Medibuntu repository(read below about repos).  See more info [here]("https://help.ubuntu.com/community/Medibuntu") about it and how to set it up on your system.

3.  Your default sources.list should suit you fine unless you find something you want/need in other repos.  Have a look [here]("https://help.ubuntu.com/community/Repositories/Ubuntu") to understand what the different repos are and how to enable/disable them as you see fit.  [Here]("http://www.ubuntu.com/community/ubuntustory/components") is additional info on each of Ubuntu's offered repos and what packages each contain.  Keep in mind anyone can host a repo and you should be wary when adding a repo from a un-trusted source.

4. My Inspiron 1420n has the same Intel X3100 chipset offered in the Inspiron 1525n and I run Compiz-Fusion daily.  Compiz-Fusion blacklists this chipset in Gutsy, but I've read some posts and articles about it working w/o any issue in Hardy Heron.  Once Dell releases their custom Ubuntu image I will be sure to check it out and see if it resolves this issue.  To bypass the hardware check and enable Compiz-Fusion on your machine just follow the [link]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility") fragos posted earlier.  This will likely introduce some issues concerning video playback, but this can be fixed as well by changing your video output settings to 'No Xv' in whichever video player you prefer.  I use VLC and can verify it works on my machine and someone [here]("https://bugs.launchpad.net/dell/+bug/141298") claims it works while using gstreamer.

5. This is another hit or miss area in my opinion.  I had suspend to ram working for me w/ Feisty, but once I upgraded to Gutsy I have yet to be able to get either to work correctly.  Although some people claim to have no issues at all.  Granted I could probably figure this out if I took the time, but I leave my laptop on 24/7 and won't need either function anytime soon.  You can refer to [this thread]("http://ubuntuforums.org/showthread.php?t=579781") to see different laptop users experiences and tweaks on hibernate/suspend, it may even have a couple of 1525n users that you can read over.  

Again, congratz on your new Dell-Ubuntu machine and be sure to share your experience here on the forums, as others can learn a lot from every small thing you did to get your machine working the way you need it to work.  Be sure to post if you run into any issues along the way.  Good luck w/ your new machine, hope yours works out as well for you as mine has for me.  =]

---EDIT---
Please take a look for more useful info here on [this]("http://ubuntuforums.org/showthread.php?t=750250") thread such as direct links and even Dell's Linux support number.

---

### Post by OhioLen on 2008-04-14
I have the exact model laptop (Inspiron 1525n), and it works great with Gutsy. However, the hibernate feature is hit-or-miss, from what I can see. Sometimes it works the way it ought to, other times it has to be completely powered down and then brought back up. Of course, it didn't always work perfectly in Windows either. :rolleyes: Suspend and Shutdown are the best bets.

The only problem I've encountered so far is probably not much of one: Dell ships the machine with a system restore ISO file in the /home directory (ubuntu-dell-reinstall.iso), but the thing is too big (5GB) for a standard DVD (4.7GB). I don't suppose it really matters because there's no Dell-specific software on the machine and there's a new version coming out soon. The only thing I worry about is if I have to deal with proprietary drivers during a crash-reinstall or distro upgrade.

---

### Post by fragos on 2008-04-14
> **OhioLen said:**
> I have the exact model laptop (Inspiron 1525n), and it works great with Gutsy. However, the hibernate feature is hit-or-miss, from what I can see. Sometimes it works the way it ought to, other times it has to be completely powered down and then brought back up. Of course, it didn't always work perfectly in Windows either. :rolleyes: Suspend and Shutdown are the best bets.

The only problem I've encountered so far is probably not much of one: Dell ships the machine with a system restore ISO file in the /home directory (ubuntu-dell-reinstall.iso), but the thing is too big (5GB) for a standard DVD (4.7GB). I don't suppose it really matters because there's no Dell-specific software on the machine and there's a new version coming out soon. The only thing I worry about is if I have to deal with proprietary drivers during a crash-reinstall or distro upgrade.

With my 1420n that partition could be used to reinstall directly.

---

### Post by OhioLen on 2008-04-14
No, I don't mean the restore *partition*. That's the FAT32 at the front of the drive. I'm talking about the *ISO* they apparently made of that partition and stored in /home. Like I said, not much of a big deal, it just prompted a WTF moment when I realized I couldn't burn the thing. I would like to have a copy of it somewhere off the HDD in case of hardware failure.

---

### Post by fragos on 2008-04-14
I understand that you can mount an ISO and acomplish the same thing as booting a Live CD. I've not personaly used that method. Try a search on "mount iso".

---

### Post by notwen on 2008-04-15
> **OhioLen said:**
> No, I don't mean the restore *partition*. That's the FAT32 at the front of the drive. I'm talking about the *ISO* they apparently made of that partition and stored in /home. Like I said, not much of a big deal, it just prompted a WTF moment when I realized I couldn't burn the thing. I would like to have a copy of it somewhere off the HDD in case of hardware failure.

Dell has recently added this restore iso on your desktop/home folder for 'convenience'.  I would just delete it and keep a copy of the latest custom Dell Ubuntu image released for your specific machine.  I myself would also recommend having this image on-hand before you attempt a normal distro upgrade through synaptic in case things don't work correctly once the upgrade has finished.  I have not had any luck w/ a normal upgrade from Feisty to Gutsy w/ my Inspiron 1420n, although the fresh install got everything working accordingly.  Maybe you could ask Dell why they made a restore too big to fit onto a standard 4.7 GB DVDR.

---

