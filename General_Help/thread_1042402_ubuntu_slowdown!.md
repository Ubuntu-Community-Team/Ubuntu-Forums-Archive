---
title: "ubuntu slowdown!"
date: 2009-01-17
forum: General Help
---

### Post by LeadHop on 2009-01-17
This has been driving me nuts lately - ubuntu's been progressively been slowing down with each update.  the biggest problem so far is firefox - given that i have multiple tabs and windows open, i've never had this problem with windows xp with even more tabs and windows. I understand how adobe hasn't been quite been kind to linux users so i've come to terms with how anything flash-related is laggy.

Up to this point I thought it was because i had a small partition and a small swap space. (8gb and 500mb, respectively), but i recently increased the partition to 32gb and 1.5 gb and it hasn't gotten much better.  this entire post was written with a lag of several seconds between keys typed and showing up on the screen.  my machine is a bit old - 4 years, 1.6ghz.

is there anyway to work around this?  i'd rather avoid having to save the home file and reinstall method.  TIA!

---

### Post by Hendrixski on 2009-01-17
Yeah, I noticed that it slows down too...
So what I just did was switch to Xubuntu.  It's worth a try:  just sudo apt-get install xubuntu-desktop.

---

### Post by jerome1232 on 2009-01-17
> **LeadHop said:**
> This has been driving me nuts lately - ubuntu's been progressively been slowing down with each update.  the biggest problem so far is firefox - given that i have multiple tabs and windows open, i've never had this problem with windows xp with even more tabs and windows. I understand how adobe hasn't been quite been kind to linux users so i've come to terms with how anything flash-related is laggy.

Up to this point I thought it was because i had a small partition and a small swap space. (8gb and 500mb, respectively), but i recently increased the partition to 32gb and 1.5 gb and it hasn't gotten much better.  this entire post was written with a lag of several seconds between keys typed and showing up on the screen.  my machine is a bit old - 4 years, 1.6ghz.

is there anyway to work around this?  i'd rather avoid having to save the home file and reinstall method.  TIA!

That's pretty bad... How much ram do you have, what video card do you have?

Can you post the out put of free?
```
free -m
```

be sure to wrap the output in [noparse]```
code tags
```[/noparse] to make the output readable.

---

### Post by LeadHop on 2009-01-17
thanks everyone!  Here's what i'm getting:

```
 total       used       free     shared    buffers     cached
Mem:          1001        926         75          0         21        236
-/+ buffers/cache:        667        333
Swap:            0          0          0

```

I've been considering switching from ubuntu to debian or xubuntu, but i'd prefer staying on ubuntu...

---

### Post by jerome1232 on 2009-01-17
hmm 1 GB of ram is plenty of ram, and your barely using any of it (667 MB of ram free), so my next guess would be video related, what graphics card are you using, what driver are you using and are you using compiz or metacity for your window manager?

If you run top what's eating the most cpu/mem, xorg? firefox?

---

### Post by LeadHop on 2009-01-18
firefox eats up most of my memory when things get bad. up to 40-60% sometimes.

I don't think it's a hardware issue since things work fine on windows.  I've tried running both metacity and compiz and both end up lagging sooner or later.  it's quite bothersome.  :S

---

### Post by DeMus on 2009-01-18
> **LeadHop said:**
> firefox eats up most of my memory when things get bad. up to 40-60% sometimes.

I don't think it's a hardware issue since things work fine on windows.  I've tried running both metacity and compiz and both end up lagging sooner or later.  it's quite bothersome.  :S

When you say Firefox eats 40-60% of your 1GB memory then yes something is wrong. I have 3 tabs open and here it takes 120MB, which I think is still a lot.
One of your earlier comments about Adobe is not exactly true: Adobe is always very slow, every program they make is slow, on Windows or on Linux, doesn't matter. It's such a shame they bought Macromedia so you still have to use Adobe on your PC of you want to use Flash. It's the only thing of Adobe on my computer, I can tell you that.
Btw, which Ubuntu are you using? Reading your comments I would expect 8.10, since a lot of users complain about it. I use 8.04 and I will not make the move until 8.10 is stable and fast.

---

### Post by LeadHop on 2009-01-18
I actually have many tabs open across 3 windows.  I would see this as the problem, but my windows handled much more tabs and windows on firefox without problems. :confused:

---

