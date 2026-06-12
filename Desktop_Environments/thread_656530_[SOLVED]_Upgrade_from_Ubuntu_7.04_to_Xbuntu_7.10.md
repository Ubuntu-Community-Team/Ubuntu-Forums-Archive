---
title: "[SOLVED] Upgrade from Ubuntu 7.04 to Xbuntu 7.10"
date: 2008-01-02
forum: Desktop Environments
---

### Post by Bruce M. on 2008-01-02
Hi Folks,

I'm getting ***ants-in-my-pants*** wanting to upgrade to Gutsy.  I heard/read that "Xbuntu" is a, how can I say this, "*slimmer*" version of Ubuntu and will run faster on older computers.

I'm running a P-III 800MHtz, no add-ons.  Sound, video and LAN built in, (Intel D815EEA motherboard) maxed out at 512MB RAM.  I would think this qualifies as an older computer.

Bringing this machine to Ubuntu from Windows 2000 Pro, was like a breath of life, it's faster, of that there is no doubt.  But Gutsy is a little more "power hungry", and while I'm *"almost"* sure it will run, that "cube" thingy (Compiz ?), I'm just as certain wont.

I still have some doubts.  Now, when I popped in the title for this thread, these popped up so, of course I read them, doesn't everybody?

1. [Xbuntu run faster then Ubuntu]("http://ubuntuforums.org/showthread.php?t=652234")

 - it runs the XFCE desktop environment and some different apps (which is what makes it lighter)

 XFCE ?? - I checked: from their site:
----------------
About Xfce

"Xfce is a lightweight desktop environment for various *NIX systems. Designed for productivity, it loads and executes applications fast, while conserving system resources." - Olivier Fourdan, creator of Xfce

Xfce 4.4 embodies the traditional UNIX philosophy of modularity and re-usability. It consists of a number of components that together provide the full functionality of the desktop environment. They are packaged separately and you can pick and choose from the available packages to create the best personal working environment.
------------------

Try installing xubuntu-desktop, see how it works out. Unless your computer is *really* old, the speed difference is not so big.

 - Now this is didn't know, I can install it "INTO" the Gnome version I have now.  Gives me a chance to "test drive" it.  I just might just do that too, if it's worth it.

2. [Xbuntu Gutsy 7.10 Upgrade ruined Perfect 7.04 install]("http://ubuntuforums.org/showthread.php?t=589320")

 - I have to take this as jusy one persons experience.  And hope mine will be different.

3. [Ubuntu to Xbuntu (Simple Question)]("http://ubuntuforums.org/showthread.php?t=516191")

 - The poster brings up a good point, that I can ask here too:  Can I keep everything in my home folder?
 - Obviously if I back it up, I'll have access to it.  But will it still be good in Xbuntu?

4. [Can I have both Ubuntu and Xbuntu on same box]("http://ubuntuforums.org/showthread.php?t=507008")

 - I already know that GRUB can duel, triple or more boots with various OS's.
 - Again it is suggested to get it through Synaptic and try it in this thread.

5, [Ubuntu/Xbuntu startup/shutdown]("http://ubuntuforums.org/showthread.php?t=228738")

 - This doesn't really relate to why I'm here but a cute read anyway.
---------------------

