---
title: "Unity desktop suddenly appeared... do not want!!"
date: 2012-02-25
forum: Desktop Environments
---

### Post by dkolars on 2012-02-25
OK, this sucks big time...  Have xUbuntu 11.04.  Was running just fine...  installed the latest automatic updates, and now I have the Unity desktop.  IT SUCKS...  I can't find anything...  

So, went on a hunt, found:
1)  [http://www.liberiangeek.net/2011/04/change-classic-ubuntu-desktop-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/change-classic-ubuntu-desktop-ubuntu-11-04-natty-narwhal/)

-&-

2)  [http://www.liberiangeek.net/2011/05/enable-ubuntu-classic-desktop-in-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/05/enable-ubuntu-classic-desktop-in-ubuntu-11-04-natty-narwhal/)


Attempted the "log out" solution from the 1st link, but when I clicked my name, it simply logged me back in without any choice of desktop.

I did the change from link #2, and when I attempted to re-start the system, it hung, and my video card started screaming... well, humming loudly, at least...  Killed the power, re-started.  

I still have the Unity desktop...  I do NOT want the Unity desktop!!!

Found a You Tube video telling how to get the classic desktop back... same instructions as link #2... Did that again (it was already set to "Ubuntu Classic"), re-boot... I STILL have the Unity desktop.   Major BS... I call BS on this...

Also found this:

[http://ubuntuguide.net/ubuntu-11-04-natty-login-to-classic-gnome-2-desktop](http://ubuntuguide.net/ubuntu-11-04-natty-login-to-classic-gnome-2-desktop)

Can not find:
"2.) Right click on “main menu”, “global menu” at top left screen and uncheck “lock to panel”, then select to “remove from panel”
3.) Right click on top panel, choose “add to panel” and then add “menu bar”.
Now you’re in Ubuntu 11.04 with classic gnome desktop!"

And this:
[http://www.emreciftci.net/2011/07/speed-up-ubuntuxubuntu-1104.html](http://www.emreciftci.net/2011/07/speed-up-ubuntuxubuntu-1104.html)

Cannot find any of this:
"2) For Xubuntu 11.04 change the recent session graphical interface  to classic Xfce.
* Click the Applications Menu icon > System>Login Manager

* Find and click on Login Screen where you can set your default session as well.
* Select Xfce as session graphical interface."


I have 32 icons in the bar on the left side of my screen!  I have I don't know how many copies of Chrome running, as when it didn't start, I clicked it again... and again...  <Alt><Tab> thankfully shows them, so at least they didn't take THAT away!!

And my graphics card is now groaning under some load that the OS has put upon it...  $#)(*^%$Y(*%^...

Major BS!  Help?  :confused: :mad:  

This ~could~ push me back to Windoze!!

---

### Post by mikodo on 2012-02-25
Have a look at this and see if you think it might be helpful:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

That, should remove Unity DE and leave the Xfce DE.

---

### Post by dkolars on 2012-02-25
Well, I did the psychocats "fix"...  Got a totally different look/desktop, missing bars, etc.  So, I reinstalled 11.04 over 11.04 using a live CD.  Seems to be back to normal, but I'm sure that I'm gonna find things missing... I note that several of my icons on my program bar are gray squares rather than the programs icon... mainly because Ub says the programs don't exist!!  So, gots to hunt them up and re-install...  NO MORE "updates", Ubuntu!!!  I'm not marking this [Solved] just yet!!

---

### Post by Linuxratty on 2012-02-25
Whoa! That's not good!
I'd planned to get Xubuntu...How could something like this even happen!?

---

### Post by dkolars on 2012-02-25
Updates... I had upgraded "normally" from 10.10 via the updates window...  11.04 looked and acted just the same as older versions... well, acted better, as it was faster!  Then, (lesson learned!) I clicked on auto updates and they zinged me...  Rule... READ the updates...  I'd never really bothered after the first few times I actually took the time to read what was going to be updated... never was anything that impacted the operation of the OS...  NOT SO this time...  When I have more time, I'll Google the updates and see which one of the b-tards installs Unity...  and write it down on a post-it and put it on my monitor!!  The next upgrade I do will not have Unity!!  If necessary, I'll go back to Windoze!  This is/was ridiculous...  I don't mind changes, if they serve a function... imho, all Unity does is serve to confuse and make the user re-learn everything again...  AND, it is not customizable!  Mistake #1 by the developers...  Mistake #2 is hyping it as an improvement... that is the users decision!!  

IF you make an 11.04 disk, you should be able to run it ok... just watch out for the "upgrades"!!

---

### Post by Krytarik on 2012-02-25
> **Linuxratty said:**
> Whoa! That's not good!
I'd planned to get Xubuntu...How could something like this even happen!?
Actually, this was the result of things you *definitely* shouldn't do, and things you *better* shouldn't do (listed in the order of the escalation that took place):

[LIST]
[*]Installing the Ubuntu and Xubuntu versions side-by-side (in a single system; apparently).
[/LIST]

[LIST]
[*]Disabling the password query on login (completely; not the same as auto-login!).
[/LIST]

[LIST]
[*]Running commands that aren't meant for the installed Ubuntu version (apparently).
[/LIST]
Regards.

---

### Post by mikodo on 2012-02-25
> **Linuxratty said:**
> Whoa! That's not good!
I'd planned to get Xubuntu...How could something like this even happen!?
Myself, when it comes time, to move on from Ubuntu 10.04, I plan to backup my personal stuff, ( Docs, Pics, Music, FF and TB profiles etc.), and fresh install Xubuntu 12.x. Then copy my personal stuff into the new install. Doing it this way, clears out all the old, and I will have a pristine install. Everything should be fine then.

Upgrading releases through apt/Synaptic, when switching from Ubuntu (with and without Unity shell) and with Ubuntu and Xubuntu, is possibly what went wrong for the OP. It is a bit confusing.

dkolars: I hope you get it sorted out, to your liking.

---

### Post by Hylas de Niall on 2012-02-25
Aw... seriously, don't let this make you go back to the Windows option.
There are other options that don't tie you down, track you, shackle you.
Stay OS. You know it makes sense.

---

### Post by dkolars on 2012-02-26
Ok, so I'll very likely NOT go back to Windoze!  ;)  

As to Ubuntu vs. xUbuntu... I was running XUbuntu 10.10 (started out with 9.04 and upgraded a couple of times to get there), and when I upgraded to 11.04 via the Update Manager it put on whatever flavor... x or not, I don't know...  but now I've got regular "Ubuntu" 11.04.  Too many flavors and I have never seen a detailed explanation of the differences between them all and the problems that might occur by mixing them up...  So, anywho, it seems to be stable now and I'm hoping it stays that way!!  I'd just like to be productive instead of having to mess with "stuff"... when I was an IT guy, they paid me to mess with "stuff", but now that I'm retired (ha!), there's no pay involved!!

---

### Post by dkolars on 2012-02-26
Aha... so, now, a day after the new install, the Update Manager pops up... says "259 updates have been selected.  119 MB will be downloaded"

So, scroll thru them and under "Recommended Updates" find:
"Interface designed for efficiency of space and interaction.  unity (Size: 609 KB)"
Description:
"Unity is a desktop experience that sings. Designed by Canonical and the Ayatana community, Unity is all about the combination of familiarity and the future. We bring together visual design, analysis of user experience testing, modern graphics technologies and a deep understanding of the free software landscape to produce what we hope will be the lightest, most elegant and most delightful way to use your PC."

And, several more files that go with this... HA... I gotcher "sings"!!  "familiarity and the future"???  I don't want any part of that future, thanks anyway.

---

### Post by Dr Watts On on 2012-02-26
oh great! Xubuntu Live 11.10 CD just an hour ago installed to this  laptop a second time (full manual repartitioning and reformat, just like  first time yesterday) and then I found this thread. What happened to me  was: 
when I got original logon and settings like I wanted, and a few successful re-logons, 
I noticed that I was offered TWO choices: XFCE was SECOND choice, Xubuntu was 1st. 

Now, why would I install Xubuntu other than for the lightweight desktop  anyway? It explains nowhere I found, that there would be a choice on  logon screen. So I logged on out of curiosity as Guest on the XFCE  choice. When I logged out, could not get back in as original user on  Xubuntu. Didn't see a lot of difference in the look and feel of the  desktop/apps in XFCE, but no explanation of the difference! Then somehow  no further LogOns to Xubuntu because my password failed. What?
I am in install #2, logged on nearly as I remember, to the Xubuntu  desktop choice, xfce still offered. What the H is the X in Xubuntu FOR  if I don't get a straight XFCE desktop PERIOD??? What is WRONG with  developers that don't EXPLAIN this stuff in their own "New Web Presence"  -- stuff that goes against the results implied by the NAME of the OS?
I chose again the 208 Security and other "updates" after 2nd install.  Watching details, noticed a bunch of Gnome stuff... WHY in (may I scream  it) -X- ubuntu? Having read this thread, I suspect I will be making a  third install over this, and put in updates AFTER I parse and delete  anything I don't like that got installed, and then do individual  updates, probably security only. Agreed, this stuff is stupid. 
AGAIN: WHAT the HELL IS the "X" in the name FOR! At least with  "standard" Ubuntu I would know I am getting (screwed with) the Unity  desktop. What, did the X crew just add stuff to Ubuntu? 
BRING IT -- I'm  pissed (and always ready to admit when I see I'm wrong on any level).

---

### Post by Krytarik on 2012-02-26
> **Dr Watts On said:**
> I noticed that I was offered TWO choices: XFCE was SECOND choice, Xubuntu was 1st. 
[..]
What the H is the X in Xubuntu FOR  if I don't get a straight XFCE desktop PERIOD???
[..]
I chose again the 208 Security and other "updates" after 2nd install.  Watching details, noticed a bunch of Gnome stuff... WHY in (may I scream  it) -X- ubuntu?
Seems like you would be better off with Alternate CD + "xfce4" meta-package:

[LIST]
[*][http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)
[/LIST]

[LIST]
[*][http://packages.ubuntu.com/oneiric/xfce4](http://packages.ubuntu.com/oneiric/xfce4)
[/LIST]
Instead of Xubuntu:

[LIST]
[*] [http://packages.ubuntu.com/oneiric-updates/xubuntu-desktop](http://packages.ubuntu.com/oneiric-updates/xubuntu-desktop)
[/LIST]
Regards.

---

### Post by Dr Watts On on 2012-02-26
@Krytarik
Danke! To clarify: the LogOn Screen offers Both Environments. I think I got the iso for the CD from the Xubuntu website, I burned it on my other computer, installing on this laptop of some poor kid my neighbor knows. Just searched "installed pkgs" filtered for Unity, found 6 pkgs. Very tempted to kill a couple of them. Will need to go to bed now (it's almost 1 AM California time) and return tomorrow to check out the links you provided. Thanks again.
PS Laptop is circa 2004 Toshiba Tecra M2 with 512MB ram, 40GB HDD. And SLLLOOOWWW! Had XP. dd'd drive "0"s.
Guten Tag

---

### Post by Elfy on 2012-02-26
> **dkolars said:**
> Aha... so, now, a day after the new install, the Update Manager pops up... says "259 updates have been selected.  119 MB will be downloaded"

So, scroll thru them and under "Recommended Updates" find:
"Interface designed for efficiency of space and interaction.  unity (Size: 609 KB)"
Description:
"Unity is a desktop experience that sings. Designed by Canonical and the Ayatana community, Unity is all about the combination of familiarity and the future. We bring together visual design, analysis of user experience testing, modern graphics technologies and a deep understanding of the free software landscape to produce what we hope will be the lightest, most elegant and most delightful way to use your PC."

And, several more files that go with this... HA... I gotcher "sings"!!  "familiarity and the future"???  I don't want any part of that future, thanks anyway.

I'd think that if unity is being called  then it needs a bug report.

You should be able to in the meantime deselect the unity bits in update manager.

---

### Post by Flymo on 2012-02-26
That's pretty scary...  Let us know how it pans out, please.

Have not had great success with upgrading *buntus cleanly over the years since Breezy - it's a big ask, imho.  Usually just back up the 'home' stuff and log all the installed apps, then migrate to a fresh installation - usually on an adjoining partition. 

Fwiw have been exercising Xubuntu Precise Alpha 2 for a few days now, both i386 and AMD64 '-desktop' flavours, they both seem to be  well made and have had no problems despite their Alpha status. 

Xubuntu may be the saviour of Canonical yet.   Kubuntu is quite nice nowadays, but our (mostly puny) hardware has trouble carrying KDE4 comfortably.  Must not mention our opinions of Unity in polite company.....:lolflag:

---

### Post by Dr Watts On on 2012-02-26
@everyone: per suggestion by Krytarik, I am downloading the alternate iso but am confused how to proceed from the link for the xfce pkg. The suggestion on the page showing dl locations for the XFCE full package suggests:
*> If you are running Ubuntu, it is strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/oneiric/aptitude") or [synaptic]("http://packages.ubuntu.com/oneiric/synaptic") to download and install packages, instead of doing so manually via this website. **You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:*
  *deb [http://[I]ubuntu.mirror.cambrium.nl/ubuntu/](http://[I]ubuntu.mirror.cambrium.nl/ubuntu/)* oneiric main universe [/I]** But I don't know how or whether it's possible to use the CLI for aptitude or synaptic on the deb file on the site. Also unclear if the listed line is inserted into sources.list, that just lets me go there, but that seems to be enabling aptitude or synaptic, and isn't the alternate cd iso strictly CLI and aren't aptitude or synaptic gui? 
Do I use apt get, or ... could someone please tell me so I can be more "grounded" on what to do at the package site?
Thanks, DrWattsOn

---

### Post by Krytarik on 2012-02-27
> **Dr Watts On said:**
> per suggestion by Krytarik, I am downloading the alternate iso but am confused how to proceed from the link for the xfce pkg.
After you used the Alternate CD to do a basic installation, you will be left with only the CLI, yes. From there, you first need to enable the "universe" repo in your "/etc/apt/sources.list", as it is disabled by default (as well as "multiverse"); you can use "nano" for that:
```
sudo nano /etc/apt/sources.list
```Then just remove the "#" in front of both the respective lines, to look like this:
```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
```Thereafter, update the package database, and install the "xfce4" meta-package, pulling in all its dependencies and recommends:
```
sudo apt-get update
sudo apt-get install xfce4
```For all of this to work out, though, you obviously need a working internet connection, however you manage that, and if it's just a temporary direct ethernet connection with your router, if you have one.

---

### Post by Dr Watts On on 2012-02-27
Hello Kryatik!
So the source is already in the list and just needs uncommenting. I am wondering: will the alternate.iso install have all the drivers of the regular Xubuntu install.iso cd, so that I can use the wireless? I use my neighbor's W/L since I maintain and repair his computer & actually admin his W/L router. He even refuses payment, God bless him! But I would need to go into his place to wire in, so would prefer to do it wirelessly. But I wouldn't know how to activate the wireless built into the laptop from CLI, even if the alternate.iso did install it's driver. I'm still good in DOS but not so much in bash. Will wait for a response before proceeding. Thanks for all the help so far.
PS: Nice Avatar (ground)
DrWattsOn

---

### Post by mikodo on 2012-02-27
Hi Krytarik,

I have decided, to follow your advice on this too! 

Your directions, as in your previous post, will be very helpful.

Any other "commands", that you can think of, that we will need to use, to get the Xfce DE working?

I have been asking around, here and on #ubuntu IRC and have made up my mind up to to with the Alternate CD install, (d-i) as they called on #Ubuntu, with the Xfce meta-package. A "vanilla-install", sounds real good.

Thanks, for the direction.

---

### Post by Krytarik on 2012-02-27
> **Dr Watts On said:**
> will the alternate.iso install have all the drivers of the regular Xubuntu install.iso cd, so that I can use the wireless?
Yes, and at least after installing XFCE, you should be able to set it up to actually use it (depending on what network tools it offers, obviously), but I don't know how to do that from the CLI. And since the concerning device is actually a laptop, I'd rather go for the 'visit the neighbor' option :D ; this way, you could also show off the newly installed system to him, inciting him to switch over to the Linux side, if he hasn't already. ;-) Otherwise, you need to google that yourself. :P

> **Dr Watts On said:**
> PS: Nice Avatar (ground)
Thanks, also for the earlier German bits! :D

> **mikodo said:**
> Any other "commands", that you can think of, that we will need to use, to get the Xfce DE working?
Actually, now that you made me think about it, installing a display manager would be a good idea :P ; I suggest LightDM:
```
sudo apt-get install lightdm
```Other than that, just press Ctrl+Alt+Del to reboot; no commands needed for that. :P

---

### Post by mikodo on 2012-02-27
Wonderful, 

Thank you again.

---

### Post by Dr Watts On on 2012-02-27
Bitte Schon, Krytarik
Ich hatte zwei Jahren in der Schule wahrend 1960 & 61 Deutsch studiert, machte ganz allen "A" (beinahe 98% average). Anyway, will do as you suggest with hardwired connection. I've put Linux Mint, Ubuntu, and now Xubuntu on about 5 other people's computers. Neighbor isn't really what we'd call a computer user. But of those 5, two belong to his in-laws, they only use Wiindows to print. This laptop belongs to a 17yr old really poor ($) kid friend of my neighbors. 
 
Will post my results from following your advice. Hope mikodo does the same. Wonder also about the OP, did those problems get resolved?
Thanks again,
DrWattsOn (a mixed pun: the Windows tool, & I've been paid in many specialties as Electronics Tech/Troubleshooter 1962-2008, so Watts On).

---

### Post by Krytarik on 2012-02-27
> **Dr Watts On said:**
> Neighbor isn't really what we'd call a computer user.
Well, my mom isn't a 'power user' either, plus already retired, but I introduced her to Ubuntu quite some years back - and she's loving it :D , much over Windows, besides some gaming stuff, of course.

> **Dr Watts On said:**
> DrWattsOn (a mixed pun: the Windows tool, & I've been paid in many specialties as Electronics Tech/Troubleshooter 1962-2008, so Watts On).
Very cool! :D

---

### Post by mikodo on 2012-02-27
@ Dr. Watts On:

I will not be leaving Ubuntu 10.04 until, the EOL of Lucid. I am just reading and learning Xfce/Xubuntu for now. I may dual boot into the Xubuntu DE again, as I have before, with Lucid until then.

Sorry, I won't be posting anytime soon, about my Alternate Cd install to Xfce meta-package. The information that Krytarik has given us, is well stored on my local disks, for now. I wish you the best, and will be following any updates to this thread by you, Krytarik, the OP and anyone else joining us to Xubuntu.

:<)

---

### Post by dkolars on 2012-02-27
OK, been away from 'puter for a day or two... my, this discussion has gotten good!!

Forestpiskie sez:  > I'd think that if unity is being called then it needs a bug report.

Unfortunately, I think that things on my system have gotten very confused!  I was running XUbuntu 10.04...  I upgraded to 10.10 via the Update Manager, and it was again, XUbuntu.  Then I upgraded to 11.04, and it went south after a couple of days...  Unfortunately, I didn't pay close enuf attention before I used a live CD install 11.04 over 11.04.

So, I don't know IF I was running XUbuntu 11.04 as the upgrade to 10.10...  However, the Live CD of 11.04 that I installed over 11.04 is Ubuntu, NOT XUbuntu...  

And, what's more, looking at the screen shots on the web for XCFE, I've always had Gnome...???  Even with XUbuntu, and never saw a screen that gave me a choice of Desktop Enviros...  So, unless the earlier versions of XCFE looked like Gnome, or did not have the choice option, I've never seen it...

So,  for now, I'm running "regular" Ubuntu...  This is where I'm seeing Unity as one of the "updates".   I didn't really realize that there was that much difference between the different 'buntus, and have always just gone to the Ubuntu site and downloaded the .iso for the next version... at some point, they gave me the "X" version, after 9.04, I would guess???   Or an update went to "X"???  dunno... only that I refuse to use Unity...  Of that, I'm certain!!

So, will d/l a version of XUbuntu 11.10 and run it from the Live CD and see what it looks like...  

According to this thread:  

[https://lists.ubuntu.com/archives/xubuntu-users/2011-January/002671.html](https://lists.ubuntu.com/archives/xubuntu-users/2011-January/002671.html)

there are no plans for Unity to invade the X enviro as it's not a project of the Ubuntu developers...

Here's a-hopin'!!

---

### Post by Elfy on 2012-02-27
If you installed Xubuntu then you get the choice to run the XFCE desktop - this is different to Xubuntu, there being some at least some 'gnome' stuff kicking about - at least there was here - you shouldn't be getting Unity.

I don't have Unity as an option here - though I am using 12.04. 

That would not be much fun ... 

I would be inclined to backup and reinstall and then update if you can't get rid of Unity - though it should be removable.

---

### Post by Dr Watts On on 2012-02-28
@**dkolars**
I was confused, even since your OP, re the precise sequence of installs on your machine, including its original starting point. Then, you twice made mention of [FONT=Georgia]*"installing 11.04 over 11.04"*[/FONT], and lost me :confused:completely.

Perhaps if you could make a short list rather than referring to them in a linear sentence? That's how I have to do my own projects to not lose track: making a table with Machine, OS, date/time, and comments. My concern is to not accidentally fall into the trap you did, so I want to consciously avoid the steps you followed that put you there.

I won't be wiping and reinstalling from vanilla [non-gui]-buntu for a couple days. I want to be sure that when I return this laptop, the kid/enduser will have a simple free (no $$) tool primarily for his schoolwork projects, so I want him to have only one logon environment, secured.

I noticed in this standard Xubuntu 11.10, when running Firefox and some apps, and checking "free" in a terminal: 
out of 512MB total, it drops to approx. 
40-45 MB free in Xubuntu Logon, and has around 122 MB free in XFCE Logon.

I worry about not understanding the tie-ins to Gnome. I would assume they exist to allow Gnome apps to run. But I don't Gnow (couldn't resist :D ), like: are Abiword and other ostensibly XFCE apps actually dependent on Gnome libs? I _just this second_ got Update Mgr. popup for "Gnome XML Lib" and "Python bindings" for it, as Security Updates. Is that because, at this second I'm in Xubuntu, and would the same u/d's have prompted in XFCE env?

I intend to eventually automate installation of security updates so I won't have to become a "surrogate father" babysitter for the kid when he gets this laptop back.

And I positively want, to NEVER see Unity on this laptop. I do plan on subjecting another machine to Unity to familiarize and figure out not just how it works, but WHY some friends of mine actually LIKE Unity (gag!) Unity on the dual-boot Windows 7 machine I built them (they only login to Windows to print).

I'll remain subscribed to this thread until I report on my wipe/reinstall of basic-untu and adding XFCE to it. Never done that before, so "bated breath" (moderate anxiety; not admitting to "fretting"). Lurking for now.
DrWattsOn

---

### Post by Dr Watts On on 2012-02-28
> **Dr Watts On said:**
> 
I worry about not understanding the tie-ins to Gnome. I would assume they exist to allow Gnome apps to run. ... 
@all: from Distrowatch.com
> Xubuntu is a Linux distribution based on Ubuntu. Unlike its parent,  however, Xubuntu uses the light-weight Xfce desktop environment and is  optimised for lower-end machines. The distribution includes only GTK+  applications where possible.
So, can someone give me a link to some kind of official documentation, that defines precisely what the X in Xubuntu means? Since Xfce dev's may not make the cut for Xubuntu v 11.04 (LTS ?) how could it remain named X ubuntu?? What is the X even there for in the name? Frustrated at nonsense,:roll:
DrWattsOn

---

### Post by dkolars on 2012-02-28
> Then, you twice made mention of "installing 11.04 over 11.04", and lost me completely.

Well, that's what the screen said when I clicked on "Install Ubuntu" while booted up from the Live CD...  Apparently, Linux will do that... Windoze doesn't like to do that, or at least queries one about it more than Linux does...  Now I'm busy finding all the programs that I used to have, and don't anymore!!  Not that many, so not so hard... doing a bunch of video editing and creating flyers now and realized that Gimp was gone... been doing a lot of "sudo apt-get install..." lately.

Yeah, I should have kept a record of what versions I had when, but didn't realize that it would become an issue...  I'm running XUbuntu on the laptop from Live Cd now just to see what it's like... of course, it can't find my wireless in the HP laptop any better than any other version!  Even with 10.10 I have to do the "rfkill list all" and "rfkill unblock" commands, then hold down the wireless button for 30 secs. to activate "things"... Can't even get that to work with 11.10 XUbuntu yet.  If it can't find my wireless, why bother...  Wish there were more industry "standards" to eliminate all the time-wasting stuff...

Wondering if it's possible to move the program bar to the bottom of the screen and change the background in XUbuntu 11.10... I can find nothing that looks like it's possible...  I don't like the top bar!

---

### Post by Dr Watts On on 2012-03-03
> **Dr Watts On said:**
> @all: from Distrowatch.com

So, can someone give me a link to some kind of official documentation, that defines precisely what the X in Xubuntu means? Since Xfce dev's may not make the cut for Xubuntu v 11.04 (LTS ?) how could it remain named X ubuntu?? What is the X even there for in the name? Frustrated at nonsense,:roll:
DrWattsOn
Update: Ok, tomorrow I plan on installing non-gui buntu then xfce  via wired internet connection. I STILL cannot find any explanation: if the X in Xubuntu stands for XFCE, then how can Xubuntu offer 2 desktop enviroment logons: one to Xubuntu, the other to XFCE? If they're the same how can they be different? I thought coding required logical thought processes. Apparently not.
<rant>I have lost respect ... </rant>
Anyway, expect to be done by Monday. Otherwise I'll just rewipe the drive and give up totally on XFCE or is it Xubuntu or is it XFCE or is it ...? Maybe Mint and their "MATE" will make sense. That's all I'm seeking: I don't mind the complexity, I do mind <rant> ... </rant> Still frustrated at nonsense,:roll:

---

### Post by dkolars on 2012-03-05
In the same vein as the title, but a bit different... I've tried Xubuntu 11.10 on my laptop from the CD... seems fine, pretty customizable, etc. etc.  

So, I go to install it and see the following screen:

> This computer currently has Ubuntu 10.10 on it.  What would you like to do?

*  Install Xubuntu 11.10 alongside Ubuntu 10.10

*  Upgrade Ubuntu 10.10 to 11.10

*  Erase Ubuntu 10.10 and reinstall

*  Something else

The language used is possibly flawed?

"Upgrade to 11.10" tells me that I will be upgraded to "Ubuntu" 11.10, the version that has Unity.  Since I need to have an internet connection to install X11.10, I'm certain that this is what they mean... if not, they should be more specific...   Why is this an option with an Xubuntu Live CD?  

"Erase and reinstall", taken literally says that it will reinstall 10.10.  Again, did they really mean that?

I guess one does not have to be fluent in language to be a programmer, huh?  (PS, I used to program)...

Where is the option:

> *  Install Xubuntu 11.10 over the current version

Are the flavors of Ubuntu so different that my settings for various programs that exist in both the Ubuntu and Xubuntu versions cannot be saved when installing?

So, now to abort the install, take a look at what I will lose by erasing Ubuntu 10.10, copy stuff to flash drive, etc. etc. etc.  PIA!!!

---

### Post by Dr Watts On on 2012-03-05
100% agreed! The CD did not recognize your installed system as being Xubuntu. From there on the choice of wording is irrelevant. If your installed system is truly Xubuntu, then the CD is bad. I wonder if you had one of those CD/DVD's that come with some magazines and offer multiboot to any of 4buntu's? Then they misprogrammed the CD/DVD, and you need to burn the iso yourself from a md5sum or sha256 verified download. I still haven't scrubbed this installation that offers 2 desktops at login. It is working so great I think I'll just pass it to the end user, and when he asks me, I'll just admit I don't know. I think I have spent 5x the time on computers screwing around trying to get them to function like I want, than the time I have actually been productive. Laugh's on me. Reminds me of back in the 80's and my 55 Chevy street racer. I gave it up when I realized I spent more time under it than in it. Not to mention $$$.

---

### Post by dkolars on 2012-03-05
Ah, but my installed system is NOT Xubuntu, 'tis Ubuntu...  still, why does it not offer to overwrite the existing OS without doing a delete?  

As I recall, computers were supposed to simplify our lives, right?  LOL  :D

---

### Post by Dr Watts On on 2012-03-05
*@dkolars*
Ahhh, I MISSED that (original install was Ubuntu)! So, the choice would be
" *Something else "  ? And then, if offered, choosing to repartition and reformat might provide the option of where to install Xubuntu? Yup, simple ... . Someday someone may make something for US not Themselves. I want my computer to be the tool, not me. Like you said, PIA!
Maybe better: install XFCE DE into your Ubuntu?
ALSO
I read in another thread about the 2 Desktops offered by the OS Xubuntu:
1: Xubuntu DE, and 2: XFCE . The "answer": the XFCE DE lacks some of the settings and artwork of Xubuntu! Ahhhh. So, if I see two cars, one a green Chevy and the other a red Toyota, and ask what is the difference between the two cars, (hopefully obvious I can SEE one is red and the other is green), the answer I get is "Well, one car is a green Chevy and the other is a red Toyota!" Gee, thanks! Are we having fun, or what?

---

### Post by dkolars on 2012-03-05
Yep, that's what I'm gonna do... re-partition, format, and install...  Actually, the X11.10 seems to be very nice... IT found my HP wireless immediately!!  And connected without me having to jump thru command line hoops!!  If for NO other reason, I'll install it!!  When I travel, it is always a nightmare to be able to connect using U10.10 and the HP laptop.  But, with the Live CD, it popped up the connection dialog box right away!  All I had to do was enter my pw, and bingo!

And, I discovered how to move the panels around, so I can make it look/behave as I want.  Will jump on that tomorrow...  today is working in the shop, tonight is music...

---

### Post by Dr Watts On on 2012-03-05
> **dkolars said:**
> And, I discovered how to move the panels around, so I can make it look/behave as I want.  Will jump on that tomorrow...  today is working in the shop, tonight is music...
[COLOR=Red]**HEY, dkolars! TELL ME TELL ME TELL ME!**[/COLOR] Or better yet give me a link if you found one. After reading the problem you had with it, I tried to move stuff around, really made a mess, and spent a while figuring out how to get it all returned to "normal" (The "Separator" on between Window Buttons and the other stuff had to be put back to "Expand", a totally new concept for me).
:popcorn:Enjoy the music tonight.

---

### Post by Dr Watts On on 2012-03-08
> **Dr Watts On said:**
> ... I still haven't scrubbed this  installation that offers 2 desktops at login. It is working so great I  think I'll just pass it to the end user, and when he asks me, I'll just  admit I don't know.
Quoting myself to keep previous promise re: results of vanilla  installation. My change of mind remains. I have had no discernible  problems with this. It runs great and basically I plan to put it on any  old computer with limited resources, that anyone wants me to work on.  Including if it has functional Windows.
I used to do that with Ubuntu. I guess I am a Xubuntu fanboy now! Even  though I still find it disconcerting, unable to find or figure out  exactly what the XFCE DE lacks that is in the Xubuntu DE.

Also found out when rebooting with my absolutely favorite tool of the  past several years PMAGIC, which I originally used to dd the drive, that  gparted no longer recognizes the swap partition, though the Xubuntu  does. I even installed gparted on this Xubuntu system. It's an older  version (pmagic uses the latest) and shows a black - "unknown" fs type.  Weird. When I had made the 2nd install of this Xubuntu system,
I had repartitioned and verified that it was swap when I quit pmagic. I  selected it as swap when installing Xubuntu, as well as made use of the  other partitions made by gparted in pmagic.
sda1 = / etc4
sda2 = extended
        sda5 = swap
        sda6 = /home
Now neither the newly installed version 0.8.1 gparted in Xubuntu nor the  latest 0.12.0 in pmagic see it, though from my cat /etc/fstab:
# swap was on /dev/sda5 during installation
#UUID=2946f61a-f255-47f5-94c6-87dc497478db none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0
NOTING: the UUID on swap was also # out. I don't want to screw up anything, so since "swapon -s"
shows
dan@Old-Tecra:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/mapper/cryptswap2                  partition    3068924    47272    -1
and I created the swap partition at 3 GB, I guess I should not try uncommenting the UUID.
So I am done here, though I plan to check back to see what's shakin.
And to see what dkolars ends up with.
Later, I'm outta here!
DrWattsOn

---

### Post by mikodo on 2012-03-08
> **Dr Watts On said:**
> Quoting myself to keep previous promise re: results of vanilla  installation. My change of mind remains. I have had no discernible  problems with this. It runs great and basically I plan to put it on any  old computer with limited resources, that anyone wants me to work on.  Including if it has functional Windows.
I used to do that with Ubuntu. I guess I am a Xubuntu fanboy now! Even  though I still find it disconcerting, unable to find or figure out  exactly what the XFCE DE lacks that is in the Xubuntu DE.
Here's the different packages:

[B][Meta-package for the Xfce Lightweight Desktop]("http://packages.ubuntu.com/oneiric/xfce4")
[/B] 
**[Xubuntu desktop system packages]("http://packages.ubuntu.com/oneiric/xubuntu-desktop")**

EDIT: Oh, I just looked back in this thread.** Krytarik**, I had forgotten, already posted these in, **Post #12**.

---

