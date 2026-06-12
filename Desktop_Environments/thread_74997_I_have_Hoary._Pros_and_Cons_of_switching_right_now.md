---
title: "I have Hoary. Pros and Cons of switching right now, please!"
date: 2005-10-13
forum: Desktop Environments
---

### Post by TmP on 2005-10-13
Hi!
The long awaited release is here.
My question is: should or shouldn't I switch to Breeze when I have a well running Hoary. 

How soon do you suggest I should make the upgrade?
Should I go for a clean install or is it safe enough to apt-get?

Thanx

---

### Post by jlx on 2005-10-13
I have had some problems, but after fix them everything works great but 3d acceleration. 
The first problem I ran to was the path to the systems fonts. The new Ubuntu installs the fonts in /usr/share/fonts/ and my xorg.conf was configured with the path /usr/lib/X11/fonts (something like that). I change the xorg.conf to point to the new path and I was able to start xwindow. 
In repositories I can't find linux-restricted modules for the new kernel so I have no fglrx module and the system uses mesa drivers.
This time all the new elements I added to the menu didn't dissappear. Gnome 2.12.1 respect all your present configuration. 
You have to install language-pack-gnome(kde)-xx. This are the language packages. The first time you run Breezy, appears an icon in the notification area and give you post-update tips. ¡It's great!
After a few hours playing with the new release I recommend change totem to totem-xine (if you use totem) and install Deskbar Applet (look at [http://browserbookapp.sourceforge.net/deskbar-screencast.html]("http://browserbookapp.sourceforge.net/deskbar-screencast.html")) and for adding new engines (imdb, wikipedia, etc) you have to open firefox and click the search bar that come by default with firefox, there you have an option to add more search engines, a mozilla proyect web page opens and you can choose whatever engines you want. Then restart your deskbar applet  and you can use all the new search engines.
I have no more to share. I think Breezy it's amazing. Let's begin the Ubuntu new era :-)

---

### Post by kaktusztea on 2005-10-13
[QUOTE=jlx]
In repositories I can't find linux-restricted modules for the new kernel so I have no fglrx module and the system uses mesa drivers.
[/QUOTE]

Install **xorg-driver-fglrx** and then run **fglrxconf**. (Before that save your old xorg.conf file!)

---

### Post by madjo on 2005-10-13
[QUOTE=TmP]Hi!
The long awaited release is here.
My question is: should or shouldn't I switch to Breeze when I have a well running Hoary. 

How soon do you suggest I should make the upgrade?
Should I go for a clean install or is it safe enough to apt-get?

Thanx[/QUOTE]
I second the question :) (I mean, I would like to have an answer to these questions too, especially the last one) :)

---

### Post by BLTicklemonster on 2005-10-13
It's a mix for me. I've got both on separate hard drives. Breezy did better with my nvidia drivers; I see a splash screen while I'm booting that isn't there in Hoary, but I can't shoutcast to stream with streamtuner, dvds don't play correctly, I had to manually place the root terminal (can't even find terminal) in apps>sys tools, and a couple of other niggling things. Overall, Hoary was easier with that one exception of the video drivers, of course. But then Hoary was around a bit before I showed up, whereas Breezy is quite the newcomer. 

Can't wait to see what it is like as things begin to gell.

OVERALL IT IS STILL A MORE PLEASANT EXPERIENCE THAN THE FIRST TIME I TRIED INSTALLING AND USING WINDOWS... So yah, tis da bomb in my book. Keep it up Ubuntu Gods!!!

---

### Post by jatos on 2005-10-13
More pros, you can edit the gnome menu now.

Looks a lot nicer on the whole.

---

### Post by majikstreet on 2005-10-13
It's really your decsion. I've been on Breezy for a while before it was released, and I had few problems.


For now, I would avoid the rush. It's like slashdotting right now I bet.

---

### Post by Jade Robbins on 2005-10-13
Stupid slashdot :@

---

### Post by mokeyjoe on 2005-10-13
I've been wondering whether to upgrade too. So far I haven't come across any serious pros to upgrading. If Breezy could be installed and 'just work' from the start then I'd be tempted but as a new Linux user it took me ages to set up Hoary (and now automounting's stopped, grr) so I don't fancy going through all that configuration all over again right away. 

If I ran accross a problem I couldn't fix and I had to reinstall then I'd use Breezy. But for now I'll wait and see.

---

### Post by Wolki on 2005-10-13
It depends on how much you like cool, new stuff. It's full of little improvements that make the overall feel better, and more things are supported better. New Gnome is nice. Bugs are fixed (and new ones introduced, but that's the way of software development) I'd say go for it. At least if you're not in critical mission mode.

As for upgrade vs reinstall... If you can reinstall with little cost, it won't hurt. Updating should work without problems though; if you're not happy with the results you can still do a reinstall later.

---