OK, here's the meat of what I'd like to know:

 1. If I download Xbuntu with Synaptic, does it "merge" with my Ubuntu that I'm running at present? (Obviously it'll be the 7.04 version)
 2. Is Xbuntu 7.10 going to be a a better choice for my old computer?
 3. Can I still run things like The GIMP, Inkscape, etc? (I'm learning with them)

Please post your opinions, thoughts and or ideas.
Who knows, maybe Ubuntu 7.10 will work with my computer.

Thanks for your time.
Bruce

---

### Post by p_quarles on 2008-01-02
1. Yes. At the login screen, you'll have to go to "options," select "session type," and then choose Xfce session. 
2. Not necessarily. 7.10 has some newer packages, but unless it has something that you specifically need, why upgrade? 
3. Yes.

---

### Post by Bruce M. on 2008-01-02
> 1. If I download Xbuntu with Synaptic, does it "merge" with my Ubuntu that I'm running at present? (Obviously it'll be the 7.04 version)
2. Is Xbuntu 7.10 going to be a a better choice for my old computer?
3. Can I still run things like The GIMP, Inkscape, etc? (I'm learning with them)

> **p_quarles said:**
> 1. Yes. At the login screen, you'll have to go to "options," select "session type," and then choose Xfce session. 
2. Not necessarily. 7.10 has some newer packages, but unless it has something that you specifically need, why upgrade? 
3. Yes.

 1. Interesting, I'll have to try this.
 2. Because someday I might want to go to 8.04. Hmmmm, I'm planning on a clean install.  So that makes sense.  Why?!?  Maybe it's just the "updated" programs.  The newer GIMP, Inkscape etc... { but do you really need them Bruce! } Probably not, but they would be nice ... dilemmas,  dilemmas ... time to think!
 3. Oh that is good news.  :)

I guess I should have asked one more Q:  Will my email be available?

NO!  Don't answer that, I'll try it and see, if not it's only a re-boot to Ubuntu.  :)

Because of 1 & 3, I'll postpone 7.10 for a bit.

Thanks
Bruce

---

