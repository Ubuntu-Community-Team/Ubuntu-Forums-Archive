---
title: "Warning, Beryl 0.1.99 upgrade broke my beryl"
date: 2007-01-18
forum: Desktop Environments
---

### Post by rabid emu on 2007-01-18
I just saw that there were Beryl updates to 01.99+0.2.0beta1.  Of course I installed them, never had much of a problem with beryl before.  However, this update completely broke beryl, it could not run at all.

If you encounter this problem, easiest thing to do (my solution) was to downgrade each package back to 0.1.4 using Synaptic.  Search 'beryl', and for each installed package click package -> force package and select the latest version that beryl worked.  After downgrading every package to 0.1.4 everything is working smoothly once again.

Hopefully Beryl team fixes this problem promptly and we can all get on with our lives staring at a rotating cube :P

---

### Post by cstrippie on 2007-01-18
Same experience here, and same solution.  Beryl folks are aware of this and working on it.

---

### Post by a.tom on 2007-01-18
same here... good to know, that there´s a simple solution (i will try later) - i would really miss my wobbling windows ;)

---

### Post by QuinnStorm on 2007-01-18
We're working as I type this on getting beta2 (0.1.99.1) put together to fix these issues.  The release was botched, and I apologize.  I wasn't managing effectively, but that will change.

---

### Post by engineer on 2007-01-18
installing the beryl-settings-bindings package helped for me.
it's not filed as dependency

---

### Post by aidanr on 2007-01-18
had a few minor issues upgrading tonight, but no major breakage, had to install through synaptic rather than update manager because for some reason the update manager wanted to dist upgrade, and also had to install beryl-settings-bindings for beryl-settings to work

other than that all seems good so far, the window tabbing is fairly impressive and the new settings manager is very nice, but there's no profile import/export :-?

---

### Post by wzzrd on 2007-01-18
Could you post back here when you fixed the problems? I get a segfault when trying to start beryl now, so I'ld really like to know when the problem is solved so I can install the new packages directly. I'll subscribe to this thread, so I'll be informed of the progress.

Btw, every time I try and download a package from the beryl repo today I get an 'IP not found' error the first time. The second time I can connect and download the way it is supposed to...

---

### Post by rudlavibizon on 2007-01-18
When i try to upgrade, i get 404 addresss not found. Is this because that bug is being fixed?
Compiz updates upgraded fine. Btw. is beryl dependant on compiz packages or are those just leftovers from my previous installation of compiz?

---

### Post by lnxnubie on 2007-01-18
Same problem with me:confused:
Any solution yet ?

---

### Post by mcduck on 2007-01-18
> **rudlavibizon said:**
> When i try to upgrade, i get 404 addresss not found. Is this because that bug is being fixed?
Compiz updates upgraded fine. Btw. is beryl dependant on compiz packages or are those just leftovers from my previous installation of compiz?

They are just old stuff from your previous Compiz installation. If you aren't using it any more you can safely uninstall them..

---

### Post by eightballd on 2007-01-18
No problems after upgrade this morning here, but beryl-settings wouldn't load for me either.  Doing like engineer said and loading beryl-settings-bindings worked for me.   New UI...nice... :)

PS:  I'm running an Nvidia FX 5200, though not sure the version of my driver.

---

### Post by rabid emu on 2007-01-18
Can anyone else confirm whether they fixed the package or not?  Does installing the bindings package fix the upgrade?

---

### Post by dshuck on 2007-01-18
After the update, upon logging in my screen never progressed beyond the password prompt, yet I heard the login audio.  I installed the beryl-settings-bindings, and can now log in, but none of the beryl functionality is working,  the processor is pegged out, and the system is crawling.  FWIW, this post took about 5 minutes to write!

---

### Post by blouzak on 2007-01-18
> **rabid emu said:**
> Can anyone else confirm whether they fixed the package or not?  Does installing the bindings package fix the upgrade?

well... NO they haven't and NO it doesn't. It makes the beryl settings manager window open. so the bindings package fixes that. I can change the settings and all but there's no point. Coz beryl is not really working. I am forced to use Metacity. I can't  downgrade to the previous version either, which was working perfectly, using synaptics...  



