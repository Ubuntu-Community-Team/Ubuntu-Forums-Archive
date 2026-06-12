---
title: "[SOLVED] Ubuntu Gaming"
date: 2008-03-13
forum: Gaming &amp; Leisure
---

### Post by doctorzeus on 2008-03-13
Ok Guys,

I'm sorry if this thread really annoys people because of my relatively new experiences with Ubuntu and linix (would you look at that I don't even know if I spelled it right!).

Ubuntu works just fine for all my work and stuff but I mostly use my PC for games. I very recently upgraded to Ubuntu thinking I could just find a compadability program for my windows games. 

I have seen about 3 other threads and know that the top 3 are really Cedega, Wine and Crossover. I tried Cedega and it didn't seem to work at all. I then tried Wine and I ended up with 2 different versions of wine waiting to be installed(which don't install) and I can't get rid of them. I am about to try crossover but if that doesn't work I'm going to feel like a real idiot for installing Linux over windows in the first place. 

I'm hoping someone is going to see this post and tell me what to do because I really am stuck with the whole terminal thing and all that.

Thanks

Doctorzeus.

---

### Post by ShodanjoDM on 2008-03-13
Have you installed the newest wine package?

This is the how to: 
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Anyway, can you be more specific about:

> I then tried Wine and I ended up with 2 different versions of wine waiting to be installed(which don't install) and I can't get rid of them?

In general, although the supports for Windows apps (including games, ofcourse) in Linux using Wine are getting better by each release, just don't expect it to run without some configuring or tweaking.

Oh btw, what games are you trying to play?

---

### Post by doctorzeus on 2008-03-13
Well according to this It says under versions I have installed:

0.9.57~winehq0~Ubuntu~7.10-1 (gutsy)

0.9.46-Oubuntu1 (gutsy)

(direct quotes)

I assume these are different versions and I try and force each version but they still don't work.

Doctorzeus.

(Yes I did install it from that exact website)

---

### Post by Tom--d on 2008-03-13
0.9.57 is the lastest version of wine. 

Dont you have it under Applications?

---

### Post by ShodanjoDM on 2008-03-13
Alright, could you post the output from both of these commands here?

```
aptitude search wine
```

and

```
aptitude show wine
```

And yes, as Tom--d wrote above, the 0.9.57 is the latest. It should overwrite the previous installed version.

---

### Post by doctorzeus on 2008-03-13
**_Here is the results for "aptitude search win_**e":

p   wine                            - Microsoft Windows Compatibility Layer (Bin
p   wine-dev                        - Microsoft Windows Compatibility Layer
(Dev
p   winefish                        - LaTeX Editor based on Bluefish      
[B][U]
and "aptitude show wine":[/U][/B]

p   wine                            - Microsoft Windows Compatibility Layer (Bin
p   wine-dev                        - Microsoft Windows Compatibility Layer (Dev
p   winefish                        - LaTeX Editor based on Bluefish            
dan@dan-laptop:~$ clear
dan@dan-laptop:~$ aptitude show wine
Package: wine
State: not installed
Version: 0.9.57~winehq0~ubuntu~7.10-1
Priority: optional
Section: otherosfs
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 53.7M
Depends: binfmt-support (>= 1.1.2), ia32-libs (>= 1.6), lib32asound2 (> 1.0.14),
         libc6-i386 (>= 2.6-1)
Suggests: msttcorefonts, xdg-utils
Conflicts: binfmt-support (< 1.1.2), winesetuptk, wine-doc, wine-utils,
           libwine-alsa, libwine-arts, libwine-capi, libwine-cms, libwine-esd,
           libwine-gl, libwine-gphoto2, libwine-jack, libwine-ldap, libwine-nas,
           libwine-print, libwine-sane, libwine-twain, xwine, libwine
Replaces: winesetuptk, wine-doc, wine-utils, libwine-alsa, libwine-arts,
          libwine-capi, libwine-cms, libwine-esd, libwine-gl, libwine-gphoto2,
          libwine-jack, libwine-ldap, libwine-nas, libwine-print, libwine-sane,
          libwine-twain, xwine
Description: Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 While Wine is usually thought of as a Microsoft Windows emulator, the Wine
 developers would prefer that users thought of Wine as a Windows compatibility
 layer for Linux. Wine does not require MS Windows, but it can use native system
 dll files in place of its own if they are available. 
 
 This package includes a program loader, which allows unmodified Windows
 binaries to run under compatible hardware.  This package also includes the
 library that implements the Wine project's free version of the Windows API,
 allowing successful running of programs ported directly from Windows. 
 
 Homepage: [http://www.winehq.org/](http://www.winehq.org/)

(A bit long sorry)

Thanks 

Doctorzeus.

---

### Post by doctorzeus on 2008-03-13
[B][I][U](To Tom--d)
[/U][/I][/B]

Yes it is under add/remove but it doesn't do anything when I click on it.

Doctorzeus

---

### Post by Tom--d on 2008-03-13
Uninstall it. Do it in Synaptic Packet Manager. Do a complete removal.

Install it through Add/Remove. 

See what happens after that.

---

### Post by lespaul_rentals on 2008-03-13
> **doctorzeus said:**
> I am about to try crossover but if that doesn't work I'm going to feel like a real idiot for installing Linux over windows in the first place.

Linux is not the place for gamers.  There are some great native Linux games like Urban Terror (my second favorite PC game of all time) but you can't switch to Linux thinking that you will be able to use wine, Cedega, Crossover, or anything else to play Windows games.

---

### Post by doctorzeus on 2008-03-13
I can't install it though! 

Thats my problem.

Doctorzeus

---

### Post by compiledkernel on 2008-03-13
> **lespaul_rentals said:**
> Linux is not the place for gamers.  There are some great native Linux games like Urban Terror (my second favorite PC game of all time) but you can't switch to Linux thinking that you will be able to use wine, Cedega, Crossover, or anything else to play Windows games.

Actually the correct assessment is that you shouldnt switch to linux for gaming without understanding there is a learning curve and some effort involved in playing games via Wine and other such implementations. Its not hard, but its not just insert CD and go either.

---

### Post by doctorzeus on 2008-03-13
**_(FOR lespaul_rentals)_**

Uh sorry but why not?

---

### Post by doctorzeus on 2008-03-13
***_ (For compiledkernel)_***

I'm quite happy to tinker with the games to make them work, I know how to use windows and its commands well but the time I've been tinkering (24hr+) is not really acceptable.

Doctorzeus

---

### Post by ShodanjoDM on 2008-03-13
> Package: wine
State: not installed
Version: 0.9.57~winehq0~ubuntu~7.10-1

It's not installed?

Hmm... How about using synaptic? Does it shows that wine is installed?

Anyway, the command output shows that you have only one version in the repository.

Try this:

```
sudo aptitude install wine
```

and if it fails, post the output here again.

---

### Post by doctorzeus on 2008-03-13
> **ShodanjoDM said:**
> It's not installed?

Hmm... How about using synaptic? Does it shows that wine is installed?

Anyway, the command output shows that you have only one version in the repository.

Try this:

```
sudo aptitude install wine
```

and if it fails, post the output here again.


It shows it is not installed and it has conflicts when I try, I just tried what you asked me to do, here is what it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  ia32-libs wine 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.1MB of archives. After unpacking 133MB will be used.
The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 which is a virtual package.
             Depends: libc6-i386 (>= 2.3.6-2) which is a virtual package.
             Depends: lib32z1 which is a virtual package.
             Depends: lib32stdc++6 which is a virtual package.
             Depends: lib32asound2 which is a virtual package.
             Depends: lib32ncurses5 which is a virtual package.
  wine: Depends: lib32asound2 (> 1.0.14) which is a virtual package.
        Depends: libc6-i386 (>= 2.6-1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
:confused:

Doctorzeus

---

### Post by compiledkernel on 2008-03-13
> **doctorzeus said:**
> ***_ (For compiledkernel)_***

I'm quite happy to tinker with the games to make them work, I know how to use windows and its commands well but the time I've been tinkering (24hr+) is not really acceptable.

Doctorzeus

I can admire your chutzpah DZ. 

Its a matter of choice really. Im a linux nerd, ill tinker getting whatever Im playing to run. I dont have an issue with it. I say that however, and with no great level of certainty I know that a gamer who just picks up linux and expects it to play his windows titles is an uninformed gamer. 

If your going to embrace Wine, please refer here for some pertinent info that needs to be read. 

[http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

---

### Post by ShodanjoDM on 2008-03-13
> **doctorzeus said:**
> 
The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 which is a virtual package.
             Depends: libc6-i386 (>= 2.3.6-2) which is a virtual package.
             Depends: lib32z1 which is a virtual package.
             Depends: lib32stdc++6 which is a virtual package.
             Depends: lib32asound2 which is a virtual package.
             Depends: lib32ncurses5 which is a virtual package.
  wine: Depends: lib32asound2 (> 1.0.14) which is a virtual package.
        Depends: libc6-i386 (>= 2.6-1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

That's strange. Too many unresolved dependencies... Just curious here, are you using 64 bit Ubuntu?
Anyway, Here's a portion of my output, edited for easier read:

> Package: wine
State: installed
Automatically installed: yes
Version: 0.9.57~winehq0~ubuntu~7.10-1
Priority: optional
Section: otherosfs
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 53.5M
Depends: 
binfmt-support (>= 1.1.2),
libasound2 (> 1.0.14),
libaudio2,
libaudiofile0 (>= 0.2.3-4), 
libc6 (>= 2.6-1), 
libesd-alsa0 (>= 0.2.35)  | libesd0 (>= 0.2.35),
libgl1-mesa-glx | libgl1, 
libglu1-mesa | libglu1, 
libgphoto2-2 (>= 2.4.0),
libgphoto2-port0 (>= 2.4.0)

...


You can see there are no lib32 such as lib32asound2 in your output, but there is a libasound2 in mine.

---

### Post by doctorzeus on 2008-03-13
> **compiledkernel said:**
> I can admire your chutzpah DZ. 

Its a matter of choice really. Im a linux nerd, ill tinker getting whatever Im playing to run. I dont have an issue with it. I say that however, and with no great level of certainty I know that a gamer who just picks up linux and expects it to play his windows titles is an uninformed gamer. 

If your going to embrace Wine, please refer here for some pertinent info that needs to be read. 

[http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

***_[I]Ok Thanks.*_[/I]**

---

### Post by doctorzeus on 2008-03-13
> **ShodanjoDM said:**
> That's strange. Too many unresolved dependencies... Just curious here, are you using 64 bit Ubuntu?
Anyway, Here's a portion of my output, edited for easier read:



You can see there are no lib32 such as lib32asound2 in your output, but there is a libasound2 in mine.

Yes I believe I am using 64bit, But I really don't see why it would effect it.

Any Idea whats going on?

Thanks

Doctorzeus

---

### Post by Twitch6000 on 2008-03-13
> **doctorzeus said:**
> Yes I believe I am using 64bit, But I really don't see why it would effect it.

Any Idea whats going on?

Thanks

Doctorzeus

computing...word found....64bit...Problem Found :p.
O sorry I like doing that anyways,if you are using the 64bit version make sure you are able to run 64bit first.If you can then look at that list for the dependencies.

---

### Post by doctorzeus on 2008-03-13
> **Twitch6000 said:**
> computing...word found....64bit...Problem Found :p.
O sorry I like doing that anyways,if you are using the 64bit version make sure you are able to run 64bit first.If you can then look at that list for the dependencies.


I've always used 64 bit on windows so yes I should be able too.

Doctorzeus

---

### Post by doctorzeus on 2008-03-13
Ok

I have used Windows all my life up until now.The speed and the timing of Lynx along with the amount of customization you can do to it is great but right now i'm not exactly impressed with others (someones gonna kill me for going into a lynx devoted site and saying it's not that great but oh well).

I've also found I can't do some rather basic things like flash player and my sound is not working but I won't discuss them in this thread because it is long enough already.

I appreciate everyones help and all but unless someone can convince me otherwise I may go back to windows because of the problems.

Ill keep trying for a couple of days more but I am having second thoughts about Lynx.#-o

Ok, help me solve this everyone cause I really need to.

Thanks

Doctorzeus.

---

### Post by doctorzeus on 2008-03-13
----------------------------------------------------------------------------

---

### Post by lespaul_rentals on 2008-03-13
> **doctorzeus said:**
> Ok

I have used Windows all my life up until now.The speed and the timing of Lynx along with the amount of customization you can do to it is great but right now i'm not exactly impressed with others (someones gonna kill me for going into a lynx devoted site and saying it's not that great but oh well).

I've also found I can't do some rather basic things like flash player and my sound is not working but I won't discuss them in this thread because it is long enough already.

I appreciate everyones help and all but unless someone can convince me otherwise I may go back to windows because of the problems.

Ill keep trying for a couple of days more but I am having second thoughts about Lynx.#-o

Ok, help me solve this everyone cause I really need to.

Thanks

Doctorzeus.

To the others in this thread:  I saw this coming, and that was the reason for my earlier post.

We've already told you that you can't expect to get all your Windows games to play on Linux.  I'm lucky if I can get 25% of my software to run.  wine and all the others are great applications but I didn't take up Linux because I wanted to be a 1337 hax0r and brag about how I can play Halo on Linux.  I took it up because I wanted to learn more about computers, and Linux allows for amazing configuration and customization, far beyond what Windows ever allowed.

We've also already told you that 64-bit Linux is not 100% perfect yet.  Many people initially have problems with 64-bit that can be worked through, but it takes patience and a willingness to learn.  You have complained about having to try to get your game to play in wine for just 24 hrs.  Sorry buddy, but people who use Linux understand that many hours can be spent attempting to fix problems.  It's part of the Linux lifestyle, one that we find rewarding.

I'm not going to waste my time trying to convince you to stay.  You came in here with a totally different opinion of Linux than what it really is.  Sorry you didn't like your time here.  You're always welcome to come back when you're willing to exhibit patience.  See ya.

---

### Post by KhaaL on 2008-03-13
doctorzeus, my advice is to install the i386 architecture until you're more proficient with linux. I've just recently switched to 64bit linux and I've been using a 64bit CPU 2 of the 3 years i've been running linux!

Regarding games, appdb is your friend. get to know wine well and neat commands like *wineprefixcreate*. Once you feel more comfortable, I'm sure you'll be able to game on linux pretty sucessfully.

Good luck :)

---

### Post by AgentZ86 on 2008-03-13
> **doctorzeus said:**
> Ok

I have used Windows all my life up until now.The speed and the timing of Lynx along with the amount of customization you can do to it is great but right now i'm not exactly impressed with others (someones gonna kill me for going into a lynx devoted site and saying it's not that great but oh well).

I've also found I can't do some rather basic things like flash player and my sound is not working but I won't discuss them in this thread because it is long enough already.

I appreciate everyones help and all but unless someone can convince me otherwise I may go back to windows because of the problems.

Ill keep trying for a couple of days more but I am having second thoughts about Lynx.#-o

Ok, help me solve this everyone cause I really need to.

Thanks

Doctorzeus.


Have you tried playing your windows games on a mac perhaps that would be more interesting for you.

I understand you want to try linux, but to jump right in and want to use it to play windows games. ? your just not going to have the best experience with it. It's like people who want their diesel vehicle to run off vegi oil. You just can't dump vegi oil in there you have to do a few things. like filter the oil, and perhaps even create a heat tank in order for the vegi oil to work properly, then after your run the engine, you have to switch back to bio diesel or regular diesel again for and idle the engine for about 5 min. so you don't clog the injectors. Because veggi oil is different then diesel and you can't just run it in a diesel engine, unless some modifications are made to accommodate the difference in fuel.

Same with linux and mac etc. Or any other type of incompatibility topic.

Basically Linux can be adapted to run many windows things, however will it run your windows things ? well each thing is different and requires a different tweak, and Linux has been striving to be multiplatform compatible and is in most cases, but yet it's still lacking in the gameage area in many cases. but not all. 

So I hope this clears things up a bit, I would personally just dual boot to windows when playing games and boot to linux for everything else, while your tweaking your linux system and trying to get your games to work on linux.

Cedega should help, and also wine might help, one thing I do with wine under the configuration setting.(configure wine) and under the Graphics Tab, I uncheck the selection which says: Allow windows manager to control the windows(leave this unchecked) I've had better luck with this and the windows will emulate it's own behaviour and not try to coordinate with your behaviour of your desktop. Just FYI

I'm playing StarTrek Armada 1, and StarTrek Armada 2 with Wine which are windows games, and then work well.
I'm lacking some keyboard shortcut functionality, but I can deal with that. The game action is still nice.


I even use my linux computer for trading currency now, even though there are a lot more options for me with windows, but I just don't want the hassle in windows. There are many other associated windows problems that have to be dealt with.

However windows will not run my linux programs either. but even if it did, windows still has it's own problems that I can't accept.

Happy hacking

---

### Post by Sammi on 2008-03-13
Even though I have been a maintainer of the Ubuntu/Wine/WoW guide (link: [http://ubuntuforums.org/showthread.php?t=579378]("http://ubuntuforums.org/showthread.php?t=579378")) for some time, I still dual-boot Windows for games, that don't work well in Linux.

Windows games are made to work in windows, and it's a miracle that Wine is able to run any of them on Linux at all - even though it runs some of them very well.

But anyway, your problem seems to be that Wine doesn't want to play nice with your 64 bit Ubuntu installation. I recommend that you install 32 bit Ubuntu and give that a try.

---

### Post by doctorzeus on 2008-03-14
Ok Thanks.

I will try the stuff you guys have recomended. Thanks for clearing it all up for me.

Doctorzeus

---