### Post by maestrobwh1 on 2009-01-18
I see exactly the same thing.  I started tinkering with Arch Linux and rest assured that when using kde4 and desktop effects enabled, I DO NOT see an issue with Firefox 3.0x  And even in Windows which I hate because it is so slow in loading on any pc I own, Firefox 3.0x is still faster.

Actions like right clicking and choosing "open in new tab" is so lagging, that another selection occurs, like "open in a new window" or "properties" opens, rather than a new tab.

I defected from Ubuntu on my laptop for now (not a slouch 1.8Ghx Athlon with 1.5 GB RAM).  I am running Arch installed from Chakra Alpha 1.  Arch is not as "refined" as Ubuntu in some ways: sometimes a broken package will stay in the repository for entirely too long (faac for example), but it does my most usual things with unprecedented speed.  Granted, I think one of the things that Arch has focused on is running more than just the kernel from RAM.  Once an application loads, there is almost no disk activity.  Not sure why, if in Ubuntu the tabs are taking up RAM, why then is it so slow to respond?

I see the same thing on my desktop and that is an Intel Atom 1.6 GHz Atom with 1.5 GB RAM and even with a SATA internal drive, Ubuntu drives me almost as nuts as Win XP.  For daily use, I either launch Arch FaunOS or Arch Chakra Live installed with Unetbootin to a USB drive.  I suspect that if I used an Kubuntu Live CD iso in this manner, I might see similar good performance.

**Arch as a regular HD install** however, running kde4 and Firefox 3.0x, **flies** as well as the live version on a USB drive and that is **where I think Arch has done a better job with something**.  

I am a KDE guy, and that is just what I seek to use.  True, running Fluxbox on Ubuntu 8.10, I don't see the issue.  Boring... zzzzz.

Shame, I have used Ubuntu since Dapper.  I am hoping this is fixed.  Firefox has been blamed, but it seems to be either the build of FireFox for Ubuntu is not tweaked as best it can be, or Ubuntu is not tweaked properly for Firefox.  I know people use other browsers like Opera, and those work fine, but I don't think it is an answer.

**I still love Ubuntu, it just seems to have a cold right now.  Maybe Seasonal Affective Disorder?  It just is a bit slow getting up and out of bed to do certain things.**

---

### Post by DeMus on 2009-01-18
On my machine, see specs in my signature, I am running a program called Boinc, an initiative of the university of Berkeley, California and within this I run the Seti program which is looking for signals from outer space coming from a telescope in South America.
I run 4 instances of the Seti program, one per processor core, keeping my processor load to 100%. Still I can do everything I want to do and I can not say Ubuntu is slow.
Well, I can say it, but I would be lying. 
Do I have a faster computer than you? Maybe. But with the load I have it won't be any faster than yours.

---

### Post by upchucky on 2009-01-18
I have the same issue, firefox is painfully slow ever since the last update, but i can't confirm if it is the firefox update to 3 that caused it or the several ubuntu updates since then.

I have a pretty good setup on my 4 networked pcs the slowest one is 2 gighz, 1g ram, the fastest is 3ghz 4g ram. before the recent updates they were all very fast on the internet.

---

### Post by PatrickMoore on 2009-01-18
have you considered a different web browser? perhaps opera or even seamonky?

---

### Post by DeMus on 2009-01-18
> **upchucky said:**
> I have the same issue, firefox is painfully slow ever since the last update, but i can't confirm if it is the firefox update to 3 that caused it or the several ubuntu updates since then.

I have a pretty good setup on my 4 networked pcs the slowest one is 2 gighz, 1g ram, the fastest is 3ghz 4g ram. before the recent updates they were all very fast on the internet.

With all due respect, but Firefox is NOT slow. If it acts slow in your machine then it must be caused by something else. Check the System Monitor to see how much percentage the processor is used, and what's causing it.

---

### Post by dtrot55 on 2009-01-18
Could your computer be throttling your processor?  Are you Over Clocking or do you have your ram timings set up correctly with the right voltages.  You could try and turn off the Cool and Quiet feature on your mobo if it has one..that has been known to throttle the processor sometimes.  

I also noticed a huge lag time in my windows machine when using software that used alot of mem and access time to the hard drives...turns out my main hard drive had a lot of errors on it...I used Spinrite and fixed everything...computer runs perfect...so there could be a possibility its a hard drive issue...have you tried other pieces of software that are mem and hard drive intensive as a test??  Do they have a version of Prime for linux?  Or try some benchmarking software to stress your computer.  Also your mem could be going bad..you could have a memory leak somewhere

