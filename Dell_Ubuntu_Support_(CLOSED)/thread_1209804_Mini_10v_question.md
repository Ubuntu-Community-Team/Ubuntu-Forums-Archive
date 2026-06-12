---
title: "Mini 10v question"
date: 2009-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bri5569 on 2009-07-10
):PI shall be receiving a new Mini _10v_ next week with ubuntu 8.04 installed. My big question is this - Am I better downloading Dells 9.04 iso or just using ubuntu's own for the upgrade. Is Dells' a different spec than the full Ubuntu and are there any benefits of one over the other. Does everything out of the box work with 9.04. Your views on the above would be grately appreciated and respected.

---

### Post by mikewhatever on 2009-07-11
You can either get a 9.04 iso from Dell, or the regular Ubuntu one, or stay with the pre-loaded 8.04 from Dell. It's hard to tell what's better, given all of these versions should work out of the box with the mini 10v. The only major difference Dell's isos provide is the customized interface. [Read more here...]("http://linux.dell.com/wiki/index.php/Ubuntu_9.04") 
Here is a good reveiw:
[http://www.reghardware.co.uk/2009/06/29/review_netbook_dell_inspiron_mini_10v/](http://www.reghardware.co.uk/2009/06/29/review_netbook_dell_inspiron_mini_10v/)

---

### Post by karamu on 2009-07-11
I just ordered a pair of these for me and my wife. I did some digging and the general consensus seems to be that the Dell version of Ubuntu sucks as you can't use the regular Ubuntu repositories thus limiting the packages you can install.

I am certainly intending to put Jaunty on mine when they come. I'm thinking not the NBR but maybe use the Xubuntu desktop to make things run a bit smoother.

---

### Post by Talon2 on 2009-07-11
Here is my opinion based on my owership of a mini 9:

My mini 9 came with 8.04 pre-loaded.  I used it for a while.  There were no big problems but there were several paper cuts.  I won't bore you with the details.  Here is the option that worked best for me:  Ubuntu 9.04 Netbook Remix.

A few details:

- The special Dell interface on 8.04 doesn't do much for me.  Some may like it.  Yes, I'm aware you can change to the standard Ubuntu 8.04 interface... all I'm saying is the Dell interface was not a reason for me to stay with the Dell version.

- The interface on the Netbook Remix I do like.  It was different at first but as I used it I soon found out it has advantages for small systems.  I really like it and use it to this day.  You have to install Netbook Remix to get this interface as far as I know (please correct me if there is a way).

-9.04 Netbook Remix (UNR) is compiled for the Atom processor whereas the normal desktop distros are not.  Performance is rather snappy.

- All hardware works out of the box with UNR.  No paper cuts or tweaking.

- UNR is updated from the regular Ubuntu repositories.  Dell's repositories leave something to be desired.

One thing I would like to see is the ability to save the Dell codecs for later use.  On the other hand, Ubuntu restricted extras does the trick.

Good luck.

---

### Post by superm1 on 2009-07-11
> **karamu said:**
> I just ordered a pair of these for me and my wife. I did some digging and the general consensus seems to be that the Dell version of Ubuntu sucks as you can't use the regular Ubuntu repositories thus limiting the packages you can install.

Propaganda.  There are full mirrors of the Ubuntu repos for main, restricted, universe and multiverse.  Upgrading to later version of Ubuntu is not supported.

> 
I am certainly intending to put Jaunty on mine when they come. I'm thinking not the NBR but maybe use the Xubuntu desktop to make things run a bit smoother.
The mini10v has some gotchas when not using The 8.04 that ships with it:

* Webcam audio
* Touchpad dead zone region on the bottom

---

### Post by superm1 on 2009-07-11
> **Talon2 said:**
> 
- The interface on the Netbook Remix I do like.  It was different at first but as I used it I soon found out it has advantages for small systems.  I really like it and use it to this day.  You have to install Netbook Remix to get this interface as far as I know (please correct me if there is a way).

You should be able to install the appropriate meta packages if you want that UI instead.

> 

-9.04 Netbook Remix (UNR) is compiled for the Atom processor whereas the normal desktop distros are not.  Performance is rather snappy.

No, UNR is i386.

> 

- All hardware works out of the box with UNR.  No paper cuts or tweaking.

With The mini9 yes.  The mini10v still has some gotchas.

> 
- UNR is updated from the regular Ubuntu repositories.  Dell's repositories leave something to be desired.

They're still full repos.  They're just of 8.04 not something more modern.

---

### Post by Talon2 on 2009-07-11
> **superm1 said:**
> Propaganda.  There are full mirrors of the Ubuntu repos for main, restricted, universe and multiverse.  Upgrading to later version of Ubuntu is not supported.


Well, let me see.  In my mind no ability to upgrade to later versions pretty much supports the original statement by karamu. I think he used the word SUCKS.

---

### Post by bri5569 on 2009-07-12
Thanks for all the replies folks. Reading through all the other posts as well, in my opinion its a matter of personal choice. One last question - if i stick with the pre-installed Ubuntu will I still be able to upgrade open office to the lastest version ie 3.1

---

### Post by superm1 on 2009-07-12
> **bri5569 said:**
> Thanks for all the replies folks. Reading through all the other posts as well, in my opinion its a matter of personal choice. One last question - if i stick with the pre-installed Ubuntu will I still be able to upgrade open office to the lastest version ie 3.1
Some people may have set up PPAs for openoffice, you'll have to look around.  The PPAs generally build for all 3 archs (i386, lpia, amd64)

---

### Post by karamu on 2009-07-13
> **Talon2 said:**
> Well, let me see.  In my mind no ability to upgrade to later versions pretty much supports the original statement by karamu. I think he used the word SUCKS.

I haven't received the machines yet so I have no first hand experience but from the research I have done I haven't found too many people happy with the Dell version of Ubuntu and as Talon2 says not being able to upgrade is pretty restrictive. I used 8.04 on my desktop and it was fine but 9.04 just seems a bit better IMHO.

---

### Post by Talon2 on 2009-07-13
> **karamu said:**
> I haven't received the machines yet so I have no first hand experience but from the research I have done I haven't found too many people happy with the Dell version of Ubuntu and as Talon2 says not being able to upgrade is pretty restrictive. I used 8.04 on my desktop and it was fine but 9.04 just seems a bit better IMHO.

A little further info:  I wouldn't be here unless Ubuntu met my needs better than anything else available.  On that note, I would like to see some things handled differently.  IMO, the installation and maintenance of software on the Ubuntu platform as a whole is confusing to the majority of regular users.  Look at the options:

PPA
Add/Remove
apt
Snaptic
Update Manager > Upgrade
deb files

There is no doubt that everything here came about because of good intentions but the current complexity is enough to make a lot of windows users run and hide.

My concern that Dell is not providing upgrades as new versions are released has to do with the fact the I often need the new capabilities that are available in the new releases.  While I'm willing to wait for new os releases, if those releases are not made available then upgrading to a new release of OpenOffice or Firefox or Cheese that has that badly needed new feature leads to really complex and non-standard ways of upgrading individual apps.  It is a hair pulling experience for me and I've been using and coding for computers since before Bill Gates dropped out of college.

I have bought 2 Dell systems with Ubuntu pre-loaded.  I've tried to live with Dell and its lack of updates but Dell's way doesn't work for me.

Cheers.

---

### Post by snowpine on 2009-07-13
Hi Talon2, I feel your frustration :) and let me share my rambling thoughts.