(I installed Ubuntu again, after 1 month of SUSE [-(  , yesterday. It was working like a charm. Unfortunately I only enjoyed it for one day. Some help would be appreciated)

---

### Post by beeng on 2007-01-18
I have the same problem... beryl-xgl crashes with a seg. fault :(

---

### Post by mysticrider92 on 2007-01-18
Nice to know I am not the only one with this problem. :-) Hopefully it will be fixed soon.

---

### Post by PriceChild on 2007-01-18
We're aiming to get 0.2.0-beta2 on the repos tomorrow...

Please just disable beryl in the meantime if its not working for you.

Pricey

---

### Post by beeng on 2007-01-18
hmm too late for that ;) I installed the SVN files and they work fine EXCEPT the beryl-settings doesn't work.  No problem, it's an interim solution.
Here's how I did it:
[http://www.biodesign.com.ar/blog/?p=28](http://www.biodesign.com.ar/blog/?p=28)

---

### Post by revertex on 2007-01-18
my temporary solution is install compiz, never played compiz before, an now i understand why they forked to beryl.
compiz is rock solid, but lacks TONS of funcionality that beryl provide.
It's almost impossible change beryl for compiz.

Please devs, i'm praying for you to fix beryl soon!  :p

---

### Post by mexlinux on 2007-01-18
Have just updated to new beryl packages and Beryl is working again,
The setting manager is not working, but Beryl is.
beryl-core version:
0.20+svn20070778-r2822+3v1ubuntu1

---

### Post by vexeuz on 2007-01-18
Just revert back to old version:

for these packages: beryl; beryl-core; beryl-manager; beryl-plugins; beryl-plugins-data; beryl-settings; emerald; libberyldecoration0; libberylsettings0; libemeraldengine0

sudo apt-get update
(i hade to repeat code for each package):
sudo aptitude purge <packages>

Mine is back to normal. Just dont update these packages again if it ask you to...

---

### Post by Dies on 2007-01-19
> **QuinnStorm said:**
> We're working as I type this on getting beta2 (0.1.99.1) put together to fix these issues.  The release was botched, and I apologize.  I wasn't managing effectively, but that will change.

From what I got to see of it, before I logged out and found I couldn't get back in - X just kept restarting - it was pretty awesome, one of my major complaints was Beryl Settings Manager because after the last upgrade there was just too much stuff, but Wow did you guys do a nice job cleaning that up. :D 
Thanks for all your hard work. Now I just can't go back to a "normal" window manager.

BTW if you set beryl-manager to autostart like I did just rm the file in ~/.config/autostart.

---

### Post by wzzrd on 2007-01-19
> **mexlinux said:**
> Have just updated to new beryl packages and Beryl is working again,
The setting manager is not working, but Beryl is.
beryl-core version:
0.20+svn20070778-r2822+3v1ubuntu1

Where did you get those packages? Downloaded manually? I don't see that package in apt, so I can't use it. Hoping new packages wil turn up today!

---

### Post by stueyboy on 2007-01-19
I found the .99 version of beryl crashed yesterday and didn't load the settings program. I completely removed them rather than downgrading and having just re-installed to see if things were better, I found that it all works now including the settings manager so maybe the kind peeps at Beryl have fixed it.

BTW, it's nice

---

### Post by wzzrd on 2007-01-19
I just did the remove-reinstall too, and no luck. Still a core dump & a segfault :(

---

### Post by jfrez on 2007-01-19
use treviño repo.
[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

---

### Post by CroEragon on 2007-01-19
Same problem here. I did what vexeuz from top of page said and its working again except Beryl Settings manager. Here is quote.

> **vexeuz said:**
> Just revert back to old version:

for these packages: beryl; beryl-core; beryl-manager; beryl-plugins; beryl-plugins-data; beryl-settings; emerald; libberyldecoration0; libberylsettings0; libemeraldengine0

sudo apt-get update
(i hade to repeat code for each package):
sudo aptitude purge <packages>

Mine is back to normal. Just dont update these packages again if it ask you to...

---

### Post by dshuck on 2007-01-19
FWIW, vexuez's fix worked for me as well.  Thanks!

---

### Post by linedpaper on 2007-01-19
grrrr...just downgraded well see if mine is all better in a second.  hopefully that bug fix comes soon!

---

### Post by mysticmarks on 2007-01-19
[http://ubuntuforums.org/showthread.php?t=341861](http://ubuntuforums.org/showthread.php?t=341861)

---

### Post by Guillaumeb on 2007-01-19
Can anyone explain what this mean?
ched 10.8kB in 0s (11.5kB/s)
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Do you actually have a key cause I do not. How do you do this? Beryl is so all f**** up !!

Also when going to Synaptic, searching for Beryl, marking one of the file as reinstallation and going to package, the "force" option is not available

---

### Post by linedpaper on 2007-01-19
after downgrading everything beryl-manager still appears to be the newer version and beryl still crashes every time i try to switch over to it as the desktop manager.  any ideas?

---

### Post by linedpaper on 2007-01-19
i just upgraded to the svn and now the menu for beryl manager does not have an option for all the beryl manager settings.  everything works though other than that.

---

### Post by sixfoottallrabbit on 2007-01-19
I just went to synaptic and searched Beryl up and there were 2 packages that were version 0.1.99.

The first, called "beryl", I have downgraded to 0.1.4, but it's still not working.

The other package, called "libberyldecoration0" will not let me choose "Force version...". It is version 0.1.99+0.2.0-beta1.

How do I downgrade this package? Is it's version locked? How do i change that?

---

### Post by linedpaper on 2007-01-19
here's my output...anbody know what's wrong?

```
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in ?
    import berylsettings
ImportError: No module named berylsettings

```

---

### Post by linedpaper on 2007-01-19
I figured out my problem, but I do not know how to fix it.  On the [http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/) repository beryl-settings-bindings is an older version.  Anybody know if there is a .deb pkg for the newest version of this package?  

	beryl-settings-bindings_0.1.5+svn20070118-r2815+3v1ubuntu0_i386.deb

---

### Post by wylie98 on 2007-01-19
Having tried most of the diffrent suggestions here and on [http://forum.beryl-project.org/viewtopic.php?f=36&t=2297&st=0&sk=t&sd=a&start=50](http://forum.beryl-project.org/viewtopic.php?f=36&t=2297&st=0&sk=t&sd=a&start=50). I got it back by switching to the svn version. Beryl started to work again for me, but the settings manager doesn't seem to work. Anybody got any ideas?

---

### Post by wylie98 on 2007-01-19
P.S. Whats the difference between the svn version and the beryl original?(in noob english please!)

---

### Post by igknighted on 2007-01-19
> **wylie98 said:**
> Having tried most of the diffrent suggestions here and on [http://forum.beryl-project.org/viewtopic.php?f=36&t=2297&st=0&sk=t&sd=a&start=50](http://forum.beryl-project.org/viewtopic.php?f=36&t=2297&st=0&sk=t&sd=a&start=50). I got it back by switching to the svn version. Beryl started to work again for me, but the settings manager doesn't seem to work. Anybody got any ideas?

install the package beryl-manager-bindings, that should solve the issue.  The SVN version appears to be fixed today, so I would stick with that.

SVN is the daily snapshot of what Beryl is working on.  It is the most up to date version possible, but also the highest likelyhood of bugs.  The other versions are standard releases (if you have any knowledge of SuSE think of SVN as the SuSE Factory Repo's)

---

### Post by mexlinux on 2007-01-19
> **wylie98 said:**
> P.S. Whats the difference between the svn version and the beryl original?(in noob english please!)

What you call original is an alpha but "stable" version.

The svn version is the version where the developer make the changes online everyday, It's not a stable version, and it may breake some times, because code is being modified all the time.

Once a new version is released officiale it will move from svn to "original", it will freez for a time, and the svn version will continue being modified

---

### Post by linedpaper on 2007-01-19
downgrade 

beryl-settings-bindings to the svn 1.5 version and it should work fine.

---

### Post by wylie98 on 2007-01-19
Thats cleared that up. Can't seem to find the bindings package you mentioned on either repos. Am i missing something?

---

### Post by sixfoottallrabbit on 2007-01-19
So guys, how do you change to the SVN version? Then when I want to change back, how do I do that?

---

### Post by mexlinux on 2007-01-19
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository")

---

### Post by jsully1 on 2007-01-19
I'm just using Metacity for today until Beta 2 is (hopefully) released tomorrow.  Keep up the good work guys, and don't get too discouraged with today's setback.

---

### Post by wylie98 on 2007-01-19
That worked. Thanks very much.

---

### Post by sixfoottallrabbit on 2007-01-19
Too bad the settings don't work on the SVN version, but yeah, good going guys on getting it running. Hope to see the official release soon.

---

### Post by starfire1983 on 2007-01-19
I was having this same problem and upgrading to the SVN version helped. After adding the repositories for the SVN (easily found on the Beryl forums) Update Manager quickly brought a notice that there were updates and it was all for beryl. This is some really cool stuff. Never thought I'd see the day when Linux could implement a OS X-style UI.

---

### Post by hollerith on 2007-01-19
Does not work for me and can't rollback back to 1.4.

---

### Post by rabid emu on 2007-01-19
In Synaptic, go up to the top menu and select 'package' and then 'force version' and select version 1.4 for every package related to beryl.

---

### Post by PriceChild on 2007-01-20
[B][COLOR=Red]Please DON'T use svn unless you are going to be contributing to bug triaging/development.[/COLOR]

[/B]For everyone else. Either use synaptic to revert all beryl packages down to 0.1.4 OR use metacity and wait for the packages later today.

---

### Post by mike00 on 2007-01-20
I tried this upgrade and it made a mess of things for me. I could only have beryl running for a few moments before it crashed. 
Everything was fine with the previous version so I was a bit annoyed by this. I tried downgrading but no luck.
Fortunately I had just made a backup image of my main partition just before this update so I can restore from that. (a well timed backup I  think :D ) I hope a working update is released soon...

---

### Post by hollerith on 2007-01-20
> **PriceChild said:**
> [B][COLOR=Red]Please DON'T use svn unless you are going to be contributing to bug triaging/development.[/COLOR]

[/B]For everyone else. Either use synaptic to revert all beryl packages down to 0.1.4 OR use metacity and wait for the packages later today.

I would GLADLY go back to 0.1.4.  I have NOT been able to do this using the force-version method described.  Perhaps a code snippet?  I have also tried the latest out 'stable' and it still doesn't work.  The only version working (and not really working working ) is the one particular svn repository.  I have submitted bug reports for 0.1.4 but the crash handler doesn't seem to work in the version I have installed.

---

### Post by ronmarley1 on 2007-01-20
> **PriceChild said:**
> [B][COLOR=Red]Please DON'T use svn unless you are going to be contributing to bug triaging/development.[/COLOR]

[/B]For everyone else. Either use synaptic to revert all beryl packages down to 0.1.4 OR use metacity and wait for the packages later today.
Hey Pricey,
Thanks for the update.  I'm just going to use Metacity and wait for the update.  However, I had forgotten how boring things are without Beryl!  Keep up the good work.

---

### Post by Belyel on 2007-01-20
> **ronmarley1 said:**
> Hey Pricey,
Thanks for the update.  I'm just going to use Metacity and wait for the update.  However, I had forgotten how boring things are without Beryl!  Keep up the good work.

I use metacity most of the time cause I haven't taken the time to tweak beryl so it doesn't make my ssh x-windows transparent, but I love having beryl around for times when I'm not working on my research.  I think I speak for all of us on the forums when I say thanks for keeping us posted on the updates and timeline for a fix for this.  I'm just happy to have beryl to show off when it's working!  And for people who are complaining: remember that this is still considered alpha software (switching to beta with this release, i believe), so it WILL have bugs and it may be unstable.  Just have patience and enjoy what you have when you have it.

> **hollerith said:**
> I would GLADLY go back to 0.1.4.  I have NOT been able to do this using the force-version method described.  Perhaps a code snippet?  I have also tried the latest out 'stable' and it still doesn't work.  The only version working (and not really working working ) is the one particular svn repository.  I have submitted bug reports for 0.1.4 but the crash handler doesn't seem to work in the version I have installed.

I have the same problem.  The key here is to do a complete uninstall/purge of the beryl packages through synaptic, then click on the package, without selecting to install it, and go to the Package menu then select "force version..."  This will allow you to only install 0.1.4 and its dependencies.  If you leave the installation packages for 0.1.99 and have some packages that are 0.1.4 and some that are 0.1.99, you'll just keep getting broken package errors and beryl won't work.  Remember: uninstall and purge 0.1.99 first, then reinstall forcing 0.1.4.

---

### Post by arsenaltengu on 2007-01-20
The 0.1.99+0.2.0-beta1 works for me if not a little heavy on the memory,
the settings manager looks amazing! 

well done =D>

---

### Post by medley on 2007-01-20
> **QuinnStorm said:**
> We're working as I type this on getting beta2 (0.1.99.1) put together to fix these issues.  The release was botched, and I apologize.  I wasn't managing effectively, but that will change.

Hi QuinnStorm

I'm writing you because it seems you're somehow involved with Beryl development. I've been trying to get it running for several weeks, and a couple nights ago with the released upgrade that seemed to give everyone else so much trouble, it worked all of a sudden. It was very impressive, and I think I suits how I like to use a desktop. However, out of curiousity, I ended by kde session to see if it would start up again when I logged back in. It did not, and hasn't worked since. It is exhibiting the same behaviour as before the upgrade.

My environment is
Kubuntu Edgy
NV FX 5200 using 97.46 (didn't work with 97.42 or the version I was using before that either)
AMD 2400+
780M ram

The fact that I was able to use it for several hours after the upgrade without any problems tells me that it's unlikely to be a driver problem.

The behavior I see is, when I log out and log in with Beryl as the session type, all of the desktop windows no longer have frames or controls. And Beryl is not functioning as far as I can tell. Beryl-manager is running in System Guard, but doesn't seem to be functioning.

I have confirmed GL acceleration is enabled via glxinfo. If I start with a kde session, go to a konsole and type beryl-manager, I don't get any errors and the ruby icon appears in the task bar. However, if I try to change anything, the the window controls disappear and beryl crashes with a message that says 'the composite manager has crashed twice within one minute and will be disabled for this session'. It falls back to kde. In konsole it says "trying '/home/phil/.xcompmgr' as configfile", then "finished parsing the configfile". Next line says "kwin: Fatal IO Error: client killed". Then it looks like it tries to read the config file again, and I presume that's when I get the message at the desktop about the comp manager crashing twice, etc.

The fact that I have had beryl running, once initially a couple of weeks ago (until I logged out and back in) and again after this upgrade, with the same mode of failure, leads me to wonder if it is a problem with some configuration files not being writable, or accessible?

I'd sure appreciate your help. Beryl looks great; I wish I could use it!

Thanks for your help.

---

### Post by jsully1 on 2007-01-20
You'd probably be better off putting that in a new thread.

---

### Post by medley on 2007-01-20
> **jsully1 said:**
> You'd probably be better off putting that in a new thread.

Ya, I appreciate that, except that I need to get help from somebody who may know what's going on. I've started at least two other threads about this and haven't gotten any help beyond the standard answers.

(I'm a desperate man](*,) )

---

### Post by NickPresta on 2007-01-20
> **hollerith said:**
> I would GLADLY go back to 0.1.4.  I have NOT been able to do this using the force-version method described.  Perhaps a code snippet?  I have also tried the latest out 'stable' and it still doesn't work.  The only version working (and not really working working ) is the one particular svn repository.  I have submitted bug reports for 0.1.4 but the crash handler doesn't seem to work in the version I have installed.

This is how I did it (Anything after the hash is a comment):

`sudo apt-get install aptitude` # You might need to install this. You might not. If you don't skip this line
`sudo aptitude purge beryl-core`
`sudo aptitude purge beryl-manager`
`sudo aptitude purge beryl-plugins`
`sudo aptitude purge beryl-plugins-data`
`sudo aptitude purge beryl-settings`
`sudo aptitude purge emerald`
`sudo aptitude purge libberyldecoration0`
`sudo aptitude purge libberylsettings0`
`sudo aptitude purge libemeraldengine0`
# I needed to downgrade each package individually.
# Aptitude will ask you if you want to downgrade these packages (use y/n/q).
# You should see (beryl installed package) -> (beryl downgraded package).
# Check that the package on the right is 0.1.4 (if it is on the left side, you already downgraded it).
# You can check your beryl-manager version after all this with `beryl-manager --version`

I hope that helps. I downgraded just fine.

---

### Post by kilroy4231 on 2007-01-20
I upgraded to beryl-core 0.2.0-svn from the 0.1.9 or whatever it was and i still have the same errors as before.....which were that I could'nt see the borders around the windows...will try and roll back alittle later

---

### Post by danhm on 2007-01-20
> **medley said:**
> Hi QuinnStorm

I'm writing you.....


I would recommend reposting that on the [offical Beryl Forum](http://forum.beryl-project.org/).


Good luck, medley!

---

### Post by BOBSONATOR on 2007-01-20
Hooray its working now, but my settings manager is borked.

New features are sick!

---

### Post by danhm on 2007-01-20
Yeah, the packages in the repository have been updated and work now.


Looking good!

---

### Post by akniss on 2007-01-20
0.1.99.2 just hit the us repos... giving it a try now.

---

### Post by Spr0k3t on 2007-01-20
1.99.2 works great here.  Using Intel 915 chipset and is smooth, better than 0.1.4 on this laptop.

---

### Post by GCT on 2007-01-20
I rolled back from the SVN packages for the new update, but I'm still seeing "Beryl SVN" on the splash screen when it starts, and my whole screen turns white =(

---

### Post by danhm on 2007-01-20
> **GCT said:**
> I rolled back from the SVN packages for the new update, but I'm still seeing "Beryl SVN" on the splash screen when it starts, and my whole screen turns white =(

Try completely removing the packages before installing 0.1.99.2

---

### Post by PriceChild on 2007-01-20
0.2.0-beta2 is out... enjoy

---

### Post by GCT on 2007-01-20
> **danhm said:**
> Try completely removing the packages before installing 0.1.99.2

I did a complete removal before I updated, still no dice.  I was getting a white screen when it updated to 0.1.99 (when it didn't segfault).  

> 0.2.0-beta2 is out... enjoy

Is that going to be on the repos or is that SVN?

---

### Post by danhm on 2007-01-20
> **GCT said:**
> I did a complete removal before I updated, still no dice.  I was getting a white screen when it updated to 0.1.99 (when it didn't segfault).  



Is that going to be on the repos or is that SVN?

It's in the repos. Hope it fixes your white screen of death!

---

### Post by revertex on 2007-01-21
1.99.2 is rock solid as usual, windows thumbnails are pretty impressive in this release, and seems less cpu intensive than previous releases.

If someone else still getting troubles, remove all beryl an emerald packages, including configurations, synaptic does it, or use apt-get autoremove feature, and start with a clean enviroment.
Don't forget your home config files

```
mv $HOME/.beryl $HOME/.beryl.old && mv $HOME/.emerald $HOME/.emerald.old
```

---

### Post by GCT on 2007-01-21
> **danhm said:**
> It's in the repos. Hope it fixes your white screen of death!

Still not seeing it, which repository is it on?

---

### Post by danhm on 2007-01-21
> **GCT said:**
> Still not seeing it, which repository is it on?

The Beryl Project one.

A segment from my sources.list:

```

## Beryl!
deb http://ubuntu.beryl-project.org/ edgy main
```

---

### Post by GCT on 2007-01-21
> **danhm said:**
> The Beryl Project one.

A segment from my sources.list:

```

## Beryl!
deb http://ubuntu.beryl-project.org/ edgy main
```

Hmm yeah I've got that one, but it's still not showing up in synaptic after i do an update. Oh well, maybe tomorrow =(

---

### Post by wylie98 on 2007-01-21
Hi All, 
I just switched to the new version of beryl and now all new windows i open appear behind the current ones. This is starting to drive me nuts because dialogue boxes appear behind stuff i have open without me realising or being able to act on them. Any help appreciated.

---

### Post by PriceChild on 2007-01-22
> **wylie98 said:**
> Hi All, 
I just switched to the new version of beryl and now all new windows i open appear behind the current ones. This is starting to drive me nuts because dialogue boxes appear behind stuff i have open without me realising or being able to act on them. Any help appreciated.Change FSP to a lower value.

---

### Post by revertex on 2007-01-22
rdesktop is totally transparent!

even with XLIB_SKIP_ARGB_VISUALS=1

---

### Post by fxandrei on 2007-02-01
i have a problem .. ive updated beryl and it didnt work anymore.. so i did the downgrade thing ...
but i have another problem now.. and can't enter in beryl settings manager ... i click on it and nothing happens ... what can i do ?

---

### Post by quark_77 on 2007-02-01
fxandrei: Can you downgrade emerald? I couldn't, that is why I'm wondering!! I use force version then select any lower version but emerald always reverts to the most recent version... not sure why. Perhaps it is worth checking whether you have different components of the various dependencies of Beryl just to make sure? Not sure if I'm pointing out the obvious here.

Anyway, just to report I had exactly the same problem with the upgrade between 0.1.99.2 and 0.1.9999.1.

I got around it by setting my repository to: deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn which I found on the Beryl-Project.org wiki for setting up Beryl on Ubuntu. Using version 0.2.0+svn... something and it runs fine apart from a stubborn refusal to disable the desktop cube.

I tried the svn method but have no idea how to use svn really so I couldn't build Beryl from the sources... 

Hope this helps

Quark_77

---

### Post by quark_77 on 2007-02-03
I have found a way to downgrade Emerald even if, like me, Synaptic's "Force Version" doesn't work [it flashes back to the latest version when you deselect Emerald].

The answer is to use aptitude... either using gnome-terminal or recovery console. Then, open aptitude, select installed packages, x11 and go down to beryl. press enter, go down to previous versions, select the version you want and press +. If it asks you to examine broken dependencies, press e and downgrade any related packages. Repeat for all the parts of Beryl [eg emerald, libemeraldengine0, libberyldecoration0 etc]

Hope this helps for people, like me, for whom this is all rather a new experience!!

Quark_77

---

### Post by Metallinut on 2007-02-05
Has anyone started using the newest released version with XGL and an ATI card?  Mine broke like eveyone else's, and I think (in my Windows side at work :() that system update has me up to date on beryl.  I'll try removing everything and installing fresh and anew...

But yeah, just wanted to see if anyone is having success with the new Beryl with XGL and fglrx on ATI.

Thanks for making such a COOL thing! (Beryl)

---

### Post by Robor on 2007-02-05
> **Metallinut said:**
> Has anyone started using the newest released version with XGL and an ATI card?  Mine broke like eveyone else's, and I think (in my Windows side at work :() that system update has me up to date on beryl.  I'll try removing everything and installing fresh and anew...

But yeah, just wanted to see if anyone is having success with the new Beryl with XGL and fglrx on ATI.

Thanks for making such a COOL thing! (Beryl)

I didn't see this thread until after I got my Beryl / AiGLX working again.  I kept getting dependency errors related to beryl-settings.  Couldn't apt-get -f install.  Same error over and over again.  I went into Symanptec and uninstalled everything related to Beryl then reinstalled it.  That still didn't work - in fact my system then booted to only flash the desktop quickly then back to the command line.

Then I remembered I had previously tried a script to install Beryl / AiGLX but it failed due to the previous dependency errors.  I got the script from here:  [http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html)  Worked for me - maybe give it a try?

---

### Post by dr_d on 2007-02-06
has anybody else managed to get 0.2.0-beta2 from ubuntu.beryl-project.org?

i saw some screenshots of 0.2.0 today and it looks almost too good to be true.

cheers!

---

### Post by dr_d on 2007-02-06
yeah something definitely seems to be wrong... if i browse the repo via http ([http://ubuntu.beryl-project.org/dists/edgy/main/](http://ubuntu.beryl-project.org/dists/edgy/main/)) there only seems to be version 0.1.9999.1

---

### Post by Metallinut on 2007-02-06
Same thing here...and I've had a hell of a time trying to revert to an older version with synaptic.  

As soon as you force version on one thing, another piece upgrades, or gets removed...I couldn't get it all down to ONE version.  So I'm still up the creek.

I'm hoping 0.2 will fix my probs, but still not up on beryl-project...

---

### Post by disturbedite on 2007-02-06
i run kubuntu btw.

but i managed to "fix" the upgrade issue by first uninstalling all beryl related packages.  then reinstalling all of them except the plugins-extra.  (i think someone mentioned that it was integrated into beryl).  the upgrade work successfully.......except for one thing...
the window decorations/borders don't work.  there are no decorations or borders of any type rendered....so its effectively useless.

that was a couple of days ago and i haven't used beryl since then, i guess i'm just waiting for an update.

---

### Post by shareMenaPeace on 2007-02-06
REINSTALL BERYL GUIDE

[http://ubuntuforums.org/showthread.php?t=354228](http://ubuntuforums.org/showthread.php?t=354228)

---

### Post by PriceChild on 2007-02-06
0.2.0 DOES NOT EXIST

0.1.9999.1~0beryl1 is 0.2.0-RC2 (release candidate 2)

---

### Post by dr_d on 2007-02-06
ah i see... thanks for clearing that up PriceChild.

well seeing as everybody seems to be having problems i think ill wait until 0.2.0 gets officially released before i install beryl. lets hope its soon :)

---

### Post by dr_d on 2007-02-07
for anyone else waiting for beryl 0.2.0... i was just reading the beryl website and it seems the target release date is 20th feb.

i'm sure it'll be worth the wait.

cheers!

---

### Post by PriceChild on 2007-02-07
> **dr_d said:**
> i was just reading the beryl website and it seems the target release date is 20th feb.That is correct: [http://www.beryl-project.org/roadmap.php](http://www.beryl-project.org/roadmap.php)

---

### Post by WijbrandSchaap on 2007-02-07
> **quark_77 said:**
> I have found a way to downgrade Emerald even if, like me, Synaptic's "Force Version" doesn't work [it flashes back to the latest version when you deselect Emerald].

The answer is to use aptitude... either using gnome-terminal or recovery console. Then, open aptitude, select installed packages, x11 and go down to beryl. press enter, go down to previous versions, select the version you want and press +. If it asks you to examine broken dependencies, press e and downgrade any related packages. Repeat for all the parts of Beryl [eg emerald, libemeraldengine0, libberyldecoration0 etc]

Hope this helps for people, like me, for whom this is all rather a new experience!!

Quark_77
Using aptitude is not really my thing. I managed to downgrade using synaptic. It takes some doing: i just downgraded every beryl component one by one, and left emerald unchanged. Only thing to watch is: when you've downgraded a package, some other packages get an upgrade-marker. Solution: remove those markers every time you downgrade a package and you're fine. Everything is now back to 99.2, emerald rests at 1.9999.1, also working fine. Took 5 minutes.
Hope this helps...

---

### Post by Metallinut on 2007-02-07
Yeah, I'm still screwed after downgrading to 0.1.4 with my stupid ATI card.  I'm on 386 with an ATI x1400 using fglrx, running XGL.  So annoying.  I wish ATI cards would just work as easily as everyone's nVidia seems to.  ARGH!  

Any word on if beryl 0.2 works with my setup (XGL, fglrx)?

---

### Post by glabouni on 2007-02-08
> downgrade to 0.1.99.2
```
sudo apt-get remove 'beryl*'
sudo apt-get install beryl=0.1.99.2~0beryl1 beryl-core=0.1.99.2~0beryl1 beryl-manager=0.1.99.2~0beryl1 beryl-plugins=0.1.99.2~0beryl1 beryl-plugins-data=0.1.99.2~0beryl1 beryl-settings=0.1.99.2~0beryl1 beryl-settings-bindings=0.1.99.2~0beryl1 emerald=0.1.99.2~0beryl1 libberyldecoration0=0.1.99.2~0beryl1 libberylsettings0=0.1.99.2~0beryl1 libemeraldengine0=0.1.99.2~0beryl1 emerald-themes=0.1.99.2~0beryl1 -V
```
from [Upgrade Broke Beryl]("http://forum.beryl-project.org/viewtopic.php?f=36&t=2977&st=0&sk=t&sd=a") on the beryl forums

---

### Post by jpneron on 2007-02-08
For what it's worth, I also had trouble with the upgrade to Beryl. It just wouldn't run. When I tried to run it, it would crash and drop back to metacity.

I finally noticed that running 'beryl-xgl' would seg fault, but running 'beryl' all by itself worked, so as a complete, brute force, totally kludgy work around, I linked beryl-xgl to beryl:
```

sudo mv /usr/bin/beryl-xgl /usr/bin/beryl-xgl.orig
sudo ln -s /usr/bin/beryl /usr/bin/beryl-xgl
```

And now it all works. 

Warning: I'm not sure will happen when the next release comes out. The link may or may not be preserved, which may or may not be a good thing. Probably the safest thing would be to 

```
sudo rm -f /usr/bin/beryl-xgl
```

before the upgrade. 

I'm running Edgy with Nvidia drivers.

Hope this helps.

Jean

---

### Post by PriceChild on 2007-02-08
jpnernon were you previously starting beryl with beryl-manager or beryl-xgl?

---

### Post by Metallinut on 2007-02-08
glabouni you're my hero!  

I've finally got beryl working again using that method you quoted!  Huzzah!

---

### Post by Metallinut on 2007-02-09
> **PriceChild said:**
> Change FSP to a lower value.

Sorry to be stupid, but exactly what setting is FSP, and where would I find it?

Thanks,

---

### Post by PriceChild on 2007-02-09
Open up beryl-settings manager and its on the front page staring at you.

Stands for "Focus Stealing Protection"

---

### Post by dr_d on 2007-02-21
Hey guys anybody know what's the deal? It's Feb 21st and I still can't find any beryl0.2.0 in ubuntu.beryl-project.org.


Any info would be much appreciated!

---

### Post by PriceChild on 2007-02-23
Patience :)

We'll poke it onto the repos when its ready :)

---

### Post by dr_d on 2007-02-26
so beta2 is working fine for everybody? i'm starting to feel some cube-withdrawals so i think i'll install the beta now and then hopefully it'll be no problem to upgrade to 0.2.0 later when it comes out ... 

:popcorn:

---

### Post by dr_d on 2007-02-26
DAMN!! it completely rocks! The Beryl team have done a bang-up job and it's only the beta. For anyone else considering installing the beta, it seems rock solid.

wow. just wow.

---

