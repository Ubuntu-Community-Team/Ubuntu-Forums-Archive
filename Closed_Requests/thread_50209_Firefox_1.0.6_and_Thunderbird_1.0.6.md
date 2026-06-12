---
title: "Firefox 1.0.6 and Thunderbird 1.0.6"
date: 2005-07-19
forum: Closed Requests
---

### Post by redlabour on 2005-07-19
They arrive this Week - hopefully in Ubuntu too ! ;)

---

### Post by dave9191 on 2005-07-19
From what I understand the versioning policy with ubuntu is that hoary will stay with firefox 1.0.2 and only have security patches applied. I think breezy is being shipped with 1.0.4. You'll probably be able to get a newer version from the backport repositories, or install it yourself. the firefox shipped with ubunutu is optimised for gnome and ubuntu. 

Dave

---

### Post by Kyral on 2005-07-20
The Firefox currently in Backports is 1.0.2 with the security patches so its basically 1.0.4...I guess a packaging bug or something. But yah, I seriously don't see why we cannot bring 1.0.6 into Backports....heck if I knew how to I would do it myself..

---

### Post by redlabour on 2005-07-20
[QUOTE=Kyral]The Firefox currently in Backports is 1.0.2 with the security patches so its basically 1.0.4...I guess a packaging bug or something. But yah, I seriously don't see why we cannot bring 1.0.6 into Backports....heck if I knew how to I would do it myself..[/QUOTE]
 The funny thing about is that even Mozilla means that this is a Bug by Ubuntu and they asked the Ubuntu Developer Team to correct the Versionnumber. You can see it on the Updatesite by Mozilla.org when you go there via Firefox from Ubuntu. :D

[http://www.mozilla.org/products/firefox/upgrade/](http://www.mozilla.org/products/firefox/upgrade/)
> You appear to be using the Firefox package provided by Ubuntu Linux. Ubuntu distributed a new version of Firefox which contains the security fixes from 1.0.6 but ... etc. 


---

### Post by dave9191 on 2005-07-20
you can always install firefox from the mozzila site yourself if you like :)

Dave

---

### Post by SpEcIeS on 2005-07-20
Even though I am an upgrade fan, 1.0.4 is running really nice, so is it really necessary to update? What are the security issues, if someone knows off the top of their head?

Perhaps it would be best to wait for the Ubuntu group to deal with this one. Mozilla's installation does not seem to comply with synaptic. Ubuntu has firefox spread about where Mozilla is a straight install.

Like one of the examples given, it may be a good idea to install into home, just to give it a try. :)

---

### Post by dave9191 on 2005-07-20
Well whenever i install software like firefox myself i always dump it into the /opt dir. Synaptic never puts anything there, so i know its all my stuff. Like java, eclipse, firefox ;)

Dave

---

### Post by SpEcIeS on 2005-07-20
[QUOTE=dave9191]Well whenever i install software like firefox myself i always dump it into the /opt dir. Synaptic never puts anything there, so i know its all my stuff. Like java, eclipse, firefox ;)

Dave[/QUOTE]
That is a great idea. Personally I started that one with OpenOffice 1.9 Beta and LimeWire. :)

_Update:_
Just applied the latest 1.0.6 firefox, and I utilized the /opt option. It works really well.

---

### Post by DiGiTaLFX on 2005-07-20
Sorry but I'm a bit new. Why doesn't the new ff get put straight into the repositories. Also (kinda related) how come things such as gaim are out dated too?

---

### Post by SpEcIeS on 2005-07-20
[QUOTE=DiGiTaLFX]Sorry but I'm a bit new. Why doesn't the new ff get put straight into the repositories. Also (kinda related) how come things such as gaim are out dated too?[/QUOTE]
This issue is version relevent. Every six months Ubuntu distributes a new version; next is breezy. :) For the impatient, like me, compile + install, create deb's + install, and install packages, like firefox. :)

In my opinion **configure --prefix=/usr ; make ; make install** is the easiest, or **checkinstall** for deb build. :)

---

### Post by darkaudit on 2005-07-20
Why would Breezy stick with 1.0.4  when it's still three months from release?

---

### Post by TravisNewman on 2005-07-20
No, breezy will have a new version, perhaps even newer than 1.0.6, it's just a matter of waiting for it.

---

### Post by jdong on 2005-07-20
Alright, both of these are valid and accepted requests. We just need to wait for Breezy to get these, then I'll backport them for Hoary.

