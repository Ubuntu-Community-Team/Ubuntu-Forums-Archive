---
title: "Cinnamon crashes on login after upgrade to 3.2 on Ubuntu 16.04"
date: 2016-11-16
forum: Desktop Environments
---

### Post by livinwell on 2016-11-16
Had been running Ubuntu 16.04 with Cinnamon 3.0 for some time now, and it was working fine.

To get Cinnamon 3.0, I had added the PPA embrosyn/cinnamon

The last update that I got from Updater application included an upgrade to the kernel along with an upgrade to Cinnamon. There were problems with the update - some files were not installed. Upon completion, I got a message to perform a partial upgrade to fix problems. I did this and it removed Cinnamon.

I attempted to reinstall Cinnamon (from PPA), but got the message about files couldn't be installed, so I removed the PPA above and installed the official version, from Ubuntu.

When I rebooted, after reinstallation, Cinnamon was broken - could not click items in the panels, and right-click acted as if I did the action on the desktop. Everything else worked, I could even access the menu, via the super key, and access applications from it.

Since Google was  unhelpful in finding a solution to the unclickable panels - I tried all that I found, but none worked. I tried uninstall/reinstall for both cinnamon and cinnamon-core, but no joy.

Figured that, maybe, since I was using 3.0 and the official version is 2.8, that my settings were incompatible, so I reinstalled the PPA and performed update and upgrade (all from terminal). The upgrade appeared to go smoothly - no error messages. Reboot results in Cinnamon crash on login. Attempted cinnamon --replace in terminal, but that resulted in the terminal being locked and the following error:

Clutter:ERROR:x11/clutter-stage-x11.c:1290:clutter_x11_get_stage_window: assertion failed: (CLUTTER_IS_STAGE_X11 (impl))
Aborted (core dumped)

I opened a second terminal to reboot and get out of fallback mode, but  could not type in it - luckily had gedit open and copy/pasted what was  needed, which worked for some reason.

Now using compiz desktop, but I'd like to get back to Cinnamon, without losing my settings, if possible.

Any thoughts on what the error means? Any solution come to mind?

Although I'm not 100% newbie, there is MUCH I still need to learn about linux. Please keep responses simple.

---

### Post by T.J. on 2016-11-16
> Had been running Ubuntu 16.04 with Cinnamon 3.0 for some time now, and it was working fine.

To get Cinnamon 3.0, I had added the PPA embrosyn/cinnamon


I do not want to seem rude or unhelpful, but any time you use a PPA archive, you are doing so at your own risk.  The code may not have been compiled properly or even be stable to begin with.  It can damage your install, perhaps beyond repair.

> Figured that, maybe, since I was using 3.0 and the official version is 2.8, that my settings were incompatible, so I reinstalled the PPA and performed update and upgrade (all from terminal). The upgrade appeared to go smoothly - no error messages. Reboot results in Cinnamon crash on login. Attempted cinnamon --replace in terminal, but that resulted in the terminal being locked and the following error:

Clutter:ERROR:x11/clutter-stage-x11.c:1290:clutter_x11_get_stage_window: assertion failed: (CLUTTER_IS_STAGE_X11 (impl))
Aborted (core dumped)

You should never test (or even login) on your own day-to-day account using untested PPA code.  It may migrate your settings, forcing you to entirely purge them from your home folder before the interface will stabilize. Always create a second user account to login when testing new code from a PPA.  If that account gets corrupted, you do not lose anything vital.

The fact that it actually core dumped is not a good sign. That means that there is a severe bug, usually - either in Cinnamon itself or one of the support libraries.


> Now using compiz desktop, but I'd like to get back to Cinnamon, without losing my settings, if possible.

My SIMPLE advice to you is to purge the PPA, go back to 2.8 for the time being until 3.2 is better tested.  You may have to dump your settings to ensure stable behavior.  If you need help doing so, please let me know.  Probably the BEST advice if you are going to use untested code would be  to contact the Cinnamon developers and ask them what they are using as a  reference platform to build and test it.  (My guess would be Mint.)   That would be the best version for you to use if you want the latest and  greatest of Cinnamon without the bugs, and would probably leave you a happier user.

