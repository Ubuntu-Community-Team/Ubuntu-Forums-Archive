---
title: "Firefox uses WAY TOO MUCH RAM (~1GB!)"
date: 2009-01-09
forum: General Help
---

### Post by sgissinger on 2009-01-09
Hi all.
I'm tired of Firefox (Mozilla/5.0 (X11; U; Linux i686; fr; rv:1.9.0.5) Gecko/2008121621 Ubuntu/8.04 (hardy) Firefox/3.0.5) eating all my memory, it has recently caused my system a major momentary slow down. I first thought it was because I was surfing Deezer.com (uses flash and flash is pretty slow under ubuntu), so I closed  the tab, but it kept using ram : around 990Mb:confused::confused:! I finally disabled some useless add-ons like showcase, restarted Firefox, and everything was back to normal : Firefox uses 3 to 5 percents of my 2GB of RAM.
My question is : How can I configure Firefox not to use more than a certain amount of RAM? Is there a way to configure it so it uses less RAM?
Thanks

---

### Post by skwon11 on 2009-01-09
Thank you for posting this... I have the same problem.  Looking forward to the responses.

---

### Post by sgissinger on 2009-01-12
Please anyone?

---

### Post by hyperdude111 on 2009-01-12
Most apps based on mozilla generally use large amounts of RAM, firefox, songbird, thunderbird ect... but specifics can depend on what you are doing.
Watching flash videos makes any browser use up more memory and all the info in your tabs, images too are quite large. This is because firefox stores all the info on your web page in the RAM to make it load faster then when you navigate away it is moved to the temporary storage if you go there again. 

There are some browsers that use far less resources but they are usually worse looking, slower and have less functions. The big plus of firefox is addons which are not present anywhere else.

If you want the other main browsers are.
Flock
Galeon
Opera
Iceweasel - Basically firefox
and for windows IE and Safari

Hope this helps.

---

### Post by WitchCraft on 2009-01-12
For Debian lenny, a funny solution is this:
```

su root
mkdir /root/Desktop/repo/dists/lenny/main/binary-i386
cd /root/Desktop/repo/dists/lenny/main/binary-i386
wget [ftp://mirror.switch.ch/mirror/opera/linux/963/final/en/i386/opera_9.63.2474.gcc4.qt3_i386.deb](ftp://mirror.switch.ch/mirror/opera/linux/963/final/en/i386/opera_9.63.2474.gcc4.qt3_i386.deb)

echo "#local repository" >> /etc/apt/sources.list
echo "deb file:///root/Desktop/repo lenny main" >> /etc/apt/sources.list
echo "deb-src file:///root/Desktop/repo lenny main" >> /etc/apt/sources.list

apt-get update
apt-get install opera_9.63.2474.gcc4.qt3_i386

```

or for the RTLD_LAZY:
```

cd ~/Desktop
wget [ftp://mirror.switch.ch/mirror/opera/linux/963/final/en/i386/opera_9.63.2474.gcc4.qt3_i386.deb](ftp://mirror.switch.ch/mirror/opera/linux/963/final/en/i386/opera_9.63.2474.gcc4.qt3_i386.deb)
dpkg -i opera*.deb
opera

```


and yet another solution is:
```

echo "#swiftfox" >> /etc/apt/sources.list
echo "deb http://getswiftfox.com/builds/debian unstable non-free" >> /etc/apt/sources.list
apt-get upgrade

apt-cache search swiftfox
swiftfox-athlon-xp - lightweight web browser based on Mozilla
swiftfox-athlon64-32bit - lightweight web browser based on Mozilla
swiftfox-i686 - lightweight web browser based on Mozilla
swiftfox-pentium-m - lightweight web browser based on Mozilla
swiftfox-pentium3 - lightweight web browser based on Mozilla
swiftfox-pentium3m - lightweight web browser based on Mozilla
swiftfox-pentium4 - lightweight web browser based on Mozilla
swiftfox-prescott - lightweight web browser based on Mozilla

apt-get -y install swiftfox-pentium4
swiftfox

```