---

### Post by loon on 2005-07-20
I have a hard time coming in terms wih this.

1.0.2 with all the security updates.... doesn't that equal 1.0.6?

This is Ubuntu, linux for human begins, and something for the non-linux friendly user to finally be brought over. This will cause problems with a new Ubuntu user (family, friends, teachers, business) who doesnt know about the forums and such.  Because when they go see the about page and FF says 1.0.2 and FF web site say the developers need to change stuff, this is going to cause second thoughts with these people.  Esp when they go to install their favorite themes and extentions and they can't.  I know Ubuntu is a type of Debian and follows the backporting, etc... but lets put a little innovation into it shall we?

(this is no way a rant or having a rude tone.)

---

### Post by jdong on 2005-07-20
Please, don't bring up all this Ubuntu ciriticism to me... I'm in no way responsible for it; I'm doing my part to correct the wrong. We're almost ready to merge with Ubuntu, for an official hoary-backports/breezy-backports repo on archive.ubuntu.com, so chances are that you'll see commented out sources.list lines for breezy-backports, much like Universe, when Breezy comes out :)


As far as 1.0.2+security updates, it makes less sense for Firefox than it does for bigger things, like GNOME or KDE, where from 2.10 to 2.10.1 would encompass much more than just security or bugfixes (new features, ABI changes, etc etc etc are all possible), and introducing this would complicate developing applications for the Ubuntu platform. Even distros like Fedora, RHEL, SuSE which provide newer versions of some packages only do so for the end-user stuff that has little effect on the overall system, such as Firefox or GAIM (and many times rarely GAIM due to compatibility with plugins)

---

### Post by manicka on 2005-07-20
I noticed that breezy now has 1.0.5. Will this be backported or will it be better to wait for 1.0.6? 
I'm happy to wait :)

---

### Post by jdong on 2005-07-20
[QUOTE=manicka]I noticed that breezy now has 1.0.5. Will this be backported or will it be better to wait for 1.0.6? 
I'm happy to wait :)[/QUOTE]
1.0.5 breaks some Firefox plugins. I'd rather wait for it to be safe :)

---

### Post by fishfork on 2005-07-20
I went ahead and got Firefox 1.0.6 from mozilla.org - you get a nice install wizard, just like the windows version. Just make sure you install it somewhere sensible like /opt.

Interestingly, I found it to be *much* quicker to load pages than the standard ubuntu version, which would really struggle on my old K6. The difference was like night and day. I wonder why - maybe because of gcc 4.0? Hopefully the forthcoming backports version will be just as fast!

---

### Post by SpEcIeS on 2005-07-20
I have also found that 1.0.6 works a little quicker, however some extensions do not work. When first installed the majority of the extensions worked, but after accidently running 1.0.4, the working ones were "confused". Nothing that a little reinstallation of these extensions did not fix. :)

Other than that, I am looking forward to the backports being available, and I believe that the backport project will be a wonderful addition to Ubuntu.  ;-)

---

### Post by Majlo on 2005-07-21
Hi ..
Firefox 1.0.6 is in Breezy 

[http://lists.ubuntu.com/archives/breezy-changes/2005-July/008100.html](http://lists.ubuntu.com/archives/breezy-changes/2005-July/008100.html)

---

### Post by manicka on 2005-07-21
[QUOTE=jdong]1.0.5 breaks some Firefox plugins. I'd rather wait for it to be safe :)[/QUOTE]
 OK Great!

---

### Post by traherom on 2005-07-21
Just curious... how can I remove the current FF from my system before checkinstalling 1.0.6? If you do it the normal way through Synaptic, it wants to remove a whole bunch dependencies...

--EDIT--
 ](*,)  Why do ubuntu packages get special verson numbers!!! Firefox doesn't recognize the repository version. I hate getting things from the site. :rolleyes:

---

### Post by ArBaDaCarBa on 2005-07-21
And what about the locales ?

---

### Post by DiGiTaLFX on 2005-07-21
OK I'm kinda understanding this a bit more now. One thing I've noticed is that the 1.0.4 package is actually identifyable as ubuntu5.**4** which is helpful. Anyway I'm just wondering, seeing as breezy sounds like it gets updates quite quicky, would it be a good idea to try and run this instead of hoary (as I like to keep things uptodate)?
Cheers
DiGiTaLFX

---