---

### Post by LeadHop on 2009-01-19
I used to primarily be on swiftweasel when i was on hardy.  It'd be nice if the answer was as simple as just switching to swiftweasel, but i found that swiftweasel can't do certain features that i can do on firefox - mainly a chat feature i really do need for school, as well as certain flash functions like video or other media/add-ons.  

I've made no modifications whatsoever to ibex, though i find that using the system monitor to reset the priority fixes the problem for a little bit.

maybe all i'll have to do is to reinstall swiftweasel and go on firefox only when i need to use the flash/chat features?

But it seems like others are having this problem as well - we all need to get to the bottom of this for the greater good!

---

### Post by Yellow Pasque on 2009-01-19
LeadHop, your free -m does not show active swap space. Most likely, it's because you changed the UUID of the swap partition when you resized it.
Suggestion: use blkid and gksudo gedit /etc/fstab
Post back if you need help with that.

---

### Post by airbornemist6 on 2009-01-19
Yes, Firefox issues appear to be pretty common in Ibex. Some computers experience no problem whatsoever, however, some go ridiculously slow. So far there is no fix I know of. Many of the instances I've heard of have one thing in common: nvidia drivers. I'm kind of wondering if that's the case. However, it still shouldn't be a problem. I'm going to try and install Arch tomorrow and see if that works any better.

---

### Post by LeadHop on 2009-01-19
> **Temüjin said:**
> LeadHop, your free -m does not show active swap space. Most likely, it's because you changed the UUID of the swap partition when you resized it.
Suggestion: use blkid and gksudo gedit /etc/fstab
Post back if you need help with that.

As they say on the interwebs: O.O.

I've no idea what UUID is.  maybe this WOULD take care of it, haha.  on gparted my linux partition shows as ext3 and my linux partition as... linux-swap.

---

### Post by LeadHop on 2009-01-19
> **airbornemist6 said:**
> Yes, Firefox issues appear to be pretty common in Ibex. Some computers experience no problem whatsoever, however, some go ridiculously slow. So far there is no fix I know of. Many of the instances I've heard of have one thing in common: nvidia drivers. I'm kind of wondering if that's the case. However, it still shouldn't be a problem. I'm going to try and install Arch tomorrow and see if that works any better.

problem is that i'm on a laptop so a video drive change isn't as easy as it sounds!

---