Linux is all about freedom. To me, this freedom means I want to educate myself as much as possible, so that I can set my system up exactly the way I want, with the applications I need for work (and play). 

If I am sitting around wondering if/when Dell is going to push an update through, then I don't have this freedom any more. Therefore, I choose to be proactive and ask myself "what is the best tool for the job?" I replaced the pre-installed "Dellbuntu" 8.04 within 15 minutes of purchasing my Mini. Dell is a great hardware company, but I have chosen not to rely on them for an up-to-date Linux distro--I rely on myself.

To clear up any confusion about the difference between ppa/add-remove/apt/synaptic/etc. here is my understanding of "the installation and maintenance of software on the Ubuntu platform":

1. Synaptic, add/remove programs, aptitude, etc. can be used interchangeably, as they are all just "front ends" for apt.
2. Applications/packages should be installed from the Ubuntu repositories whenever possible. 
3. Upgrading your applications to newer versions happens every six months when you upgrade to a new release.

If you follow those three rules, you'll typically be fine... but if you are adding PPA's or installing .debs that you downloaded from the web, you'd better know what you're doing. Obviously Dell makes rule 3 impossible to follow if you stick with 8.04. ;)

---

### Post by karamu on 2009-07-24
Just received my machines (typing on mine now). Initial impressions- very happy with the hardware- nice little machine indeed. Not so happy with the software. After 20mins of playing with it:
[LIST]
[*]Can't choose server (I am in Japan but it seems like it is using the US server- not very fast)
[*]Repositories DO seem limited- can't install Thunderbird!!
[*]Haven't been able to get Compiz running yet.
[/LIST]
Of course I will investigate further, but initial impressions support my intention of installing regular Jaunty.

---

### Post by karamu on 2009-07-24
> **karamu said:**
> Just received my machines (typing on mine now). Initial impressions- very happy with the hardware- nice little machine indeed. Not so happy with the software. After 20mins of playing with it:
[LIST]
[*]Can't choose server (I am in Japan but it seems like it is using the US server- not very fast)
[*]Repositories DO seem limited- can't install Thunderbird!!
[*]Haven't been able to get Compiz running yet.
[/LIST]
Of course I will investigate further, but initial impressions support my intention of installing regular Jaunty.

Ok, I take that back- Thunderbird is in the repositories- don't know why I couldn't find it yesterday.

---

### Post by jwaclawsky on 2009-07-25
I have a mini9 with 8.04 and recently went to 9.04. I have found the 9.04 to be better. 