### Post by Omnios on 2005-07-21
Hi I think one of the driving forces behind having the latest browser goes beyond having something new and shiney though that is a factor. I find there a lot of multimedia sites where I can not access certain media because I have an aged version of a browser this isn't always a problem but if one of someone's main visited sites have this problem it becomes a very serios issue for them. 

 Cheers

---

### Post by Kyral on 2005-07-21
I'm building the Firefox 1.0.6 package right now. I'll post it up once I try it on my system.

(I hope I don't get in trouble for this one...)

---

### Post by jdong on 2005-07-21
I'll build & upload 1.0.6 packages built from 1.0.5 Ubuntu diffs...

---

### Post by Seth on 2005-07-21
[QUOTE=jdong]I'll build & upload 1.0.6 packages built from 1.0.5 Ubuntu diffs...[/QUOTE]
 1.06 is in Breezy now.

---

### Post by jdong on 2005-07-21
Thanks, building :)

---

### Post by jdong on 2005-07-21
BTW, that was my 3000th post ;)

---

### Post by dave9191 on 2005-07-21
[QUOTE=jdong]BTW, that was my 3000th post ;)[/QUOTE]

Let me be the first to congratulate you :) 

*Caugh*Spammer*Caugh*

J/K ;)

Dave

---

### Post by jdong on 2005-07-21
FF1.0.6 built and uploaded

Thunderbird is not in Breezy. Bring it back up when it's there

---

### Post by jesse on 2005-07-21
You can always install firefox 1.0.6 from the debian unstable repository. It works. I'm using it.

---

### Post by aerials on 2005-07-21
[QUOTE=jdong]FF1.0.6 built and uploaded[/QUOTE]

I can't get that. Synaptic tells me that mozilla-firefox is dependant on 'firefox' which doesn't exist.

---

### Post by SpEcIeS on 2005-07-21
[QUOTE=jesse]You can always install firefox 1.0.6 from the debian unstable repository. It works. I'm using it.[/QUOTE]
What is the link to that repository?

---

### Post by darkaudit on 2005-07-21
[QUOTE=aerials]I can't get that. Synaptic tells me that mozilla-firefox is dependant on 'firefox' which doesn't exist.[/QUOTE]I'm using the mirrormax repository, and the new firefox-gnome-support is present, but not firefox itself. The dummy packages are updated.

---

### Post by Kyral on 2005-07-21
Dangit, jdong beat me. I wanted to get one to work :P

Oh well, the ones I did work, so I'm happy :D

---

### Post by jcohen on 2005-07-21
root@jasonslaptop:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  firefox-gnome-support
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

root@jasonslaptop:~# apt-get install firefox-gnome-support
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  firefox-gnome-support: Depends: firefox (= 1.0.6-1ubuntu1~5.04ubp1) but 1.0.4-1ubuntu3~5.04ubp5 is

This problem is happening on both the mirromax and brianpuccio mirrors. The problem is that /dists/hoary-backports-staging/main/binary-i386/Packages.gz does not include firefox 1.0.6 even though the firefox 1.0.6 deb is sitting in staging. Please fix this.

---

### Post by manicka on 2005-07-21
[QUOTE=jdong]FF1.0.6 built and uploaded

Thunderbird is not in Breezy. Bring it back up when it's there[/QUOTE]
 Great News!, thanks for the great ongoing effort you put into backports :D

---

### Post by SpEcIeS on 2005-07-22
Here is an idea for the impatient. :)

Since I was tired of seeing the update disk in the system tray I downloaded the deb package for firefox from here: **[http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/main/binary-i386/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/main/binary-i386/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb)**
Use **sudo dpkg -i firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb** from the download point, then **use synaptic to update the necessary files for firefox**. Well not necessary, but it will stop the update warning in the system tray.

Now I can remove firefox from the **/opt** directory. :)

_Update_
I forgot to mention that synaptic will grumble about 2 broken packages, so do not pay attention to this and update all firefox packages. Search "*firefox*"

---

### Post by jcohen on 2005-07-22
Firefox now installs from staging. Thanks jdong.

---

### Post by donar73 on 2005-07-22
[QUOTE=jcohen]Firefox now installs from staging. Thanks jdong.[/QUOTE]

Which mirror are you using? At [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) there's only the firefox-gnome-support - deb...

---

