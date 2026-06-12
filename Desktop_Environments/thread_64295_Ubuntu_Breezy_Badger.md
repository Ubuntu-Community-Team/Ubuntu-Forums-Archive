---
title: "Ubuntu Breezy Badger"
date: 2005-09-10
forum: Desktop Environments
---

### Post by kamiccolo on 2005-09-10
Hi!

Like all others of you I'm looking forward to the final release of Ubuntu 5.10 and I also want to install it. But I have some questions:

1. What will be better, updating from Hoary to Breezy or setting up a completely new system? I heard about other distros that updates aren't such good as a completely new system.

2. What will be changed in Breezy? Is for example the new Gnome 2.12 integrated? What other changes will be there?

Does anyone know something about?

---

### Post by XDevHald on 2005-09-10
Well, for one, I would not recommend doing a dist-upgrade, reasong being is breezy will override hoarys applications and will get confused on what version it's really suppose to run for that application. It also bugs your repos and makes things a little buggy.

It's best if you do a fresh install and save yourself some time and the hassel :)

Now for number two, you can read up on the changes of breezy and gnome 2.12 righ tin the link provided below.

[http://www.ubuntuforums.org/showthread.php?t=63684](http://www.ubuntuforums.org/showthread.php?t=63684)

Good Luck!

---

### Post by kamiccolo on 2005-09-10
Well, the changes in Breezy are really cool. But when it's released I have to backup my files. It's good that I have a second hard drive. If only I would know how I can mount it, but I have enough time to learn.  :) 
Now I'm really looking forward to the release.

---

### Post by David Marrs on 2005-09-10
[QUOTE=Steve Myers]Well, for one, I would not recommend doing a dist-upgrade, reasong being is breezy will override hoarys applications and will get confused on what version it's really suppose to run for that application. It also bugs your repos and makes things a little buggy.[/QUOTE]
That's a shame. But why does it override? Shouldn't it just upgrade the packages? I thought that the whole point of a dist-upgrade was that it kept a check on everything that gets upgraded so that compatibility remains.

---

### Post by kamiccolo on 2005-09-11
A good question.

And there's another problem:
I downloaded the preview release yesterday and I wanted to install it on a second hard drive, only for testing. But in the installation routine it isn't able to copy the rest of the packages on the drive. The drive has 8,5 GB, so it actually has to be enough space. I tried different methods to make the partitions, automaticly and manually, but Ubuntu always says that there isn't enough space in /var. That's impossible. /dev/hda1 (ext3) has 8,0 of 8,5 GB, that has to be enough for only about 400 MB packages.
Colony 4 of Breezy didn't have this problem. Hoary works correctly too.
So what can I do?

---

### Post by Keffin on 2005-09-11
[QUOTE=kamiccolo].....So what can I do?[/QUOTE]

The first thing to do on strange errors is to check the MD5Sum of the ISO you burned. To do this go to a terminal and type md5sum /path/to/iso.iso. It should match with the number next to the iso you downloaded at this link [http://se.releases.ubuntu.com/5.10/MD5SUMS](http://se.releases.ubuntu.com/5.10/MD5SUMS). It is also possible that the CD burn went wrong. K3b has an option you set before burning to verify written data, such an option is probably available in everything else too.

After discounting the above, I really have no idea. Is there anything "unusual" with your hard drive setup (RAID, really new/old drive) that would hide this problem from most people?

---

### Post by angkor on 2005-09-11
[QUOTE=Steve Myers]Well, for one, I would not recommend doing a dist-upgrade, reasong being is breezy will override hoarys applications and will get confused on what version it's really suppose to run for that application. It also bugs your repos and makes things a little buggy.

It's best if you do a fresh install and save yourself some time and the hassel :)[/QUOTE]

What do you mean by 'overriding' Hoary's applications? If an application is upgraded you won't have two versions of an app on your comp.

The advantage of upgrading is that you'll keep all your settings and configs. I'd recommend doing a dist-upgrade....cause if that doesn't work properly you could always do a fresh install of Breezy.

I just did an upgrade from Hoary to Breezy on my test laptop and it worked flawlessly except for some things in Breezy being broken right now, but all that will be fixed when it's released.

---

### Post by spencer on 2005-09-12
I too used 'dist-upgrade' and so far everything seems intact. It actually feels smoother and more responsive to me. I've even had the automatic updates notify me of updates already and I have had no problems from what I can see.

Oh, I just remembered there were a few changes that were made made to my default sound application when I opened up sound files. opening sound files changed to another sound app that I don't remeber now. I had to reinstall xine-ui and mplayer but nothing drastic. Firefox was even updated since I upgraded to Breezy Badger.

Ubuntu runs great on this old gateway. 

Many Thanks to the ubuntu minds. Looking forward to the next stage.  :) 

-spencer

---

### Post by psychicdragon on 2005-09-12
There's no reason not to dist-upgrade. I think some people like to reinstall when they upgrade primarily to get rid of the crap that accumulates on their system after a while (unused applications and libraries). It's totally unnecessary, you can just remove them through synaptic in less time.