BTW, that "maximus" program that Dell ships with 8.04 on the mini 9 is just plain crap. It's buggy and spoils what is a somewhat good working desktop.

---

### Post by karamu on 2009-07-26
> **jwaclawsky said:**
> I have a mini9 with 8.04 and recently went to 9.04. I have found the 9.04 to be better. 

BTW, that "maximus" program that Dell ships with 8.04 on the mini 9 is just plain crap. It's buggy and spoils what is a somewhat good working desktop.

Agreed- it's just been a day or so and it is rally starting to annoy me.

---

### Post by MartynT on 2009-07-26
Hi,

I've had my 10v for 5 days now (just got the wireless working today ](*,) ) and I've been wondering about upgrading to 9.04 UNR .... does everything work (especially the wireless :rolleyes: ) and is Dell's better than the vanilla Ubuntu UNR.

I've found a few things.  The 10v comes with some things that are not available with standard Ubuntu.  These include dell-launcher and their video chat thing, but it also includes the fluedo codecs for gstreamer.  You bought them so you might want to save them before moving 9.04.

There is also a problem with 9.04's microphone / sound recorder.

I want to use my 10v with Skype, so this is a bit of a show stopper for me.  If/when I find solutions to these I'll post back here.

---

### Post by coyote on 2009-11-03
Just bought a Mini10v from the Dell Outlet (refurbished) which came with XP Home. First thing I did was wipe the drive and install Xubuntu 9.10. Everything else is quite snappy and I've only used about 5 Gb on the 16 Gb SATA SSD drive, with Open Office installed. I have a 32 Gb external SSD IDE drive for mass storage and use SD cards for quick stores like we used to do with floppies....before the fall of Rome. With XP on the same drive I had less than 2 Gb after installing Microsoft Office and it ran slow as a 486. I don't like the fact that it comes with 1 Gb of RAM and is a real pain to upgrade. (You basically have to tear the computer down to get to the memory module). However, the Xubuntu install seems to seldom be using more than a couple of hundred Mb of the 993 Mb available according to System Monitor. I also installed without a swap partition and set noatime in fstab to prolong the life of my SSD.

All in all I really like Xubuntu 9.10 and have had no problems doing anything I usually do so far! 

[Update] The webcam mic and touchpad are both working fine now with Karmic!

CB 8)

---

### Post by karamu on 2009-11-30
Glad to hear someone else enjoying their Mini 10v without Windows!! I have been running Ubuntu Karmic for a couple of months now with no  probs and the glitches that seemed to have been present with Jaunty on the 10v are all gone (well, basically the external mic).]

I run the regular Gnome Ubuntu- thought about installing Xubuntu but the performance is fine- I have a 160gig HDD so the footprint is not really an issue for me- I guess Xfce installs smaller.

I read about a Dell Moblin Jaunty remix that is being shipped with the 10v (not sure which country it was though)- hopefully Dell will get their act together and ship a Linux netbook that works properly!

---

### Post by undfined on 2009-12-01
I tried installing UNR 9.10 (Karmic) on my hours old 10v a couple of times through various downloads and USB sticks.  The performance was choppy and slow, no 1366x768 resolution, updates were slow and often failed, and was basically unusable.

The regular i386 9.10 install went fine and after a couple hours google searching my video looks great at the full HD resolution.  My only issue left is I can't get bluetooth to enable.  And I really expected Karmic to run a little smoother - like it does on my Inspiron 1420n and 2 desktops.  I didn't do my research before I bought the computer though, so I'm not complaining.

---

### Post by karamu on 2009-12-06
> **undfined said:**
> I tried installing UNR 9.10 (Karmic) on my hours old 10v a couple of times through various downloads and USB sticks.  The performance was choppy and slow, no 1366x768 resolution, updates were slow and often failed, and was basically unusable.

I have tried Karmic UNR live on a USB stick but didn't like the interface so didn't install it- it seemed to run OK though so I don't know what was wrong on your machine....

> **undfined said:**
> 
The regular i386 9.10 install went fine and after a couple hours google searching my video looks great at the full HD resolution.  My only issue left is I can't get bluetooth to enable.  And I really expected Karmic to run a little smoother - like it does on my Inspiron 1420n and 2 desktops.  I didn't do my research before I bought the computer though, so I'm not complaining.

Bluetooth works fine on my machine "out the box" as it were- I have used it Fedora 12 as well- am currently running Linux Mint 8 which is based on Karmic but there is no need to mess about with Medibuntu to get some applications like Skype and Google Earth. The performance seems good as well. Would recommend it.

---

### Post by trixman on 2009-12-06
can i install programs form the package manager. i use 2 collection programs 

tellico
gnome comic collector


thanks

---

### Post by karamu on 2009-12-07
> **trixman said:**
> can i install programs form the package manager. i use 2 collection programs 

tellico
gnome comic collector



The repositories are the regular Ubuntu ones- I just checked and Tellico is there but not the comic collector. I guess you can install it via the internet- I'm not familiar with that particular program, sorry.

---