---

### Post by daprofessor on 2009-01-12
List the add-ons you have installed, some add-ons use much ram, I haven't had it use that much ram though.

I have 9 add-ons and a theme and I'm using  about 175MB of ram.

---

### Post by WitchCraft on 2009-01-12
> **daprofessor said:**
> List the add-ons you have installed, some add-ons use much ram, I haven't had it use that much ram though.

I have 9 add-ons and a theme and I'm using  about 175MB of ram.

no seriously, a browser that needs more than 100 MB RAM with just one tab open is serious crap.
Opera can have 20+ open tabs (including youtube videos), and only needs appx 102 MB...
I remember my arachne web browser on dos. It run on a OS that had 16 MB RAM total!

Install opera, it's the fastest and technically the most correct and usable browser.
But still, opera can't beat Kazehakase Web Browser (19.5 MB)

Or install swiftfox, it's like firefox, just more leightweight, and just that the latest bugs are fixed and replaced with new ones...

---

### Post by daprofessor on 2009-01-12
I don't know what to tell you, I have used Firefox for years and haven't had the ram issues you are, yes Firefox uses quite a few resources, but always less than 200MB in Linux and around 250MB in Windows, have you tried uninstalling, removing all files and re-installing???

---

### Post by NT4usB on 2009-01-13
Removing and reinstalling won't get you anywhere.
Renamng the (hidden folder) .somethingfirefox folder in your home folder, then creating a new profile might.
And/or, get the adblock, flashblock, and noskript extension and run those. They go a long way to reducing Firefox overhead.
fwiw, Firefox is better than it used to be. Time was, Firefox would use more memory on my work box than SolidWorks, ProE, MechanicalDesktop, or any of the other CAD software I run.
Didn't slow anything down, just sucked...

---

### Post by airjaw on 2009-01-14
My Firefox is currently using 245MB RAM, but I have seen it go as high as 500MB quite often.  I suspect that when it goes to 500MB it is a bug.  Firefox has always been buggy in Ubuntu for me.
Also, sometimes after you close firefox, there will still be a firefox process running (and usually taking up 500MB Ram for me) and you' have to manually kill it.

FYI I usually have two firefox windows open with out 10-15 tabs each and youtube videos playing. I think 250MB RAM is probably about right.

---

### Post by Famicommander on 2009-01-14
I suggest using Opera. On every computer I've tried it on, it's been faster, more stable, more capable, and less resource intensive than Firefox or Chrome.

---

### Post by cb34 on 2009-01-14
[http://www.tweakfactor.com/articles/tweaks/firefoxtweak/4.html](http://www.tweakfactor.com/articles/tweaks/firefoxtweak/4.html)

see if anything in here helps you. there's some tweaks for mem, but not sure if it is referring to the ram mem.

my iceweasel is super fast after tweaking it a bit.

ther is a program cpulimit.. maybe try to look for a ramlimit type of program...??

(opera has its own issues, and iMO it sucks.)

---

### Post by sgissinger on 2009-01-16
Thanks for all these helpful answers.
I think I'm ready to pay the price of a relatively unstable browser, just for its awesome addons : I have installed the classic compact theme, firebug, fast video downloader, user agent switcher, world reference + google translator, web developer, measure it, gtranslate, fire ftp, gmail space, hots.ip geolocation plugin, unclosed tabs button, tab counter and .com url fixer. They are all pretty useful and I don't think they cause my RAM problem. Right now, it uses arounf 90Mb...

---

### Post by sgissinger on 2009-01-16
And thanks for suggesting opera, i find it too windows-like but it seems it is indeed the best alternative. I had already installed it on my system but I only use it to check website compatibility.

---

### Post by nonoitall on 2009-01-22
There's definitely something seriously wrong with Firefox on Ubuntu.  All I need to do is open it (with *no* extensions, no less) and leave it running for less than an hour.  Poof!  My system slows to a crawl with massive swapping going on.  I don't even have to be using Firefox - it can just be minimized while I'm watching a DVD or doing office work.  But somehow, it manages to gobble up 700+ MB of memory.  (This just isn't acceptable for a laptop with 1 GB of RAM, with part of it reserved for the IGP.)