### Post by jasplund on 2005-07-22
[QUOTE=donar73]Which mirror are you using? At [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) there's only the firefox-gnome-support - deb...[/QUOTE]
It's the same with the mirrormax mirror. I can't find firefox with synaptic. But it appears to be in the repository [http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/main/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/main/binary-i386/)

Johan

---

### Post by DiGiTaLFX on 2005-07-22
Hey could someone point me in the direction to find out about this backports thing. I'd just assumed that this was all added to the main repository. And how about the extras too? I can't really find a description in the forums (I'm not very good at searching tho). Cheers
DiGiTaLFX

---

### Post by manicka on 2005-07-22
[QUOTE=SpEcIeS]Here is an idea for the impatient. :)

Since I was tired of seeing the update disk in the system tray I downloaded the deb package for firefox from here: **[http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/main/binary-i386/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/main/binary-i386/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb)**
Use **sudo dpkg -i firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb** from the download point, then **use synaptic to update the necessary files for firefox**. "[/QUOTE]
thanks for the link. The firefox package isn't showning up for me yet at mirrormax in staging.
Force installed this deb then fixed the dependecies through synaptic.

Thanks again jdong for the packages :D

---

### Post by rpgcyco on 2005-07-22
Weird, I am using the Mirrormax mirrors and all is well! I'm using Firefox 1.0.6 now.

- Rpg Cyco

---

### Post by traherom on 2005-07-22
Well, I'm new to ubuntu and it/Debian's packaging setup.

What do values do I put in the Repositories dialog so I can update through mirrormax?

---

### Post by manicka on 2005-07-22
[QUOTE=rpgcyco]Weird, I am using the Mirrormax mirrors and all is well! I'm using Firefox 1.0.6 now.

- Rpg Cyco[/QUOTE]
 hmm, not sure why the package wasn't showing up for me. I don't usually use staging and only unhash it when necessary.

anyway ,as long as we have 1.0.6 from backports, it's all good however we get there :D

---

### Post by geearf on 2005-07-22
is firefox only in the staging area until more test ?

I'm a bit afraid to install something in staging at work :)

Thanks,

---

### Post by darkaudit on 2005-07-22
as of 9:30(ish)am EDT, both mirrormax and Brian's only had firefox-gnome-support in staging as far as synaptic could see. I used the link Species provided to get the .deb of firefox, installed that no problem :) and went to synaptic. it reported that firefox-gnome-support was broken. I upgraded that package and now have 1.0.6 up and running.