That said, you can always try purging and reinstalling clutter before the rest of cinnamon.  You can also dump your settings to see if old settings are what causes clutter to crash.  I doubt that though.

---

### Post by livinwell on 2016-11-16
No offense taken. I do understand that there are risks involved in using PPA, but that was the only way to get away from that God awful unity, to begin with, and I guess I got a bit complacent. Prior to my upgrade to 16.04, I was using the official release version of Cinnamon, but 3.0 was stated as being stable (which I found to be true), and a little cleaner interface, so I went back to PPA to get it.

This particular PPA has builds specifically for Ubuntu.

Had not thought about creating a 'dummy' user to test out updates. I think I'll get that implemented, once I get this straightened out - want to get back to a stable setting before I start adding stuff.

I agree that it is not likely that the settings are what is causing the crash, but always a consideration when nothing else works.

I do have backups of my settings, prior to the update, so all is not lost if settings are cleared - was just hoping not to have to go that route. I guess that settings from 3.0 will work with 2.8. I installed 3.0 when I upgraded to 16.04 (clean install), so I've never had any settings for 2.8.

I have seen a purge PPA command somewhere, during my searching, but don't recall where, offhand. If you would be so kind as to provide the command, I'd much appreciate it. I assume that the PPA purge will remove settings too, or do I assume too much?

I wouldn't have gone back to the PPA if 2.8 was working properly - will cross that bridge if/when I get to it.

---

### Post by T.J. on 2016-11-16
It's ppa-purge, I believe. You may actually have to install ppa-purge manually - best to check.  Personally, I prefer Debian so the help I can offer is limited in this respect.  I have 16.04 installed for puttering about and testing custom packages - but I never use other people's PPAs.  I build the source myself. 

I have had too many bad experiences of poorly packaged code causing data corruption.  The "advantage" of Ubuntu having so many PPAs instead of a central repo of solid tested community rated backports is IMHO a total failure.  That and the fact that Debian Testing/Unstable packages are used as community packages in an LTS has actually turned me off from Ubuntu.  Often the PPAs are just too darn risky, or and the community supported packages don't even work at all.  

An example that comes to mind would be blogilo. The 16.04 version looks like it was drawn straight from Debian Testing/Unstable, and not even tested to make sure it works.  If Canonical is going to pull it in to an LTS without patching it after 6 months, a bug report seemed redundant. I'm not throwing stones, but it's a bad policy.  LTS versions should be limited to software that actually works instead of segfaulting.

---

### Post by livinwell on 2016-11-17
You were right about having to install ppa-purge. I did so, and ran it with the PPA. All did not go to plan, but it did appear to work, to a point. I got a bunch of warnings about downgrading and some about bluetooth stuff, which I'd removed earlier, since I don't use it. At the end it showed the following error:

Errors were encountered while processing:  /var/cache/apt/archives/nemo_2.8.6-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
/usr/sbin/ppa-purge: line 191: aptitude: command not found
Warning:  Something went wrong, packages may not have been reverted

I don't believe that aptitude is installed on my system, so that would explain that portion.

Since it appeared that things didn't go as I'd like, I went ahead and did the following:

Ran apt-get -f install, as suggested in the terminal, which removed Cinnamon and Nemo

Ran apt-get purge cinnamon cinnamon-core

Ran apt-get autoremove

Ran apt-get install cinnamon cinnamon-core

I then restarted the system, choosing Cinnamon as my desktop.

Lo and behold, Cinnamon (2.8) is now working as it should. Surprisingly, my settings were not lost - I thought that the purge option should have deleted them, but the background, width and font of the panels and app lauanchers were all in place. A very pleasant surprise.

Thanks for your help.

---