I'm running Breezy right now. The upgrade went smoothly with absolutley no breakage.

---

### Post by Zodiac on 2005-09-12
[QUOTE=psychicdragon]There's no reason not to dist-upgrade. I think some people like to reinstall when they upgrade primarily to get rid of the crap that accumulates on their system after a while (unused applications and libraries). It's totally unnecessary, you can just remove them through synaptic in less time.

I'm running Breezy right now. The upgrade went smoothly with absolutley no breakage.[/QUOTE]
 What is the dist upgrade command? Do you have to update the synaptic package locations first? 

I am so doin this... I am antsy for Breezy!!

---

### Post by Tiede on 2005-09-12
If you really want to update right now, you can try [ following this howto ](http://ubuntuguide.org/#upgradingubuntu)
What I do to change all the hoary to breezy in gedit is do a 'find and replace'. Quicker and more efficent ;)

Ok, this is just a bit out of the main theme here but this question has been bugging me a lot, and the ramifications fall back to here...
Isn't Breezy Badger supposed to *ALWAYS* stay experimental with the name of the new releases replacing it at the end... Because I have been thinking, if that is the case, when we upgrade from Hoary to breezy, all we do is get the experimental release (wich will ** always** be buggy) and after October, when someone tries to do a simple apt-get upgrade he will end-up with the next set of developpement softwares out there...
Were my sources mistaking, or am I right when I think this?

---

### Post by dahli.llama on 2005-09-12
Will doing an upgrade change my kernel?  I assume so, but I just want to be sure.

The hardest thing I've had to do with Ubuntu was getting my wireless card configured and if the kernel is going to change then I'll need to do it again and it would be nice to know beforehand.

---

### Post by mr_ed on 2005-09-12
[QUOTE=Tiede]Isn't Breezy Badger supposed to *ALWAYS* stay experimental with the name of the new releases replacing it at the end...[/QUOTE]

Nope.  :)

Breezy is the name of the next release.  The unstable branch will change to something else (hey, what happened to Grumpy?) :)
Previous to this version, Hoary was the unstable branch, and Warty was the stable one.

I think you're confusing it with Debian.  Sid will always be Debian unstable (since Sid is the kid that breaks all the toys).  Once Sarge was released, they renamed testing to Etch, and left Sid as is.

---

### Post by mr_ed on 2005-09-12
[QUOTE=dahli.llama]Will doing an upgrade change my kernel?  I assume so, but I just want to be sure.[/QUOTE]

Yes, it will.

> The hardest thing I've had to do with Ubuntu was getting my wireless card configured and if the kernel is going to change then I'll need to do it again and it would be nice to know beforehand.

Your old kernel will remain on your system (until you remove it).

I just upgraded to Breezy with no problems.  Were you using ndiswrapper?
That's the only place where you may get shot in the foot, since the version of ndiswrapper changed, too.

---

### Post by olddog55 on 2005-09-12
> What is the dist upgrade command? 
>Do you have to update the synaptic package locations first?
>I am so doin this... I am antsy for Breezy!!

via Comand Line:   From a 'Root Terminal'
1.  edit the /etc/apt/sources.list to add:
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe
  [ And yes, I left off the 'sources' lines...  Intentionally.  I am assuming no custom compile packages. ]
2.  execute an "apt-get update"
3.  execute an "apt-get dist-upgrade"
then stand back and watch the upgrade...

or via Synaptic Package Manager:
1.  -> Settings -> Repositories -> Add -> Custom  and add the following 3 lines:
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe
2. 'OK' out of Settings and force a -> Reload
3. -> Mark All Upgrades -> Smart Update
  [ Let it churn for a while.  When done, it says 'No Package is Selected, but if you go to "Installed (upgradeable)" you will see a whole bunch (hundreds) of packages pending. ]
4. Click on -> Apply
5. Look through the Summary (-> Show Details), if all OK, click on -> Apply
6. Synaptic/Apt will begin downloading the ~521Mb of files and you're on your way to Breezy Badger.   :cool: 

Good Luck!    :grin: 

/d

---

### Post by dahli.llama on 2005-09-12
[QUOTE=mr_ed]
I just upgraded to Breezy with no problems.  Were you using ndiswrapper?
That's the only place where you may get shot in the foot, since the version of ndiswrapper changed, too.[/QUOTE]

Yeah ndiswrapper.

It works great for me and my D-Link wireless card, so I'm happy.  It's not too difficult I've found, but it's time consuming and sometimes takes a few kicks to get it working correctly.

---

### Post by Tiede on 2005-09-13
[QUOTE=mr_ed]Nope.  :)

Breezy is the name of the next release.  The unstable branch will change to something else (hey, what happened to Grumpy?) :)
Previous to this version, Hoary was the unstable branch, and Warty was the stable one.

I think you're confusing it with Debian.  Sid will always be Debian unstable (since Sid is the kid that breaks all the toys).  Once Sarge was released, they renamed testing to Etch, and left Sid as is.[/QUOTE]
 I think you are right mr ed. I must have been confusing it with Sid...(That's one of the factors that contributed to the breaking of my old (1994) laptop :D )

---