It's really weird too, because I've never experienced this on Windows at all, or even on Ubuntu up to a few months ago.  I'm giving Swiftfox a shot though, and for the moment it seems to be performing well.  (If it doesn't pull through, I shudder to think that I might actually switch from Ubuntu back to Vista in order to *save memory*. :()

---

### Post by grndslm on 2009-01-22
Have you tried saving your bookmarks (apparently you don't have any extensions) and then deleting the .mozilla folder in your home directory??

---

### Post by nonoitall on 2009-01-23
Well Swiftfox indirectly led me to the solution.  The problem (at least for me) doesn't appear to be Firefox itself, but rather a very common plugin:  Flash.

Swiftfox didn't suffer from any of the memory hogging problems that Firefox did, but there was one little peculiarity:  Swiftfox wasn't using Firefox's Flash plugin.  I'd been wanting to try out the new 64-bit Flash plugin anyway, so I ditched the old 32-bit plugin and its wrapper and manually installed the 64-bit plugin.  It still did not work with Swiftfox, but it did in Firefox, and surprise, surprise - Firefox's memory usage hasn't gone out of control since.

Obviously, this would only be a solution if you're running 64-bit Linux.  I loosely followed [these instructions]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml") to remove the old plugin and install the new one.  Hope this helps someone else.

---

### Post by seenxu on 2009-01-25
swiftfox is not in active development anymore!

Go have a look of swiftweasel, they have the latest pgo optimized ff 3.0.5, and no problem with flashplayer and mplayer plugins. At least in my case, after using swiftweasel 3.0.5, the ram usage(with seven addons) is between 260mb-330mb, on the contrary, ram usage of firefox 3.0.5 varied between 200mb till 1200mb, it is horrible! 

I'd strongly recommend everyone who has ff ram usage problem go with swiftweasel or compile your own pgo optimized firefox.

PS:
my ram usage conclusions both are based on freshly created profile, newly installed addons.

---

### Post by binbash on 2009-01-25
firefox 3.1b uses less ram than 3.0x

---

### Post by OrangeCrate on 2009-01-25
As you discuss this, please remember that Linux utilizes RAM differently than what you were accustomed to on Windows...

**Linux Memory Management or 'Why is there no free RAM?'**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by shinobi2539 on 2009-02-15
In fact, even if you are not watching flash movies... it EATS too much RAM!!!... i was just reading facebook in one window with just one tab... and there were 134MB RAM just for Facebook? wtf???!!!

I was thinking if the problem are my bookmarks and installed plugins, I just started deleting some, but the problem still there... if anyone knows the answer to this, please! post it I'll thank U a lot!!!

Alex Ochoa

---

### Post by seenxu on 2009-02-15
> **shinobi2539 said:**
> In fact, even if you are not watching flash movies... it EATS too much RAM!!!... i was just reading facebook in one window with just one tab... and there were 134MB RAM just for Facebook? wtf???!!!

I was thinking if the problem are my bookmarks and installed plugins, I just started deleting some, but the problem still there... if anyone knows the answer to this, please! post it I'll thank U a lot!!!

Alex Ochoa

try to create a new empty/clean profile, you will see the difference.

---

### Post by Sukarn on 2009-05-24
> **OrangeCrate said:**
> As you discuss this, please remember that Linux utilizes RAM differently than what you were accustomed to on Windows...

**Linux Memory Management or 'Why is there no free RAM?'**



[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

The page you link to describes the typical usage of RAM, and how RAM is handled by the Linux kernel. This does not affect how much RAM a given program uses at a given point of time, unless the maximum capacity of RAM was reached (the point where swapping or disposing of data takes place on Linux).

This rarely happens when a machine has 4 GB of RAM, and is used for casual browsing/video/music (not any professional video editing or , but it still appears that firefox is capable of reaching ~1 GB of RAM. I have experienced this myself on a machine with 2 GB RAM where firefox reached ~1 GB of RAM while typing on facebook. I closed and re-opened firefox to find that it was now using ~80 MB of RAM.

I've had firefox slowing my system to a crawl and causing swapping my a desktop with 512 MB of RAM, running Debian Lenny (stable), where the OS with desktop environment seems to take ~100 MB, whereas firefox alone while typing and chatting on facebook reached ~800 MB and caused major swapping and slowdowns until I end the process (close firefox) and re-open it.

I fail to understand how firefox's RAM usage jumps to such huge numbers while browsing certain websites.

What we are talking about in this thread is the huge amounts of RAM that can be occupied by firefox on some machines, not how the kernel manages RAM or caches data or any other kernel and RAM related thing.

---

### Post by MB94128 on 2010-10-17
My suspicion is that the JavaScript interpreter used by Mozilla Tribe browsers (FF / SM / Nav. / etc.) may be a RAM pig. This is based on having RAM bloat when visiting sites that use a lot of JS (e.g. comment managers at the bottom of an online newspaper article). I've had problems with FF's 1.x, 1.5.x, 2.x and SeaMonkey 1.1. 

The solution I use is to have multiple configurations (my start-up options for FF 2 are "-ProfileManager -no-remote" + SM 1.1 is "-SelectProfile"). I run Flash games and content out of one profile to avoid lockups (I've had hangs with my third Flash use in a session and on exit), lean content in a second (basic HTML + light JS), and JS pigs in a third. 

Tar Baby Dept. - Beware of having too many bookmarks (hundreds are okay, thousands will drag) and too fat of a download log (tens are okay, hundreds will drag). Also, the Download Manager should be either hibernating or tabbed (I use the "Download Manager Tweak" extension). Jack-in-the-box mode has had a noticeable impact on my laptop (2GB RAM, ~2GHz clock). A former workstation (PIII-600) was what prompted me to first use the DM tweak.

NB - FlashBlock is installed in my FF 2, Nav.9, and SM 1.1 (chrome).

P.S. I'm not using FF 3 or later due to my preference for "bookmarks.html".

---

### Post by sendblink23 on 2010-10-17
> **MB94128 said:**
> My suspicion is that the JavaScript interpreter used by Mozilla Tribe browsers (FF / SM / Nav. / etc.) may be a RAM pig. This is based on having RAM bloat when visiting sites that use a lot of JS (e.g. comment managers at the bottom of an online newspaper article). I've had problems with FF's 1.x, 1.5.x, 2.x and SeaMonkey 1.1. 

The solution I use is to have multiple configurations (my start-up options for FF 2 are "-ProfileManager -no-remote" + SM 1.1 is "-SelectProfile"). I run Flash games and content out of one profile to avoid lockups (I've had hangs with my third Flash use in a session and on exit), lean content in a second (basic HTML + light JS), and JS pigs in a third. 

Tar Baby Dept. - Beware of having too many bookmarks (hundreds are okay, thousands will drag) and too fat of a download log (tens are okay, hundreds will drag). Also, the Download Manager should be either hibernating or tabbed (I use the "Download Manager Tweak" extension). Jack-in-the-box mode has had a noticeable impact on my laptop (2GB RAM, ~2GHz clock). A former workstation (PIII-600) was what prompted me to first use the DM tweak.

NB - FlashBlock is installed in my FF 2, Nav.9, and SM 1.1 (chrome).

P.S. I'm not using FF 3 or later due to my preference for "bookmarks.html".

last Post MAY 2009

stop reviving old threads :P

---