### Post by T.J. on 2016-11-17
> **livinwell said:**
> You were right about having to install ppa-purge. I did so, and ran it with the PPA. All did not go to plan, but it did appear to work, to a point. I got a bunch of warnings about downgrading and some about bluetooth stuff, which I'd removed earlier, since I don't use it. At the end it showed the following error:

Errors were encountered while processing:  /var/cache/apt/archives/nemo_2.8.6-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
/usr/sbin/ppa-purge: line 191: aptitude: command not found
Warning:  Something went wrong, packages may not have been reverted

I don't believe that aptitude is installed on my system, so that would explain that portion.

Since it appeared that things didn't go as I'd like, I went ahead and did the following:

Ran apt-get -f install, as suggested in the terminal, which removed Cinnamon and Nemo

Ran apt-get purge cinnamon cinnamon-core

Ran apt-get autoremove

Ran apt-get install cinnamon cinnamon-core

I then restarted the system, choosing Cinnamon as my desktop.

Lo and behold, Cinnamon (2.8) is now working as it should. Surprisingly, my settings were not lost - I thought that the purge option should have deleted them, but the background, width and font of the panels and app lauanchers were all in place. A very pleasant surprise.

Thanks for your help.

You're welcome.

Your settings are in hidden folders in your home holder, so they are not touched in a purge.  

Aptitude is the Debian advanced package manager. It's like apt-get on steroids. I highly recommend it, even on Ubuntu, for fixing breakage.  It is very good at solving broken dependencies, especially in chains.  I do not know why Ubuntu removes it from the default install.  IMO, it is a stupid thing to do.  I NEVER install Ubuntu without it.  If it was not at least available, I would not use Ubuntu as it would be too great a loss in comparison to Debian.  It has a LOT of useful features.  You can get the same results with various commands such as apt-cache, but aptitude puts them all in one place and has a Ncurses UI.

---

### Post by livinwell on 2016-11-17
> **T.J. said:**
> You're welcome.

Your settings are in hidden folders in your home holder, so they are not touched in a purge.  

Aptitude is the Debian advanced package manager. It's like apt-get on steroids. I highly recommend it, even on Ubuntu, for fixing breakage.  It is very good at solving broken dependencies, especially in chains.  I do not know why Ubuntu removes it from the default install.  IMO, it is a stupid thing to do.  I NEVER install Ubuntu without it.  If it was not at least available, I would not use Ubuntu as it would be too great a loss in comparison to Debian.  It has a LOT of useful features.  You can get the same results with various commands such as apt-cache, but aptitude puts them all in one place and has a Ncurses UI.

I understand where settings are, but it was my understanding that using purge with apt-get cleared those directories as well as removing the package. Mebbe I missed something when I was reading about apt-get...

I think that aptitude was a part of Ubuntu at one time, but I could be mistaken. The command seems really familiar, but I know that it is not installed in my current setup. I believe I'll remedy that situation, on your recommendation.

Coming from DOS and OS/2 background (I've never used Windows as a primary OS), I was used to the command line. OS/2, however, had a fantastic desktop and such good GUI utilities that  I got spoiled and got away from the command line. My son changed me over to Ubuntu from eComStation (OS/2 after IBM gave  it up) because he said he couldn't build me a box, for it, due to a  lack of drivers for newer equipment. Still on the learning curve when it  comes to the command line in Ubuntu. Not afraid of it, just don't know  much about the commands, and much of the documentation is a bit cryptic  if you don't know the terminology. I need to study up and use it more.

Getting off topic, here. Would like to ask further questions regarding aptitude if you'll contact me via georgianatives.net (my homepage).

---

### Post by T.J. on 2016-11-18
> **livinwell said:**
> I understand where settings are, but it was my understanding that using purge with apt-get cleared those directories as well as removing the package..

Global settings are purged. Personal settings are kept in your folder.  You can contact me via private message here on the board, then we can talk about email or whatever.

---

