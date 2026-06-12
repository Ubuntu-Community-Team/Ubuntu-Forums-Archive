---
title: "installing latest dangerdeep from svn"
date: 2011-01-23
forum: Gaming &amp; Leisure
---

### Post by ubudog on 2011-01-23
The Danger from the Deep team has released a new guide for installing dangerdeep from svn.  You can find it here.  Hope this helps people...

[http://dangerdeep.sourceforge.net/2011/01/20/building-dangerdeep-on-debian/](http://dangerdeep.sourceforge.net/2011/01/20/building-dangerdeep-on-debian/)

---

### Post by NM5TF on 2011-01-26
> **ubudog said:**
> The Danger from the Deep team has released a new guide for installing dangerdeep from svn.  You can find it here.  Hope this helps people...

[http://dangerdeep.sourceforge.net/2011/01/20/building-dangerdeep-on-debian/](http://dangerdeep.sourceforge.net/2011/01/20/building-dangerdeep-on-debian/)

I downloaded this & it works OK for 5 minutes or so, then it hangs up & goes to a black screen...the music is still playing but I can't do anything until I kill the process with CTL+ALT+F1

I have disabled the screensaver & power mgt, but that didn't help :mad:

anyone else have this problem :confused:

---

### Post by ubudog on 2011-01-27
> **NM5TF said:**
> I downloaded this & it works OK for 5 minutes or so, then it hangs up & goes to a black screen...the music is still playing but I can't do anything until I kill the process with CTL+ALT+F1

I have disabled the screensaver & power mgt, but that didn't help :mad:

anyone else have this problem :confused:

I actually have that same problem.  That is one of the main reasons I bought this new gaming laptop, but I still have the problem.  Nvidia too.

---

### Post by realzippy on 2011-01-27
> **NM5TF said:**
> I downloaded this & it works OK for 5 minutes or so, then it hangs up & goes to a black screen...the music is still playing but I can't do anything until I kill the process with CTL+ALT+F1

I have disabled the screensaver & power mgt, but that didn't help :mad:

anyone else have this problem :confused:

Same.
Crashes on 2 machines here,so not vga driver related (Intel/NVIDIA).
Tried also disabling compiz,AA and AF,nothing.
But I like the music..

---

### Post by NM5TF on 2011-01-27
I went to the sourceforge site to ask for help...it tells me to go the 
#dangerdeep IRC channel to ask for help...the IRC channel tells me it's for developers use only & tells me to go to sourceforge site & ask for help WTF:confused::confused:

---

### Post by ubudog on 2011-01-28
> **NM5TF said:**
> I went to the sourceforge site to ask for help...it tells me to go the 
#dangerdeep IRC channel to ask for help...the IRC channel tells me it's for developers use only & tells me to go to sourceforge site & ask for help WTF:confused::confused:

Yeah, don't worry about that, they don't really care.  I went on there and talked to the devs (though they are rarely on there), and they guided me through a bunch of debugging and stuff, with no result...  :(

---

### Post by lkjoel on 2011-02-19
> **ubudog said:**
> The Danger from the Deep team has released a new guide for installing dangerdeep from svn.  You can find it here.  Hope this helps people...

[http://dangerdeep.sourceforge.net/2011/01/20/building-dangerdeep-on-debian/](http://dangerdeep.sourceforge.net/2011/01/20/building-dangerdeep-on-debian/)
Nice tutorial.
If any of you want an automatic installation script for this, I attached it.

NOTICE: The installation was generated from a script.
It works on my machine, but it is not 100% certain that it will work on your machine.

---

### Post by realzippy on 2011-02-20
> **lkjoel said:**
> Nice tutorial.
If any of you want an automatic installation script for this, I attached it.

NOTICE: The installation was generated from a script.
It works on my machine, but it is not 100% certain that it will work on your machine.


So does the game **not** crash on your machine?
Nobody got it running ... installing is not the problem.

---

### Post by lkjoel on 2011-02-20
> **realzippy said:**
> So does the game **not** crash on your machine?
Nobody got it running ... installing is not the problem.
I haven't tried the game.
I mean't the install script worked.

---

### Post by NM5TF on 2011-02-20
> **lkjoel said:**
> I haven't tried the game.
I mean't the install script worked.


PLEASE try the game to see if it works longer than 5-6 minutes on your machine....

I did NOT have any trouble installing it, but it won't work longer than 5-6 minutes before hanging & crashing...

I did talk to 1 of the DEVS on IRC #dangerdeep channel & gave him a
stack trace of my problems...he said he would try to make time to look 
into it ( they are all busy with work/school ) & hopefully come up with
a fix....

---

### Post by lkjoel on 2011-02-21
> **NM5TF said:**
> PLEASE try the game to see if it works longer than 5-6 minutes on your machine....

I did NOT have any trouble installing it, but it won't work longer than 5-6 minutes before hanging & crashing...

I did talk to 1 of the DEVS on IRC #dangerdeep channel & gave him a
stack trace of my problems...he said he would try to make time to look 
into it ( they are all busy with work/school ) & hopefully come up with
a fix....
My computer is not made for gaming.
Actually, my computer has a few problems, so it is quite slow.

---

### Post by Dlambert on 2011-03-19
Game runs, but freezes when close to convoy.

---

### Post by NM5TF on 2011-04-04
> **Dlambert said:**
> Game runs, but freezes when close to convoy.

I never even get "close to convoy"...even at "flank speed"...
it freezes after 5-6 minutes....

after loading "new" release last week I did notice that the game menus
seem to load faster than before, but game still freezes....

---

### Post by realzippy on 2011-04-06
..same here,after loading 198 MB of updates,it still does not run.
Don't they test their stuff themselves?

---

### Post by NM5TF on 2011-04-06
> **realzippy said:**
> ..same here,after loading 198 MB of updates,it still does not run.
Don't they test their stuff themselves?

don't know if they do...

I did talk to 1 of the DEVS on IRC # Dangerdeep channel & gave him a stack trace of my SIGENT error...he said he would look at it...I think that is
where the "updates" came from...just guessing of course....

---

### Post by ubudog on 2011-04-06
Yep I did the same like 5 months ago...

---

### Post by realzippy on 2011-04-06
Just read on there page:

Latest Ubuntu Builds
January 23rd, 2010 by mbady
[I]For Ubuntu Linux users we have created a Launchpad PPA with the latest build of the SVN trunk.
Like the Win32 builds **they are totally untested** and we expect them to contain bugs ...[/I]

Now I understand.
Anybody tested compiling from source?

---

### Post by NM5TF on 2011-04-06
> **realzippy said:**
> Just read on there page:

Latest Ubuntu Builds
January 23rd, 2010 by mbady
[I]For Ubuntu Linux users we have created a Launchpad PPA with the latest build of the SVN trunk.
Like the Win32 builds **they are totally untested** and we expect them to contain bugs ...[/I]

Now I understand.
Anybody tested compiling from source?

my "latest updates" came from the Update Manager via mbady & were dated
sometime last Month...

I also tried compiling from source from the Sourceforge Site...

both gave the same results...it seems to work fine for 5-6 minutes
& then freezes...only way out is CTRL-ALT-F1 & then CTRL-ALT-F8 & then
CTRL-ALT-BACKSPACE to get back to desktop...

real bummer as the graphics are great & looks to be a great game when/if
it ever works!!!

---

### Post by realzippy on 2011-04-06
ok,so I won't compile.
thanks.
So going to mess around with ~/.dangerdeep/config

---

### Post by realzippy on 2011-04-06
just enabled debugging in the config file..

*<debug value="1"*

Indeed creates a debug.log,but file is empty  :(
Can someone also test this?

---

### Post by ubudog on 2011-04-06
> **realzippy said:**
> just enabled debugging in the config file..

*<debug value="1"*

Indeed creates a debug.log,but file is empty  :(
Can someone also test this?

Sure, I will try this later when I have time and post back.

---

### Post by NM5TF on 2011-04-06
> **realzippy said:**
> just enabled debugging in the config file..

*<debug value="1"*

Indeed creates a debug.log,but file is empty  :(
Can someone also test this?

same thing here...

set debug value=1

REALLY slowed down the game loading, guess this should be expected???

debug.log is empty even tho game still froze...:confused:

---

### Post by ubudog on 2011-04-06
> **NM5TF said:**
> same thing here...

set debug value=1

REALLY slowed down the game loading, guess this should be expected???

debug.log is empty even tho game still froze...:confused:

Lol, yeah, guess it's to be expected...  :-(

---

### Post by NM5TF on 2011-04-12
this morning the Update Manager installed the "latest & greatest" update 
to Dangerdeep....version 0+3065~lucid1.....unfortunately, the problem is
still not fixed...

while the menus do seem to load faster, the game still crashes after 5-6
minutes...

at least someone seems to be working on it...hopefully it will soon become
a playable game!!!

---

### Post by ubudog on 2011-04-12
Yep, at least it is still active, and isn't abandoned like some other Linux games that would've probably gotten better...

---

### Post by NM5TF on 2011-04-12
> **ubudog said:**
> Yep, at least it is still active, and isn't abandoned like some other Linux games that would've probably gotten better...

got a msg from one of the Devs on IRC #dangerdeep channel...they just put
new code on SVN & asked to test it...am downloading it now from Synaptic..
will test it when it finishes

they are actively working on code as time permits...:p

---

### Post by ubudog on 2011-04-12
Sounds great!  I will do the same.

---

### Post by realzippy on 2011-04-13
...same crashing as used to.
Still no error.log file.
think the config file doesn't work properly,eg. deactivating sound
also does not work.Can you ask the developer about the error log file?
Think it is essential when attempting to fix code...?

Noticed:

When diving,game does not crash.Crashes immediately when surfacing and
going to tower.

---

### Post by NM5TF on 2011-04-13
> **realzippy said:**
> ...same crashing as used to.
Still no error.log file.
think the config file doesn't work properly,eg. deactivating sound
also does not work.Can you ask the developer about the error log file?
Think it is essential when attempting to fix code...?

Noticed:

When diving,game does not crash.Crashes immediately when surfacing and
going to tower.

still crashes here also...have not noticed it working when dived, but have not checked either...error.log file still empty here also...

just sent a msg to Dev on IRC...waiting for response & will post back when they do....at least they trying to fix it!!! :)

---

### Post by NM5TF on 2011-05-09
got a message from the Devs on IRC #dangerdeep stating they have not
been able to reproduce the problem....

I asked him what distro & hardware platform they are using...waiting for a response now....

they did state that "some clean up work was done a couple of weeks ago"...
don't know what that means yet....

at least they seem to be still working on the game...we'll hope for the best....

---

### Post by NM5TF on 2011-05-10
> **NM5TF said:**
> got a message from the Devs on IRC #dangerdeep stating they have not
been able to reproduce the problem....

I asked him what distro & hardware platform they are using...waiting for a response now....

they did state that "some clean up work was done a couple of weeks ago"...
don't know what that means yet....

at least they seem to be still working on the game...we'll hope for the best....


they just responded...see my reply at bottom of this page:

[http://ubuntuforums.org/showthread.php?t=1702979&page=2](http://ubuntuforums.org/showthread.php?t=1702979&page=2)

---

### Post by NM5TF on 2011-05-12
MAJOR NEWS...

I am now able to play this game with no problems...:P

to see how I did it go to my last post here;

[http://ubuntuforums.org/showthread.php?t=1702979](http://ubuntuforums.org/showthread.php?t=1702979)

---

### Post by ubudog on 2011-05-24
EDIT: Disregard this...

---

### Post by NM5TF on 2011-08-06
IT'S FIXED!!!!:P

Dangerdeep DEV's have found & fixed the bug that has been causing
it to crash...the bug was in the terrain code according to the DEV
I talked to....

Have been playing it for last 2-3 days for over 3 hours at a time
with no problems!!! Have managed to sink every ship in a large convoy
and even reload torpedo tubes.

The latest download has superb graphics & game play....give it a try!!!

---

### Post by realzippy on 2011-08-06
Ok,I will download the update...
Thanks for sharing.
The game is fun?

---

### Post by NM5TF on 2011-08-06
> **realzippy said:**
> Ok,I will download the update...
Thanks for sharing.
The game is fun?

If you like Sub Sims, this is the best I've seen yet....they are
adding to it all the time...still some features to be implemented,
but it's great fun...especially with a 64 bit box, the graphics
are great....

---

### Post by realzippy on 2011-08-06
Yes,like them.But more the arcade ones,like "Enigma rising tide"
(which used to run pretty well in wine),once tried
"Silent Hunter3" and was unable to get out of the harbour without
collision  ;-)...

---

### Post by realzippy on 2011-08-06
Arrgh!
segvault !

---

### Post by ubudog on 2011-08-06
> **realzippy said:**
> Arrgh!
segvault !

Try getting the latest svn and *rebuilding*.

An example:
```
cd dangerdeep; svn up
```

Then,
```
scons debug=1 datadir=~/dangerdeep/data
```

You can then run it like so:
```
cd ~/dangerdeep; ./build/linux/dangerdeep
```

That did it for me, it seems to fix all the segfaults and random crashes.  :-)

---

### Post by NM5TF on 2011-08-06
found a new bug today & am working on it with the DEV's...

any type II submarine will NOT submerge...the DEV says he is have
problems with buoyancy issues for type II subs...I agree...

the good news is that type VII submarine works as it should, so the
game is totally playable with that sub.....they will work on it until
they get fixed

---

### Post by realzippy on 2011-08-06
Got the newest svn version now,but still:
```
SIGSEGV caught!
```

Will try it on another machine in the evening...

---

### Post by NM5TF on 2011-08-06
> **realzippy said:**
> Got the newest svn version now,but still:
```
SIGSEGV caught!
```

Will try it on another machine in the evening...

on my machine it started working suddenly after the latest 10.04.2
Kernel update...there was also an update thru the update manager...
don't know which update caused it to work...most likely the update
that the DEV's did....

do you do the daily updates thru sudo apt-get update???  might try
that to see if works...just a thot...

you are running it in native mode & not thru WINE aren't you???

---

### Post by realzippy on 2011-08-06
No wine.
Same issue on downloaded/updated version and built from svn...
And I am on 10.10 with 2.6.35-28...
but,as mentioned,I will try it on my nvidia machine (this one is intel)
and report...

---

### Post by ubudog on 2011-08-06
> **realzippy said:**
> Got the newest svn version now,but still:
```
SIGSEGV caught!
```

Will try it on another machine in the evening...

Did you rebuild it?

---

### Post by realzippy on 2011-08-06
> **ubudog said:**
> Did you rebuild it?

I tried,but it was already Revision 3406....since svn built was only 2 minutes old...  ;-)

---

### Post by ubudog on 2011-08-06
> **realzippy said:**
> I tried,but it was already Revision 3406....since svn built was only 2 minutes old...  ;-)

Well, it would probably be best to build after every svn up, you might find that your problem is fixed.  :-)

---

### Post by realzippy on 2011-08-06
Ok,with nvidia card it finally is running using latest svn.
....reached convoy the first time without crash!

---

### Post by NM5TF on 2011-08-06
> **realzippy said:**
> Ok,with nvidia card it finally is running using latest svn.
....reached convoy the first time without crash!

I also have nvidia card...how about you Ubudog???

I will report to the DEV's after I hear from you that it seems to work
with nvidia but not intel cards....unless Ubudog uses intel card....

---

### Post by lkjoel on 2011-08-06
Why compile it from source?
Try this: [https://launchpad.net/~aegirxx-googlemail/+archive/dftd-latest]("https://launchpad.net/%7Eaegirxx-googlemail/+archive/dftd-latest")

---

### Post by realzippy on 2011-08-06
> **lkjoel said:**
> Why compile it from source?
Try this: [https://launchpad.net/~aegirxx-googlemail/+archive/dftd-latest]("https://launchpad.net/%7Eaegirxx-googlemail/+archive/dftd-latest")
..this didn 't work.

---

### Post by lkjoel on 2011-08-06
> **realzippy said:**
> ..this didn 't work.
Sorry, I forgot to mention that the new build will start in 14 hours, so it should be available in around 24 hours.

---

### Post by realzippy on 2011-08-07
Everything is fine,means game running since svn 3406 on my nvidia machine.
3407 also works,both do not on Intel integrated graphics (I3 pre sandy),
game refuses starting with sigvault error.A few month ago game started on Intel fine,but crashed after a few minutes...
This may be due to the intel driver,which changed meanwhile.

---

### Post by NM5TF on 2011-08-07
> **realzippy said:**
> Ok,with nvidia card it finally is running using latest svn.
....reached convoy the first time without crash!

the DEV's want to know if you are using 10.10 on the nvidia machine that is working now...they say they are using an Intel card on their development
machine, but running Gentoo Linux....

---

### Post by realzippy on 2011-08-07
10.10 on both machines.
btw:
```
description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:d1400000-d17fffff memory:c0000000-cfffffff ioport:4050(size=8)
```

If devs want me to run debug mode or need other infos,no problem.
I would like to help if I can...

---

### Post by NM5TF on 2011-08-07
> **realzippy said:**
> 10.10 on both machines.
btw:
```
description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:d1400000-d17fffff memory:c0000000-cfffffff ioport:4050(size=8)
```

If devs want me to run debug mode or need other infos,no problem.
I would like to help if I can...

if you go to IRC #dangerdeep channel, he is there now...

BTW, you may need to update your kernel if still running 2.6.25-38...
I run 2.6.32-33-generic FWIW....

---

### Post by realzippy on 2011-08-07
> **NM5TF said:**
> if you go to IRC #dangerdeep channel, he is there now...

BTW, you may need to update your kernel if still running 2.6.25-38...
I run 2.6.32-33-generic FWIW....

I also have a test partition with 11.04 and a few kernels (also 3.x.xx),
will have a test later.I am pretty busy today (real life calling)...

---

### Post by NM5TF on 2011-08-07
> **realzippy said:**
> I also have a test partition with 11.04 and a few kernels (also 3.x.xx),
will have a test later.I am pretty busy today (real life calling)...

if you get time later, check into IRC #dangerdeep....check in with tx2rx...he is Matt in the U.K.

---

### Post by Dlambert on 2011-08-07
This is great news for my favorite Open Source game.

---

### Post by ubudog on 2011-08-07
> **Dlambert said:**
> This is great news for my favorite Open Source game.

:guitar:

---

### Post by lkjoel on 2011-08-08
I think that the PPA contains the bug-fixed revision!
```
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo sed -i "s/`lsb_release -s -c`/maverick/g" /etc/apt/sources.list.d/aegirxx-googlemail*
sudo apt-get update
sudo apt-get install dangerdeep-latest

```
[]("https://launchpad.net/%7Eaegirxx-googlemail/+archive/dftd-latest")

---

### Post by ubudog on 2011-08-08
> **lkjoel said:**
> I think that the PPA contains the bug-fixed revision!
```
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo sed -i "s/`lsb_release -s -c`/maverick/g" /etc/apt/sources.list.d/aegirxx-googlemail*
sudo apt-get update
sudo apt-get install dangerdeep-latest

```
[]("https://launchpad.net/%7Eaegirxx-googlemail/+archive/dftd-latest")

Cool!

---

### Post by Dlambert on 2011-08-14
> **lkjoel said:**
> I think that the PPA contains the bug-fixed revision!
```
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo sed -i "s/`lsb_release -s -c`/maverick/g" /etc/apt/sources.list.d/aegirxx-googlemail*
sudo apt-get update
sudo apt-get install dangerdeep-latest

```
[]("https://launchpad.net/%7Eaegirxx-googlemail/+archive/dftd-latest")

Yea, i followed the Sites Debian compile, and everything still crashed, no dive, etc.

---

### Post by Dlambert on 2011-08-14
Trying PPA tomorrow

---

### Post by Dlambert on 2011-08-14
Btw,
Linux Mint Debian Edition XFCE 64 bit
Nvidia GTS 450
AMD Phenom II x4 OC'D @ 3.6 Ghz
4GB of DDR3 Gskill Ram 8-8-7-24

---

### Post by Dlambert on 2011-08-14
When i set resolution at 1600x900, its still not correct. Any ideas?

---

### Post by ubudog on 2011-08-14
Is your resolution not supported by the game? I recommend running it in windowed mode then.

---

### Post by lkjoel on 2011-08-15
So which revision is the bug-fixed one?

---

### Post by Dlambert on 2011-08-20
The PPA, haven't tried it yet...but the site install is buggy

---

### Post by lkjoel on 2011-08-20
It works for me

---

### Post by Dlambert on 2011-08-21
> **lkjoel said:**
> It works for me

I havent tried the version in the post. I'm talking about the debian compile straight off their site.

---

### Post by Dlambert on 2011-08-21
Can you tell the Devs to update the site? Maybe give instructions to latest version etc...

---

### Post by lkjoel on 2011-08-21
What do you mean? Doesn't it work already?

dangerdeep works from the PPA no problem.

---

### Post by realzippy on 2011-08-25
Here the ppa version works on intel and nvidia graphics.
Btw,dangerdeep as reason to buy a gaming laptop seems strange.
Although the game seems to run meanwhile,it is far away from standarts in submarine simulation,I would say it's alpha.
Check out [silent hunter]("http://silent-hunter.uk.ubi.com/silent-hunter-5/") if you want a highend submarine game..

---

### Post by ubudog on 2011-08-25
> **realzippy said:**
> Here the ppa version works on intel and nvidia graphics.
Btw,dangerdeep as reason to buy a gaming laptop seems strange.
Although the game seems to run meanwhile,it is far away from standarts in submarine simulation,I would say it's alpha.
Check out [silent hunter]("http://silent-hunter.uk.ubi.com/silent-hunter-5/") if you want a highend submarine game..

Yeah, it's in alpha stage:
[http://ubudog.net/dangerdeepalpha.png](http://ubudog.net/dangerdeepalpha.png)

There are other alternatives, but I think they do a great job with the limited manpower and money.  :-)

---

### Post by realzippy on 2011-08-25
> **ubudog said:**
> 
 but I think they do a great job with the limited manpower and money.  :-)

No question.Id didn't mean bad by "alpha"..was estimated,didn't know.
Looks promising,hope they keep on coding...torpedo hit effects eg.
Music is great at the tower at night...

---

### Post by ubudog on 2011-08-26
> **realzippy said:**
> No question.Id didn't mean bad by "alpha"..was estimated,didn't know.
Looks promising,hope they keep on coding...torpedo hit effects eg.
Music is great at the tower at night...

Yeah, hopefully the project goes on... 

I do love the music, yeah.  :-)

---

### Post by Dlambert on 2011-08-27
Who bought a gaming pc for Dftd?

---

### Post by lkjoel on 2011-08-27
I didn't buy a gaming pc for it, but I overclocked my graphics card (400 MHZ GPU, 620 MHZ Memory).

---

### Post by ubudog on 2011-08-27
> **Dlambert said:**
> Who bought a gaming pc for Dftd?

I did, lol, but I use it for other things too.  ;-)

---

### Post by Dlambert on 2011-08-28
Trying right now on pure Debian sid, with the maverick PPA.

---

### Post by ubudog on 2011-08-28
> **Dlambert said:**
> Trying right now on pure Debian sid, with the maverick PPA.

Cool, I think that's what the devs use.  Keep us updated.  ;-)

---

### Post by Dlambert on 2011-08-28
Long time ubuntu user, but I really like the Rolling release ideal. And unity is a no go for me. XFCE.

---

### Post by ubudog on 2011-08-29
> **Dlambert said:**
> Long time ubuntu user, but I really like the Rolling release ideal. And unity is a no go for me. XFCE.

I like plain old GNOME.  Will stick with my 2.32.0.  XFCE is also nice.

---

### Post by Dlambert on 2011-08-29
> **lkjoel said:**
> I think that the PPA contains the bug-fixed revision!
```
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo sed -i "s/`lsb_release -s -c`/maverick/g" /etc/apt/sources.list.d/aegirxx-googlemail*
sudo apt-get update
sudo apt-get install dangerdeep-latest

```
[]("https://launchpad.net/%7Eaegirxx-googlemail/+archive/dftd-latest")

OK, i did this, but modified this to run from Debian Sid. I downloaded it, and ran it and like someone said before type II subs don't dive, my res 1600x900 isn't supported, even though it's listed. I will do further testing. Specs: 

> AMD Phenom II x4 OC @ 3.6GHz
Nvidia GTS 450
4Gb gkill ddr3 1600


---

### Post by Dlambert on 2011-08-29
Vendor: NVIDIA Corporation
Render: GeForce GTS 450/PCI/SSE2
Version: 4.1.0 NVIDIA 280.13
GLSL: 4.10 NVIDIA via Cg compiler
[Good] :-) OpenGL Version: 4.1.x 
[Good] :-) Found 4 Texture Units and 32 Image Texture Units 
[Good] :-) Support for vertex buffer objects
[Good] :-) Support for framebuffer objects
[Good] :-) Support for non power of two textures
[Good] :-) Support for fragment shaders
[Good] :-) Support for vertex shaders
[Good] :-) Support for shader objects
[Good]  Support for texture compression
[Good]  Support for 16bit floats

---

### Post by Dlambert on 2011-08-29
Actually the other sub Barely dives as well, you have to wait a while. Then you cant return to the surface. Historical battles, even training ones don't work.:confused: I thought it was fixed? And all other subs rotate UN-naturally.

---

### Post by Dlambert on 2011-08-29
sudo add-apt-repository ppa:aegirxx-googlemail/dftd-latest
sudo sed -i "s/`lsb_release -s -c`/maverick/g" /etc/apt/sources.list.d/aegirxx-googlemail*
sudo apt-get update
sudo apt-get install dangerdeep-latest


Worked for me in sid

---

### Post by Dlambert on 2011-08-29
In sid, im using LMDE (linux mint debian edition) and i Open software manager, edit, sources, other software, add, 

> deb [http://ppa.launchpad.net/aegirxx-googlemail/dftd-latest/ubuntu](http://ppa.launchpad.net/aegirxx-googlemail/dftd-latest/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/aegirxx-googlemail/dftd-latest/ubuntu](http://ppa.launchpad.net/aegirxx-googlemail/dftd-latest/ubuntu) maverick main

Then

> sudo apt update

Then install

---