### Post by adamlau on 2009-01-19
Firefox is a turtle indeed. Though my [3.1b2 PGO build absolutely decimated Opera 10 under SunSpider](http://ubuntuforums.org/showthread.php?t=1040896), startup and absolute rendering continues to lag far behind other browsers. This is with AdBlockPlus and flashplugin-nonfree only and the following (where /tmp is actually on tmpfs):

user_pref("browser.cache.disk.parent_directory", "/tmp/firefox-cache");
user_pref("browser.cache.offline.parent_directory", "/tmp/firefox-cache-offline");
user_pref("network.http.pipelining", true);
user_pref("network.http.pipelining.maxrequests", 16);
user_pref("network.http.pipelining.ssl", true);
user_pref("network.http.proxy.pipelining", true);
user_pref("nglayout.initialpaint.delay", "0");

Aside from building and using the latest PGO-enabled nightlies (and carefully stripping out elements of chrome), there is very little that can be done to speed up the Firefox experience. My advice is to try a few prebuilt releases (falling back to 2.x, if necessary) to see how they run: [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/)

---

### Post by jimv on 2009-01-19
Try this in Firefox:

Type "about:config" in the address bar and hit enter.
Right click on the settings list, and go to New>Integer.
For the name, put "toolkit.storage.synchronous".
For the value, put 0.
Restart Firefox.

---

### Post by adamlau on 2009-01-19
You could also try to increase the priority of firefox-bin.

---

### Post by Yellow Pasque on 2009-01-19
> **LeadHop said:**
> I've no idea what UUID is.
Use these two commands:
```
blkid | grep swap
gksudo gedit /etc/fstab
```
Copy the UUID given by the first command for your swap partition and paste it into the fstab file overwriting the old UUID for the swap partition.
It will look like:
```
UUID=<paste here> none swap sw 0 0 
```
Save. Quit. Reboot. Check free -m again.

---

### Post by LeadHop on 2009-01-19
Thanks for all of your guys' help and suggestions, but i've thrown in the towel and downloaded swiftweasel.  Now i need some help moving firefox settings over to swiftweasel and setting swiftweasel into my profile so i can find it under applications > internet.

i'll check on this post regularly, but i've also made a new post here:

[http://ubuntuforums.org/showthread.php?t=1044710](http://ubuntuforums.org/showthread.php?t=1044710)

thanks to everyone!

---

### Post by Yellow Pasque on 2009-01-19
> but i've thrown in the towel and downloaded swiftweasel
Great, but have you gotten your swap partition working yet? If you run out of virtual memory, your system will slow to a crawl regardless of what browser you're using.

---

### Post by LeadHop on 2009-01-19
Thanks for sticking by Temujin - I appreciate the help!  I did what you told me and I got this:

```
total       used       free     shared    buffers     cached
Mem:          1001        975         25          0        160        254
-/+ buffers/cache:        560        440
Swap:            0          0          0

```

idk why my swap shows as 0 :-(

---

### Post by Yellow Pasque on 2009-01-19
Can you post the output of:
```
sudo blkid
cat /etc/fstab
sudo swapon -a -v
```

---

### Post by LeadHop on 2009-01-20
for sudo bldkid:

```
/dev/sda1: UUID="62085DCD085DA139" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="01c3283d-e7a3-423f-b48b-503766fd46ef" 
/dev/sda6: UUID="1eb827bf-37a8-4bd8-9d03-22cadd4b4110" TYPE="ext3" 
/dev/sdb1: UUID="487C385D7C3847C8" LABEL="New Volume" TYPE="ntfs" 
```

cat /etc/fstab:
```
sibilance@sibilance-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1eb827bf-37a8-4bd8-9d03-22cadd4b4110 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=01c3283d-e7a3-423f-b48b-503766fd46ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

it's all greek to me.

oh, and i got nothing for swapon -a -v

---

### Post by Yellow Pasque on 2009-01-20
Ok, let's try:
```
sudo mkswap /dev/sda5
sudo swapon -v /dev/sda5
```

---

### Post by LeadHop on 2009-01-20
Ok, here's what i get:

```
sibilance@sibilance-laptop:~$ sudo mkswap /dev/sda5
/dev/sda5: Device or resource busy
sibilance@sibilance-laptop:~$ sudo swapon -v /dev/sda5
swapon on /dev/sda5
swapon: /dev/sda5: Device or resource busy
```

btw, thanks again.  I really appreciate you walking me through this.

---

### Post by Yellow Pasque on 2009-01-20
> I really appreciate you walking me through this.
LOL, but we haven't gotten anywhere yet.
Let's try this one more time:
```
sudo swapoff -v /dev/sda5
sudo mkswap /dev/sda5
sudo swapon -v /dev/sda5
free -m
```

EDIT: NOTE that the mkswap command will probably change the UUID of the partition yet again. Copy the UUID that mkswap spits out (or use blkid) and paste it into /etc/fstab like you did before.

---

### Post by LeadHop on 2009-01-20
haha, well hopefully this thread will go somewhere.

```
sibilance@sibilance-laptop:~$ sudo swapoff -v /dev/sda5
swapoff on /dev/sda5
sudo mkswap /dev/sda5
sudo swapon -v /dev/sda5
sibilance@sibilance-laptop:~$ sudo mkswap /dev/sda5
Setting up swapspace version 1, size = 1534200 KiB
no label, UUID=cfe4c3e7-5400-4f09-b248-ad51a6c0522d
sibilance@sibilance-laptop:~$ sudo swapon -v /dev/sda5
swapon on /dev/sda5
 sibilance@sibilance-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        733        267          0         59        131
-/+ buffers/cache:        543        458
Swap:         1498          0       1498

```

---

### Post by LeadHop on 2009-01-20
done and done with UUID swap.

---

### Post by Yellow Pasque on 2009-01-20
Great, it worked. Now:
> EDIT: NOTE that the mkswap command will probably change the UUID of the partition yet again. Copy the UUID that mkswap spits out (or use blkid) and paste it into /etc/fstab like you did before.
You don't need to reboot at the moment, but the next time you do, make sure free -m still shows Swapspace as 1498 and not 0.

---

### Post by LeadHop on 2009-01-20
fail:

```
             total       used       free     shared    buffers     cached
Mem:          1001        527        473          0         17        180
-/+ buffers/cache:        329        671
Swap:            0          0          0

```

---