### Post by p_quarles on 2008-01-02
True, GIMP 2.4 is a pretty big improvement over the one in the Feisty repos. Of course, you can always install that without upgrading the entire OS: [http://packages.ubuntu.com/gutsy/graphics/gimp](http://packages.ubuntu.com/gutsy/graphics/gimp)
Just grab the main package and its dependencies, and it shouldn't be too much trouble.

---

### Post by Bruce M. on 2008-01-02
> **p_quarles said:**
> True, GIMP 2.4 is a pretty big improvement over the one in the Feisty repos. Of course, you can always install that without upgrading the entire OS: [http://packages.ubuntu.com/gutsy/graphics/gimp](http://packages.ubuntu.com/gutsy/graphics/gimp)
Just grab the main package and its dependencies, and it shouldn't be too much trouble.

Whoa Nelly!

Are you saying I can use Gutsy programs in Feisty?

I remember once wanting to upgrade Firefox.  Think I had 6.04 or 6.10 (and Feisty was out at the time), and went to the Firefox site to get it.  It didn't work, don't ask why, I don't recall. So I made due until I got Feisty.

But this grabbing stuff from Gutsy's repos is a neat idea.

BTW, Xbuntu coming down as I type. Floating around 30 k/s, which is good for me.  :)

Any idea what this is?

```

Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done

```

or this one:

```

The following packages have been kept back:
  tzdata 
The following NEW packages will be installed:

```

Thanks p_quarles
Bruce

---

### Post by p_quarles on 2008-01-02
The "Duplicate" entry thing is probably easy to fix by editing your /etc/apt/sources.list file. If you want to post that here, I can tell you exactly what to change. 

tzdata = time zone data. That could be held back if you set your time zone manually, maybe?

---

### Post by Bruce M. on 2008-01-02
> **p_quarles said:**
> The "Duplicate" entry thing is probably easy to fix by editing your /etc/apt/sources.list file. If you want to post that here, I can tell you exactly what to change. 

tzdata = time zone data. That could be held back if you set your time zone manually, maybe?

Just finished eating, and going to watch a movie with my wife.  Came to tell you that Xbuntu is up and running.  Yup, faster too!

Will test more tomorrow and post /etc/apt/sources.list as well.

Goodnight and Thank you
Bruce

---

### Post by Bruce M. on 2008-01-03
> **p_quarles said:**
> The "Duplicate" entry thing is probably easy to fix by editing your /etc/apt/sources.list file. If you want to post that here, I can tell you exactly what to change. 

tzdata = time zone data. That could be held back if you set your time zone manually, maybe?

Got notified of a **tzdata** update last night - got it now.

If I read this correctly I see a few duplicates.  :(

```

#
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://ar.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

How safe is it to edit?  Looks like read only, will need sudo nano or gksudo gedit to edit.

Thanks,
Bruce

---

### Post by p_quarles on 2008-01-03
Safe as houses. The worst that could possibly happen is that you'd disable all repositories, and that would be simple to fix.

It looks like the only duplicate entry is the CD-ROM. Just comment out (using "#") two of those entries (or all three, if you don't want to use the CD as a repo), and run
```
sudo apt-get update
```
The duplicate entry warning should go away.

---

### Post by Bruce M. on 2008-01-03
> **p_quarles said:**
> Safe as houses. The worst that could possibly happen is that you'd disable all repositories, and that would be simple to fix.

It looks like the only duplicate entry is the CD-ROM. Just comment out (using "#") two of those entries (or all three, if you don't want to use the CD as a repo), and run
```
sudo apt-get update
```
The duplicate entry warning should go away.

Yup, done, warnings gone.

Thanks
Bruce

BTW, haven't played with Xbuntu yet today.  But will later, It looks a bit different and does seem to run a bit faster.  :)

---

### Post by p_quarles on 2008-01-03
> **Bruce M. said:**
> BTW, haven't played with Xbuntu yet today.  But will later, It looks a bit different and does seem to run a bit faster.  :)
I'm sure you'll like it. It's really not that much different from Gnome, and it's definitely a bit faster.

If want *real* speed, though, I'd recommend Fluxbox. It seems a bit intimidating to configure at first, but once you see how the configuration text files work, it's actually a breeze (i.e., much less complicated than Conky). My machine could run Vista (if I wanted to), but I still use Fluxbox because it improves the performance of all my applications by a noticeable amount.

---

### Post by Bruce M. on 2008-01-03
> **p_quarles said:**
> True, GIMP 2.4 is a pretty big improvement over the one in the Feisty repos. Of course, you can always install that without upgrading the entire OS: [http://packages.ubuntu.com/gutsy/graphics/gimp](http://packages.ubuntu.com/gutsy/graphics/gimp)
Just grab the main package and its dependencies, and it shouldn't be too much trouble.

Just checked this page out.
There are 30+ RED dots, 1 green and 4 blue.

How do I do this?
Just tried the first one, gimp-data, see image   :cry:

That's what happened with Firefox when I wanted to "upgrade" from the Firefox site, UBUNTU wouldn't allow it.  In fact even now, Firefox's upgrade feature is "*grayed out*".

Why does Ubuntu restrict out chances to upgrade programs? (but that is another thread I'll start later).

Bruce

---

### Post by Bruce M. on 2008-02-15
15 Feb 2008

Today was Install Gutsy Day. Chose not to install Xubuntu.

Ubuntu Gutsy 7.10 now up and running after a some research, two of which are below:

[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=684783](http://ubuntuforums.org/showthread.php?t=684783)
[*][http://ubuntuforums.org/showthread.php?t=656530](http://ubuntuforums.org/showthread.php?t=656530)
[/LIST]

I chose the Alt CD and installed 7.10 over 7.04 keeping my /home (different partition) intact (had a backup though) and everything went fairly well.

The Alt CD checked out OK, so I put:

sda5 - / - reformat
sda7 - /home - kept data
sda6 - /swap

First attempt had a hiccup, it failed the "Select and install software", but gave me the chance to try agin starting at that point.  So I did.

Second attempt was successful.

186 security updates later and I was reinstalling some of my programs:

[LIST=1]
[*]Thunderbird - all mail available
[*]jPilot - data intact
[*]conky
[*]curl
[*]lm-sensors
[*]Thunar
[*]Inkscape, and my one and only game;
[*]Wesnoth
[/LIST]

I finally got Gutsy!

---

### Post by newagelink on 2008-02-16
[COLOR="Navy"]I wish to update, and I have the disc ready, but first I want to backup my program data (bookmarks, emails, song ratings, etc.) [http://ubuntuforums.org/showpost.php?p=4345893&postcount=5](http://ubuntuforums.org/showpost.php?p=4345893&postcount=5)

What's the best way to do it?

EDIT: Sorry, I meant to post this post here: [http://ubuntuforums.org/showthread.php?t=580852&highlight=backup+home&page=154](http://ubuntuforums.org/showthread.php?t=580852&highlight=backup+home&page=154)[/COLOR]

---