### Post by graynotgrey on 2005-10-13
I have a 300 mhx G3 Apple iBook and a Pentium III 400MHz tower with a Nvidia TNT2 and Soundblaster Live card that I run Ubuntu on. Hoary ran fine and I had customized the configuration according to the unofficial Ubuntu Guide ([http://ubuntuguide.org)](http://ubuntuguide.org)). I first tested with the Live Breezy Preview CD a month ago and liked some of the new enhancements which are mostly  subtle ones, but there are many of them. Therefore I updated my sources.list (replace hoary with breezy)and executed the following two commands:

sudo apt-get update
sudo apt-get dist-upgrade

Afterwards I rebooted.

A couple problems I had on the P3 computer was with my Nividia drivers. 3D accelleration no longer worked and I had to restort to the 2d driver (nv). Old cards such as mine I later discovered are no longer supported by the newer Nvidia drivers, but there are nvidia-glx-legacy drivers available in the respositories. They did not work at first until I learned about the  nvidia legacy specific linux restricted modules. Once they were installed the Nvidia 3d driver works fine. 

There were some issues with Firefox multimedia plugins, but Breezy offers better support and more options. The easiest way to configure multi-media is to use Easy Ubuntu or Automatix ([http://ubuntuforums.org/showthread.php?t=66563)](http://ubuntuforums.org/showthread.php?t=66563)), an excellent graphical automated script utility that installs and configures many of the most popular items off of the unofficial Ubuntu guide. Mplayer works with many, but still not all streaming movie files I have tried.  

The iBook had no issues with the upgrade, except a couple restarts during the  upgrade process.

Since then I've installed Breezy on six Dell XPS Deminion PII 333MHZ desktop towers. The most significant issue with those machines were that the Yamaha OPL3SA card was not being automatically detected but I found a solution on the forums to quickly resolve that problem and sound worked fine afterwards.

In the end, I feel the pros outweight the cons. I've gone from warty to hoary to breezy without any serious issues. Apt-get is a wonderful package system and is the main reason I moved away from the RPM distributions (Red Hat, Fedora and Mandrake) which I found unecessarily frustrating and tedious to update although utilities like yum help, but apt-get along with Synaptic is much better. :smile:

---

### Post by mokeyjoe on 2005-10-13
How is the new GNOME different from the old one? 

You're the first person I've heard from who had no problems with the update. I guess that's the problem with forums - you generally only hear from people when they have problems!

---

### Post by snowjunkie on 2005-10-13
I simply used dist-upgrade as well and had no problems... I would advise that method over re-installing.

---

### Post by Wolki on 2005-10-13
[QUOTE=mokeyjoe]How is the new GNOME different from the old one? [/QUOTE]

A quick overview:

[http://www.gnome.org/~davyd/gnome-2-12/](http://www.gnome.org/~davyd/gnome-2-12/)

---

### Post by sickdude on 2005-10-14
installed a clean badger, used to have the hedgehog.

i think everybody should take the step as soon as possible it looks and feels great friendly user interface and no hardware crap or install crap

i made a fresh install on my server also a ex-hedgehog. and this works great to

so make the step and be amazed :D

---

### Post by TmP on 2005-10-14
Thank You!
You are amaizing. This forum itselfes could be the reason to switch to Ubuntu.

Please keep posting your views!
I think a lot of people will find it usefull.

Thanx again!:KS

---

### Post by TmP on 2005-10-17
It seems to me that the situation with Breezy is quite difficult.
Many people are finding it unsatisfactory.

Can anybody explain if the developement process of Breezy is finished or can I hope for an install version available for downloading with all the patches some time in the future? I hope that by popular demand the image will be upgraded with the final release of OpenOffce2. It would be such a shame having to download it separately.

Please keep posting your views!

Pros and Cons of switching to Breezy right NOW!

ThanX!

---

### Post by afonic on 2005-10-17
If you are 100% happy with your system, don't touch it. 

But if you like the impovements of Breezy (new Gnome, new kernel, x.org etc) and like to be in the edge, upgrading with apt-get should do it.

Bottom line, Breezy is much improved, but if someone is happy with his desktop, I don't really see the reason to upgrade as the changes are not THAT much. Hoary will also be supported with updates for at least a year more, so it is really your choice!

---

### Post by jdawdy on 2005-10-17
Keeping in mind I reinstalled, and didnt upgrade via apt, and that I am running an HP laptop (Ubuntu does very well on HP laptops), plus I use KDE installed onto Ubuntu (not the Kubuntu install disc)

MUCH better.  Here is a list off the top of my head of things that now workbetter:

Kaffeine doesnt crash nearly as much, or get cranky and not play any sound.
Kmail works much better.
Some annoying bugs in KDE have been fixed (Kmenu not saving was one)
Came with Openoffice 2 installed, so didnt have to muck around with that
Better support for my HP printer (used to have to print, shut printer off, turn back on, then click on "resume")
Firefox is recent, stable version

Cons:
Media codecs.  Nuff said.

---

### Post by polo_step on 2005-10-17
If it's not a stupid question, why not run 5.10 Live experimentally and see if it works better or worse than 5.04?

5.10 Live made some 5.04 problems of long standing go away for me because of later versions of applications, I suppose, and didn't crash anything, so I'm inclined to do a clean install of 5.10 on a new drive.  After seeing all the problems people are having after doing the upgrade to existing 5.04 systems, I don't think I want to try that.

Unfortunately, about the first real bug noticed in 5.10 just happens to be something I need to have right, an spca5xx driver to do a webcam upgrade I had in mind. :( 

How soon do incremental bugfix versions appear?

---

### Post by agger on 2005-10-17
[QUOTE=madjo]I second the question :) (I mean, I would like to have an answer to these questions too, especially the last one) :)[/QUOTE]

First of all: I switched from Hoary to Breezy, and everything is working fine for me. There's a bit more eye candy, but mostly everything is much the same.

I don't use OpenOffice a lot, so I don't really care whether it's one version of the other.

So, yes: breezy works fine, 

BUT: 

It's very similar to Hoary. Most of the "revolution" has happened back-stage, in the technical ins and outs we end-users don't have to worry about too much.

So if you have a well running Hoary, and there's not some new feature in Breezy that you actually need to have, then keep it - it's completely okay.
Of course, upgrading now will make the transition to the Drake easier, hwen that time comes.

As for apt-get vs. clean install: One of my friend got a completely clean dist-upgrade. For me, dist-upgrade failed because of conflicting Python packages (I think), so I had to do a fresh install. If I hadn't burned my /home to a DVD first, all data there would've been lost. So if you want to do a dist-upgrade, be prepared it might fail and have backup of all your data.

If your /home is on a separate partition, you don't have to worry about that, though.

---

### Post by plumcreek on 2005-10-17
[QUOTE=TmP]How soon do you suggest I should make the upgrade?
Should I go for a clean install or is it safe enough to apt-get?[/QUOTE]

I think it's safe to make the upgrade right now.

I've upgraded using both methods. On my tower at home I went for the clean install method because I was worried that I might have problems due to all of the tweaking I've done on it over the past 6 months. My /home directory is on a separate harddrive, so all I had to do was wipe out the boot drive and go. 

Very easy install. The new bootsplash is nice and I really appreciate all of the under-the-hood improvements. My home tower seems a bit faster than before, everything is nice and snappy.

On my work computer I went with the apt-get dist-upgrade method. I started it (using the instructions [here]("https://wiki.ubuntu.com/BreezyUpgradeNotes")) before leaving work on Friday and then checked on it (via VNC and ssh) a couple times over the weekend. It took a while, but it seemed to go ok. There were a couple hiccups due to some of the dozens of non-standard packages I've installed (using [Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563"), [haih]("http://www.ubuntuforums.org/showthread.php?t=22860"), alien, directions from [ubuntuguide]("http://www.ubuntuguide.org") , and of course -- compiling from source :cool: ). Overall though, the install process went very well. When I got into work this morning, my freshly installed Breezy system was here waiting for me (I'm using it to post this). 

I couldn't be happier with Breezy. I'm noticing all sorts of little things that keep improving my opinion of this release. Highly recommended in my book.

---

### Post by TmP on 2005-10-21
[QUOTE=polo_step]If it's not a stupid question, why not run 5.10 Live experimentally and see if it works better or worse than 5.04?
[/QUOTE]

It is a fact that LiveCD release tends to be much slower than the installed one. So I won't be able to compare the actual speed with a non fully-installed system.

Another thing is the stuff that i had installed. Will it work with my new ubuntu? No checking that without apt-get ( is it supposed to work or should I expect reinstalling from scratch?).

And lastly, since I have 256MB RAM ( I guess thats the reason ), the liveCD tends to freeze after some time - around an hour of intensive usage. It suddenly slows down while frantically reading something of the cd. Than it gets so annoingly slow that i simply have to boot. No checking the stablility that way.
:rolleyes: 

In the meantime, the OpenOffice2 is out.
And my previous qestion seems to have been anwsered: there will be no including the OO2 in the official download version of Breezy. It's not a very flexible policy. I find making rules that bind you silly. Its supposed to find its way into the repositories, but not anytime soon. On the other hand, people say that its ok to download the rpm, alien it and than install. And the final version isn't different from the pre-installed one except for some bug fixes.
Anyway the more stable the better...

What about weaker computers?
I'll be inheriting an old 700MHz desktop from my parents. It's going to be my primary download machine and a typewritter for my Girlfriend. Since Breezy seemes more gizmo-packed than Hoary, which one would you recommend?

Thanx for keeping this post alive!

---

### Post by wabble on 2005-10-21
Hibernation on laptops was better in hoary. I can't get it to work anymore. Or, atleast the hibernation works. It's just that when you boot up the computer hangs and stalls. Sweet.

On all other issues i think it's worth the upgrade :p

---