Then I went here: [http://ubuntuforums.org/showthread.php?t=39263&highlight=firefox](http://ubuntuforums.org/showthread.php?t=39263&highlight=firefox) to get the proper Firefox logos in the Help->About window. :)

---

### Post by jasplund on 2005-07-22
its being fixed [http://ubuntuforums.org/showthread.php?t=50995](http://ubuntuforums.org/showthread.php?t=50995)

---

### Post by jesse on 2005-07-22
1. Uninstall every package you have containing the word "firefox"

2. Then add the following line to the file /etc/apt/sources.list

deb [ftp://packages.debian.org/debian/](ftp://packages.debian.org/debian/) unstable main contrib non-free

and save the new version of sources.list (You'll have to open it as root by typing "sudo gedit /ect/apt/sources.list" at a terminal to have write priveliges.) 

3. Open Synaptic (if it's not already running) and reload the package list. 
(or, without synaptic running, type "sudo apt-get update" at a terminal)

4. In synaptic do a search for "firefox." You should not have any firefox packages installed at all, so install "mozilla-firefox" and "mozilla-firefox-gnome support" which are in the debian unstable repository. These are the only firefox packages you really need at all. You do not need "firefox" and "firefox-gnome-support" from the backport repository (which do not contain the word "mozilla" and which depend on "mozilla-firefox" and "mozilla-firefox-gnome-support" anyway. 

5. IMPORTANT! Once you've installed these two mozilla-firefox packages, comment out the debian unstable repository. (Put a # symbol in front of the line in your file /etc/apt/sources.list)

#deb [ftp://packages.debian.org/debian/](ftp://packages.debian.org/debian/) unstable main contrib non-free

It's a good idea to keep it in your list of disabled repositories, just in case you ever need the newest version of a debian package, but it's not a good idea to have it enabled as a source unless you need such a specific newer package. E.g. if you want to use gtkpod with an Ipod shuffle, you have to the use version from the debian unstable repository, as the older versions of gtkpod found in the ubuntu repositories (including backports and breezy so far) and the stable debian repositories don't work with the shuffle. (Sorry for going slightly off on a tangent.)

---

### Post by Kyral on 2005-07-22
Firefox 1.0.6 and all related packages are in Backports/Staging now. I updated about 2 hours ago and they came down the pike

---

### Post by jesse on 2005-07-22
Good to hear. I haven't checked the backports in a few days. Perhaps I'll switch from the debian packages to them.  :roll:

---

### Post by jesse on 2005-07-22
I checked the backport repositories I have, but they only list 1.0.4 as the newest version specifically for ubuntu. Where is the ubuntu version of 1.0.6 you're referring to located? 

I'd prefer to use it, but the debian unstable packages have the same functionality.

---

### Post by AndyAWS on 2005-07-22
[QUOTE=jesse]I checked the backport repositories I have, but they only list 1.0.4 as the newest version specifically for ubuntu. Where is the ubuntu version of 1.0.6 you're referring to located? 

I'd prefer to use it, but the debian unstable packages have the same functionality.[/QUOTE]

The new packages are in Staging
Make sure you have the Backport Staging repos in your sources.list.

---

### Post by jesse on 2005-07-22
Silly me. Had I read the entire thread before posting my silly debian recommendations, I would have figured this out. 

 [-X

---

### Post by jdong on 2005-07-23
UPDATE: 1.0.6 has been pulled from the repository ([http://lists.ubuntu.com/archives/ubuntu-users/2005-July/043452.html)](http://lists.ubuntu.com/archives/ubuntu-users/2005-July/043452.html)), due to the extensions problem.

---

### Post by jesse on 2005-07-23
I'm still using the debian version of 1.0.6 and have various extensions installed and working without problems. Of course I've only had it installed for about a week. Before that I had the Ubuntu version of 1.0.2

Is this an issue just with the Ubuntu version of 1.0.6 or with 1.0.6 in general?

---

### Post by manicka on 2005-07-23
[QUOTE=jdong]UPDATE: 1.0.6 has been pulled from the repository ([http://lists.ubuntu.com/archives/ubuntu-users/2005-July/043452.html)](http://lists.ubuntu.com/archives/ubuntu-users/2005-July/043452.html)), due to the extensions problem.[/QUOTE]
 but the backports version is still there isn't it? I'm having no problems with it

---

### Post by SpEcIeS on 2005-07-23
[QUOTE=manicka]but the backports version is still there isn't it? I'm having no problems with it[/QUOTE]
Everything works well on my end too. I wonder what is up?

---

### Post by jdong on 2005-07-23
[QUOTE=manicka]but the backports version is still there isn't it? I'm having no problems with it[/QUOTE]

No, no, I've soft-deleted it from the repository, too.

[http://backports.ubuntuforums.org/log.php](http://backports.ubuntuforums.org/log.php)

Pulled via revisions 492 and 493.

---

### Post by manicka on 2005-07-23
[QUOTE=jdong]No, no, I've soft-deleted it from the repository, too.

[http://backports.ubuntuforums.org/log.php](http://backports.ubuntuforums.org/log.php)

Pulled via revisions 492 and 493.[/QUOTE]
 That's a shame as the backports version seems to be okay. 

I understand why it was pulled though :)

---

### Post by jdong on 2005-07-23
[QUOTE=manicka]That's a shame as the backports version seems to be okay. 

I understand why it was pulled though :)[/QUOTE]

Did it work with extensions (TabBrowser, AiO gestures, etc)? From what I understand, as soon as you add in the extensions, firefox will start crashing and misbehaving.

If you guys want, I can restore it to Staging again for some further testing. Just let me know.

---

### Post by jdong on 2005-07-23
Firefox 1.0.6 has been **restored to staging**. It'll take till at least the top of the hour before you can get it via a mirror.

Please **test and REPORT BACK** if this package:

(1) Works with no extensions installed
(2) Works with extensions installed



I'll use this information to make a better decision about this package's future status in Staging.

---

### Post by manicka on 2005-07-24
I'm using it with the existing extensions that I had before updating from staging.

English (GB) Language Pack
fireftp
Adblock
Smiley Xtra
Bandwidth Tester
Beagle Indexer
Web Developer

I must admit that a few of these like the bandwidth tester I hardly ever use, but I haven't had a single crash.

I'm not that keen on messing with things but if I get a chance, I'll add in a couple of new ones (the ones specifically mentioned above to start) and let you know how it goes

---

### Post by manicka on 2005-07-24
[QUOTE=manicka]I'm using it with the existing extensions that I had before updating from staging.

English (GB) Language Pack
fireftp
Adblock
Smiley Xtra
Bandwidth Tester
Beagle Indexer
Web Developer

I must admit that a few of these like the bandwidth tester I hardly ever use, but I haven't had a single crash.

I'm not that keen on messing with things but if I get a chance, I'll add in a couple of new ones (the ones specifically mentioned above to start) and let you know how it goes[/QUOTE]
 Okay I removed all bar the language pack which I couldn't uninstall

no problems

Added them all back in bar fireftp, bandwidth tester and added Tabbrowser preferences

no problems so far

---

### Post by garnertr on 2005-07-24
[QUOTE=fishfork]I went ahead and got Firefox 1.0.6 from mozilla.org - you get a nice install wizard, just like the windows version. Just make sure you install it somewhere sensible like /opt.[/QUOTE]


?? what is the purpose of /opt??  Is it to install personal software (ie, not installed by ubuntu?)  I'm a dweeb and a newbie, so pls explain.. willing to learn, just need the background.. :)

Thanks!!

---

### Post by rpgcyco on 2005-07-24
> ?? what is the purpose of /opt?? Is it to install personal software (ie, not installed by ubuntu?) I'm a dweeb and a newbie, so pls explain.. willing to learn, just need the background..

Here is some information. :)

[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html)

- Rpg Cyco

---

### Post by mr_pouit on 2005-07-24
Using Firefox 1.0.6 with the existing extensions that I had before updating from staging :
- English (gb) language pack
- bbcode 0.4.1.1
- Français language pack
- User Agent switcher 0.6.6
- Tabmix Plus 0.2.3

and no problem ! :lol:

i will try later without extension ;)

---

### Post by jasplund on 2005-07-24
Using Firefox 1.0.6 with the existing extensions that I had before updating from staging :

Swedish Language Pack 1.0.1
Adblock v.5 d2 * nightly 39
Plain Text Links 0.2
WebmailCompose 0.6.1
Gmail Delete Button 2.6.1

I haven't had any problem at all with the version from staging

---

### Post by manicka on 2005-07-24
Also added Forecastfox which is supposed to only work on deerpark, but it is functioning well on 1.0.6

---

### Post by ozzie123 on 2005-07-24
So the question is... when will FF and Thunderbird 1.0.6 comes out from the staging tree?

---

### Post by jdong on 2005-07-24
[QUOTE=ozzie123]So the question is... when will FF and Thunderbird 1.0.6 comes out from the staging tree?[/QUOTE]


We first need more feedback about the plugin compatibility. If it's good, this should be in stable in a week.

---

### Post by SpEcIeS on 2005-07-24
I know that when I installed 1.0.6 in my /opt, with mozilla's installer, the extensions went for a loop. Some worked and some did not. After applying the backport package, manually, then adding the other firefox dependency packages, everything worked fine. It still continues to work well. Which extensions are reported as not working well?

---

### Post by rpgcyco on 2005-07-25
I'm having no troubles with the backported 1.0.6 with no extensions installed or with the Google Toolbar installed.

- Rpg Cyco

---

### Post by Virtual DarKness on 2005-08-01
Seems that thunderbird 1.0.6 as been released also as an official update.. hmm...

bye,
Giovanni.

---

### Post by dbloom on 2005-08-02
can anyone update extensions with firefox 1.06?  i still have the same extension update issues from 1.04... running the 1.06 version from the mozilla web site seems to work flawlessly though....

---

### Post by manicka on 2005-08-02
[QUOTE=dbloom]can anyone update extensions with firefox 1.06?  i still have the same extension update issues from 1.04... running the 1.06 version from the mozilla web site seems to work flawlessly though....[/QUOTE]
 Try removing Firefox with synaptic and doing a 'complete removal'. Then  reinstal 1.0.6

---

### Post by dbloom on 2005-08-04
>  Try removing Firefox with synaptic and doing a 'complete removal'. Then reinstal 1.0.6 

it didn't seem to work.  i'll just stick with the binary from getfirefox -- it runs great.

thanks though.

---

### Post by ozzie123 on 2005-08-04
I use the file right from synaptic. Didn't uninstall firefox first, just upgrade it. It works just fine.

---

