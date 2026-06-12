---
title: "Problem with Adobe Flash Player on Ubuntu 9.04"
date: 2009-04-23
forum: General Help
---

### Post by charleskw on 2009-04-23
So I just clean installed Ubuntu 9.04 on my lap top and I can't seem to install adobe flash player. It worked fine with Ubuntu 8.10. When I try to install the Adobe flash player plug in for Firefox it has an error message. Any idea for help is appreciated.

---

### Post by joeyknuccione on 2009-04-23
Post the error message.

---

### Post by charleskw on 2009-04-23
> **joeyknuccione said:**
> Post the error message.

So, when I go to a page that requires adobe flash player and the message appears at the top that says that i need to install missing plug-ins I click on it, press install, then this message appears:

Could not find package SWDEF- Mozilla

---

### Post by nandemonai on 2009-04-23
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by charleskw on 2009-04-23
> **nandemonai said:**
> ```
sudo apt-get install flashplugin-nonfree
```

My result was :
E: Couldn't find package flashplugin-nonfree

---

### Post by pw_f100_220 on 2009-04-23
charleskw, I did the exact things but after some restarts playing with other things I tried flashplugin-nonfree and it was able to install.  I guess just put it back on your list of things to do with Jaunty for a few minutes then try it again.

Unfortunately, I can't get Hulu.com to work...youtube works...but I don't want youtube.

---

### Post by nandemonai on 2009-04-23
> **charleskw said:**
> My result was :
E: Couldn't find package flashplugin-nonfree

It's in the multiverse. You'll have to enable the repo.

---

### Post by nandemonai on 2009-04-23
> **pw_f100_220 said:**
> charleskw, I did the exact things but after some restarts playing with other things I tried flashplugin-nonfree and it was able to install.  I guess just put it back on your list of things to do with Jaunty for a few minutes then try it again.

Unfortunately, I can't get Hulu.com to work...youtube works...but I don't want youtube.

I can't test hulu.com for you as I'm not in the states. Sorry. Should work. I've not come across anything I couldn't play.

I'd suggest looking into the ubuntu-restricted-extras package.

---

### Post by pw_f100_220 on 2009-04-23
I suppose I enabled the multiverse along the way as well...whoops
Just fixed my flash problem...swfdec was hindering everything...REMOVED AND VOILA!!

flashplugin-nonfree all the way!

thanks for the insight nandemonai

---

### Post by nandemonai on 2009-04-23
Ah yeah I should have mentioned, only having one flash player really helps ;)

---

### Post by pw_f100_220 on 2009-04-23
Yeah...I forgot about that one...

and on second thought, the video is really choppy, even when fully buffered.  It looks like a lot of people have had this problem, but no one had any answers that I could find

---

### Post by nandemonai on 2009-04-23
Could be due to your video driver.

What card and what drivers?

I'm running nvidia with the restricted drivers here and it's primo.

---

### Post by pw_f100_220 on 2009-04-23
intel x1300 i think...do you have a way to check all of that?  It's been a while

---

### Post by nandemonai on 2009-04-23
> **pw_f100_220 said:**
> intel x1300 i think...do you have a way to check all of that?  It's been a while

```
lspci | grep VGA
```

Intel could be part of the problem. I've been seeing numerous issue with it in Jaunty.

---

### Post by pw_f100_220 on 2009-04-23
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

?

---

### Post by codeseer on 2009-04-23
Jaunty 32-bit or 64-bit?

---

### Post by pw_f100_220 on 2009-04-23
32...Thinkpad T61

---

### Post by nandemonai on 2009-04-23
> **pw_f100_220 said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

?

That's certainly Intel. I'd do some searching here on the forums, there seems to be many a headache with Intel this release.

---

### Post by codeseer on 2009-04-23
Clean up past installation of Flash:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

Download and install new .deb Flash from here: [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

---

### Post by charleskw on 2009-04-23
> **nandemonai said:**
> It's in the multiverse. You'll have to enable the repo.

What exactly do I need to do?

---

### Post by nandemonai on 2009-04-23
> **charleskw said:**
> What exactly do I need to do?

System -> Administration -> Software Sources

(Ignore my mirror in the attached screenshot)

---

### Post by codeseer on 2009-04-23
> **pw_f100_220 said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

?

The GM965 drivers are built in with the kernel.

Take a look at this: [https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Other%20known%20issues]("https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Other%20known%20issues")

---

### Post by pw_f100_220 on 2009-04-23
hmmmm...I did some purging your way codeseer, then reinstalled flash...it's still choppy, so I tried "MigrationHeuristic" "greedy" and was blessed with incessantly blinking gnome panels...which i'm not ok with.  My xorg.conf is now back to default yet the blinking panels still persist.  I have done a restart and all...this is very interesting, I might install fluxbox sooner than I thought

Thanks for helping so far!  I have not yet begun to fight!

---

### Post by pw_f100_220 on 2009-04-23
I am using dual monitors...that often helps screw things up

---

### Post by codeseer on 2009-04-24
> **pw_f100_220 said:**
> hmmmm...I did some purging your way codeseer, then reinstalled flash...it's still choppy, so I tried "MigrationHeuristic" "greedy" and was blessed with incessantly blinking gnome panels...which i'm not ok with.  My xorg.conf is now back to default yet the blinking panels still persist.  I have done a restart and all...this is very interesting, I might install fluxbox sooner than I thought

Thanks for helping so far!  I have not yet begun to fight!

That is interesting. This and other issues arising makes me want to wait to switch to Jaunty. Besides, my md5sums are both wrong for the 32-bit and 64-bit.

Edit:

From my readings, it seems that a handful of people have had luck by upgrading the kernel to 2.6.30rc3.

---

### Post by pw_f100_220 on 2009-04-24
JUST DO IT!!!  no greater feeling than jumping into the unknown then climbing out of it again with whatever you may learn!  unless of course you have a current project that you need to get done before you can devote your attention to such a crusade.  besides, you seem more experienced and competent with Ubuntu than me.

plus it makes you appreciate a stable install that much more.  I installed Fluxbox and it looks better than ever in Jaunty, even though it's the same Fluxbox.  I didn't see that eyepleaser in my future, but it's now the present! at such a small price!

---

### Post by codeseer on 2009-04-24
Yeah, I've got to keep my system fairly stable until the 6th when college turns out.

---

### Post by MacAlert on 2009-04-24
I'm trying to install Flash but I get a wrong architecure message 'i386'. I am running the 64bit version of Ubuntu. Please help!

EDIT: Never mind, don't know what I did but it is working now.

---

### Post by codeseer on 2009-04-24
> **MacAlert said:**
> I'm trying to install Flash but I get a wrong architecure message 'i386'. I am running the 64bit version of Ubuntu. Please help!

Download it from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract it using: tar zxvf libflashplayer-*.tar.gz

Clean up past installation of Flash:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

Install the new Flash:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins
```

---

### Post by MacAlert on 2009-04-24
> **codeseer said:**
> Download it from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract it using: tar zxvf libflashplayer-*.tar.gz

Clean up past installation of Flash:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

Install the new Flash:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins
```
Where do I save the file from Adobe? Sorry for the dumb questions, very new to Linux.

---

### Post by gabii5 on 2009-04-24
Solved problem with install Adobe Flash Player on Ubuntu 9.04

1.
Removing SwfDec
System > Administration > Synaptic

search for swfdec-mozilla > right click > Mark for Complete Removal > Apply


2.
Adobe Flash Player 10.

install_flash_player_10_linux.deb 
from this address:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

worked for me...

---

### Post by meeples on 2009-04-24
i think i got flash through ubuntu restricted extras in the repo... its easier it downloads all ur mp3 codecs and stuff aswel :)

---

### Post by pw_f100_220 on 2009-04-24
restricted extras didn't get me flash...still a great package though

---

### Post by codeseer on 2009-04-24
> **MacAlert said:**
> Where do I save the file from Adobe? Sorry for the dumb questions, very new to Linux.

Probably the best way to do it is to download it and save it to your Desktop. Then open a terminal (Applications->Accessories->Terminal) and type 'cd ~/Desktop', then type 'tar zxvf libflashplayer-*.tar.gz', then type 'cd libflash' and hit the TAB key to complete the name, then hit Enter. Then you'll want to run all the cleanup stuff. Finally follow that with the 'install the new Flash' part of the instructions.

---

### Post by codeseer on 2009-04-24
> **gabii5 said:**
> Solved problem with install Adobe Flash Player on Ubuntu 9.04

1.
Removing SwfDec
System > Administration > Synaptic

search for swfdec-mozilla > right click > Mark for Complete Removal > Apply


2.
Adobe Flash Player 10.

install_flash_player_10_linux.deb 
from this address:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

worked for me...

That will work for 32-bit users sometimes, though I like telling them to run the cleanup first, to be sure that all the flash stuff is gone and won't conflict; this gets rid of swfdec-mozilla in the process as well as other possible installs.

---

### Post by codeseer on 2009-04-24
> **meeples said:**
> i think i got flash through ubuntu restricted extras in the repo... its easier it downloads all ur mp3 codecs and stuff aswel :)

The version of Flash you get from the repositories like that works well on a lot of stuff, though there are some key sites that it just doesn't work on. This is where you have to clean it up using the process I posted and install the Flash from the official website.

---

### Post by uid0 on 2009-04-24
> **codeseer said:**
> Download it from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract it using: tar zxvf libflashplayer-*.tar.gz

Clean up past installation of Flash:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

Install the new Flash:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins
```


Thanks, codeseer.  This worked just fine for me.  

Interestingly enough, The description in 9.04 Synaptic for flashplugin-nonfree is "This package is a transitional package that can safely be removed after you installed flashplugin-installer."   I don't see a flashplugin-installer package though....

---

### Post by codeseer on 2009-04-24
> **uid0 said:**
> Thanks, codeseer.  This worked just fine for me.  

Interestingly enough, The description in 9.04 Synaptic for flashplugin-nonfree is "This package is a transitional package that can safely be removed after you installed flashplugin-installer."   I don't see a flashplugin-installer package though....

Yeah, there's something different between that package and the official download. I don't know what it is, but it just doesn't work on some websites.

---

### Post by beerdoctor on 2009-04-25
> **joeyknuccione said:**
> Post the error message.

I had a frustrating day after the two and half hour upgrade from Ibex to Jaunty, only to discover that Adobe flash did not work. Tried everything, from synaptic to command line, all it said was Adobe was installed, but it did not work. Finally, when back to 8.1, reinstalled all software applications and everything works fine. I liked the look of Jaunty, but without Adobe flash working properly, it is not a modern computer. Perhaps the problem was the update did not take into account the amd64 architecture? I do not know.

---

### Post by MacAlert on 2009-04-25
> **codeseer said:**
> Probably the best way to do it is to download it and save it to your Desktop. Then open a terminal (Applications->Accessories->Terminal) and type 'cd ~/Desktop', then type 'tar zxvf libflashplayer-*.tar.gz', then type 'cd libflash' and hit the TAB key to complete the name, then hit Enter. Then you'll want to run all the cleanup stuff. Finally follow that with the 'install the new Flash' part of the instructions.

That did it. Thank you very much for your help!!!

---

### Post by markbl on 2009-04-25
codeseer, I replaced the packaged nonfree flash player with the official adobe one as you suggest here but it makes no difference with my laptop intel 945GM video. Flash still runs hopelessly in Jaunty. It was ok on Intrepid.

Just hope ubuntu fix this soon ...

---

### Post by codeseer on 2009-04-25
> **markbl said:**
> codeseer, I replaced the packaged nonfree flash player with the official adobe one as you suggest here but it makes no difference with my laptop intel 945GM video. Flash still runs hopelessly in Jaunty. It was ok on Intrepid.

Just hope ubuntu fix this soon ...

Yeah, it's looking like there's an issue with Intel users and possibly other users. You could try updating to the latest kernel.

---

### Post by DeeRawzzz on 2009-04-25
> **gabii5 said:**
> Solved problem with install Adobe Flash Player on Ubuntu 9.04

1.
Removing SwfDec
System > Administration > Synaptic

search for swfdec-mozilla > right click > Mark for Complete Removal > Apply


2.
Adobe Flash Player 10.

install_flash_player_10_linux.deb 
from this address:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

worked for me...

Thank you so much--worked perfectly!

---

### Post by markbl on 2009-04-25
> **codeseer said:**
> Yeah, it's looking like there's an issue with Intel users and possibly other users. You could try updating to the latest kernel.
FYI I have an almost identical fresh install of Jaunty on my main nvidea based PC and there I use exactly the same firefox directory to my laptop (i.e. it is copied so shares the same plugins/environment etc) with the same version of firefox etc; and here it runs fine. The problem is only on my laptop with the intel video.

I can live with it so I'll wait until something comes through the updates. I like to avoid prodding my machines with spurious packages.

---

### Post by cdwillis on 2009-04-26
I installed ubuntu-restricted-extras and flash is working fine for me. My integrated graphics is the Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03).

---

### Post by Sevis on 2009-04-26
> **codeseer said:**
> ```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```
```
cp: cannot create regular file `/usr/lib/mozilla/plugins/': Is a directory
```

Return this if the directory doesn't exist. Fix:

```
sudo mkdir /usr/lib/mozilla/plugins/
```

---

### Post by markbl on 2009-04-27
I eventually realized that my problem really was not specific to the flash player, my overall X performance was hopeless compared to intrepid with my intel 945GM video card. I followed the procedure given at [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) to upgrade X and my X performance improved heaps. Now flash player runs just find in full screen.

---

### Post by codeseer on 2009-04-27
Thank you, markbl.

---

### Post by snowman14 on 2009-04-27
Sorry im a noob and i just tried to install the .deb package you guys listed earlier

So i put
sudo dpkg -i install_flash_player_10_linux.deb into the terminal and i got this error

dpkg: dependency problems prevent configuration of adobe-flashplugin:
     adobe-flashplugin depends on libcurl3; however:
          Package libcurl3 is not installed

Can somone direct me from here? Thanks!

I figured it out! Learning more each day yay. Flash finally works

---

### Post by codeseer on 2009-04-27
> **snowman14 said:**
> Sorry im a noob and i just tried to install the .deb package you guys listed earlier

So i put
sudo dpkg -i install_flash_player_10_linux.deb into the terminal and i got this error

dpkg: dependency problems prevent configuration of adobe-flashplugin:
     adobe-flashplugin depends on libcurl3; however:
          Package libcurl3 is not installed

Can somone direct me from here? Thanks!

I figured it out! Learning more each day yay. Flash finally works

Great to hear!

For those who may encounter this post and experience missing dependencies, they can be acquired by typing the following in the terminal:

```

sudo apt-get install libcurl3

```

(Replace 'libcurl3' with the name of any other dependency you may be missing).

---

### Post by thebeev on 2009-04-27
Hello all,

First post here.  I've been having issues trying to get the flashplugin to work correctly in firefox.  Read through this entire thread here and still having problems.

Here is my setup, wasn't sure if this should be posted here or in virtualization.

XP Pro64bit host
Xubuntu 9.04 32bit guest
VMware Workstation 6.5.2build 156735
Firefox 3.0.9

This is a **fresh** xubuntu install and downloaded the latest updates.  Basically what happens with flash video's(youtube, hulu etc.) The video comes up but it's like someone is fast forwarding the video.  Kinda funny, but getting fustrating because I've been googling and searching for solutions for the past 2days now.  Of course I'm not getting sound either.  And if it means anything, same issue is happening in opera.

Appreciate the help!

---

### Post by codeseer on 2009-04-27
> **thebeev said:**
> Hello all,

First post here.  I've been having issues trying to get the flashplugin to work correctly in firefox.  Read through this entire thread here and still having problems.

Here is my setup, wasn't sure if this should be posted here or in virtualization.

XP Pro64bit host
Xubuntu 9.04 32bit guest
VMware Workstation 6.5.2build 156735
Firefox 3.0.9

This is a **fresh** xubuntu install and downloaded the latest updates.  Basically what happens with flash video's(youtube, hulu etc.) The video comes up but it's like someone is fast forwarding the video.  Kinda funny, but getting fustrating because I've been googling and searching for solutions for the past 2days now.  Of course I'm not getting sound either.  And if it means anything, same issue is happening in opera.

Appreciate the help!

```
lspci | grep VGA
```

err... what video card?

---

### Post by thebeev on 2009-04-27
> **codeseer said:**
> ```
lspci | grep VGA
```err... what video card?

Sorry about that, that might help It's a ATI Radeon HD 3870x2.

I ran that command in terminal.
```
Desktop$ lspci | grep VGA
00:0f.0 VGA compatible controller: VMware Inc Abstract SVGA II Adapter
```

---

### Post by codeseer on 2009-04-28
> **thebeev said:**
> Sorry about that, that might help It's a ATI Radeon HD 3870x2.

I ran that command in terminal.
```
Desktop$ lspci | grep VGA
00:0f.0 VGA compatible controller: VMware Inc Abstract SVGA II Adapter
```

You probably need the Kernel upgrade.

Just the Kernel specific stuff in step 1: [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by thebeev on 2009-04-28
Thanks Codeseer, I'll give that a try.

---

### Post by thebeev on 2009-04-28
> **codeseer said:**
> You probably need the Kernel upgrade.

Just the Kernel specific stuff in step 1: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Ok did the kernel update in step 1.  Afterwords I installed flash, and... :) the videos play back at a normal speed, woot!  Close firefox, carried on.  Opened firefox at a later time and now the flash videos are back to the "fast forward" playback. :confused:

I'm starting to wonder if it's something to do with my current version of vmware workstation, 6.5.2-156735.  Because ubuntu 9.04 was not listed as a supported guest OS and it's only experimental for hosting?

---

### Post by codeseer on 2009-04-28
Could be. My VirtualBox install seems to work fine, both 32-bit and 64-bit.

---

### Post by aeronutt on 2009-05-03
> **codeseer said:**
> Great to hear!

For those who may encounter this post and experience missing dependencies, they can be acquired by typing the following in the terminal:

```

sudo apt-get install libcurl3

```

(Replace 'libcurl3' with the name of any other dependency you may be missing).

I'm getting "Error: Dependency is not satisfiable: libcurl3" when trying to install "install_flash_player_10_linux.deb".

sudo apt-get install libcurl3 returns "E: Couldn't find package libcurl3"

Any ideas what to try next?

EDIT: I added 'medibuntu' and all is well.

---

### Post by ehababoud on 2009-05-17
having a similar issue. sorry if i'm not allowed to post here, i can't fullscreen any videos because when i do it starts to delay the picture and jitters. never happened in any other linux distributions or my windows one so i don't think its my driver. what you guys think?
is there a possible alternative to the flash i downloaded?

thanks in advanced

ehab

---

### Post by Milv8 on 2009-05-18
Hi all

I have had problems since installing Jaunty, Flash seem to be the problem,also you tube.

installed adobe non free as mention in earlier post. then i removed from synaptic swf-mozilla and all is well.

hope this helps others

Love linux hate windows

regards
Bo

---

### Post by johnswb on 2009-05-20
And what does a person do if they do not have multiverse in the repo?

---

### Post by thtrgremlin on 2009-05-20
synaptic->settings->repositories->Software restricted by copyright or legal issues (multiverse)

---

### Post by sam1948 on 2009-06-02
> **codeseer said:**
> Download it from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract it using: tar zxvf libflashplayer-*.tar.gz
.............




thanks codeseer

only I selected only one of the steps. I did this:
```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

- restart firefox 
- try to open a flash video and fail
- then firefox gives u the link to download 
- select the .deb and install it 

Regards

---

### Post by pmenefee on 2009-06-03
With 9.04........

I opened Firefox and tried to run Pandora, which requires flash.  Firefox asked if I wanted to install the missing program necessary to run Pandora.  I said yes and picked the Adobe Flash installer from the list.  Ran it from Firefox and then restarted Firefox when it finished.  Pandora now runs, so I guess Adobe Flash is installed.

Pete
(surely it can't be that easy.........but it was)

---

### Post by newagelink on 2009-06-03
> **pmenefee said:**
> With 9.04........

I opened Firefox and tried to run Pandora, which requires flash.  Firefox asked if I wanted to install the missing program necessary to run Pandora.  I said yes and picked the Adobe Flash installer from the list.  Ran it from Firefox and then restarted Firefox when it finished.  Pandora now runs, so I guess Adobe Flash is installed.

Pete
(surely it can't be that easy.........but it was)Hm, see, I'm also trying to use pandora, but the flash appears to freeze; see attached pandora.png: it will get to that point then sit there indefinitely, even with "Done" printed in the Status bar.

---

### Post by pmenefee on 2009-06-03
I wish I could help, but I'd have been out of luck if it hadn't gone smoothly.  Seems like once before Firefox wanted a couple of addons, but worked fine after Flash and one other were installed.  I got a Firefox addon needed message though.  Just took a couple of tries.

This time it slicked right on through.

---

### Post by domex on 2009-06-13
> **codeseer said:**
> Clean up past installation of Flash:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```Download and install new .deb Flash from here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Thank you kind sir this worked perfectly!:p:KS:KS:KS:KS

---

### Post by running_rabbit07 on 2009-06-13
> **nandemonai said:**
> ```
lspci | grep VGA
```Intel could be part of the problem. I've been seeing numerous issue with it in Jaunty.

Funny thing. I had the opposite problem with Debian Lenny 5.0.1. Could not get NVIDIA drivers to load. Nor could I get a response to a forum post from the debian forum where I was begging for help. Ditched the Debian and here I am Happily using Ubuntu and everything is working great.

 Thanks go out to all the "geeks" here helping people have a happy PC!

---

### Post by Hutto on 2009-06-24
This always works for me...AMD64

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz

---

### Post by Titofish on 2009-06-29
ok people what is happening whit the choppy video in full screen is a problem whit the computer that has a intel graphic card.  

The way I RESOLVE that problem was doing this;
1. **Aplication >Terminal** 
2. You need to create the directory and file manually, e.g.:


 $ sudo mkdir /etc/adobe
$ echo "OverrideGPUValidation=true" >~/mms.cfg
$ sudo mv ~/mms.cfg /etc/adobe/


Note: This fix it for _**youtube only**_.  Is the easy way to fixed, it work for me.


I find this in other site and paste here. I have a gateway model UC7087U Laptop and an Aser Aspire One D250 notebook runing ubuntu remix and it works very nice. 



This is only for computers whit **_intel grahic cards_** ok. Thanks I hope it work for you guys.):P  Helping you from Puero Rico.

---

### Post by De4dSpace on 2009-07-01
I downloaded the flash installer via Synaptic Package Manager (multiverse) and noticed how it only crashes when your not MOVING your mouse around in the Firefox browser, wtf?

[COLOR=Red]Forgot to mention "using 64bit 9.04"[/COLOR]

---

### Post by colau on 2009-07-01
> **De4dSpace said:**
> I downloaded the flash installer via Synaptic Package Manager (multiverse) and noticed how it only crashes when your not MOVING your mouse around in the Firefox browser, wtf?
Strange.
[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

---

### Post by Denton Larson on 2009-07-17
> **codeseer said:**
> Clean up past installation of Flash:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```

Download and install new .deb Flash from here: [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

I did this and it WORKS!!!!!!
Thank you
Denton

---

### Post by bmp52 on 2009-07-18
When trying to install Flash player using the:  .deb for Ubuntu 8.04+  version and then install it using:    GDebi Package Installer (default)   it begins to install but then I get the following message:  Error: Dependency is not satisfiable: libcurl3     

Any ideas?

---

### Post by sam1948 on 2009-07-18
> **bmp52 said:**
> When trying to install Flash player using the:  .deb for Ubuntu 8.04+  version and then install it using:    GDebi Package Installer (default)   it begins to install but then I get the following message:  Error: Dependency is not satisfiable: libcurl3     

Any ideas?

instead try opening a command line and type this:
```
sudo aptitude install flashplugin-nonfree
```
afterwards:
if it worked - fine.
otherwise - copy paste the output

---

### Post by bmp52 on 2009-07-18
I updated Firefox and then tried it again. This time I was prompted to install the libcurl3 package which I did and then Flash installed after that. Not really sure what libcurl3 does but seems to work fine now. Thanks for your help.

---

### Post by chazzyb on 2009-07-24
On a side note, I have spent all day working out why Flash 10 would not run on Jaunty 9.04. I un-installed all superfluous versions (swfdec etc etc).

Still no joy turns out the fix was the nvidia driver (180) is buggy with flash downgrade to version 170 and flash will work sweet as a nut if you have cleaned up your installation and used adobe-flashplugin through apt-get.

Regards

ChazzyB

---

### Post by OceanWinds on 2009-07-25
excellent stuff dude...

flash is working great now :)

---

### Post by hoogland on 2009-07-25
I am having weird behavior for flash playback. I removed all packages and references to flash prior to downloading the 64-bit adobe flash plugin version 10 alpha and copying it to my ~/mozilla/plugins/ directory. It worked for a while, then all of a sudden I can not see progression of video. Audio plays fine, but the screen shows black. When I move the slider of the Youtube player, I can get a frozen image of the video. Sometimes there is fast forward playback. I have looked into changing PulseAudio to Alsa, but this does not mitigate the problem. I must add that I had some of this behavior also in using the totem-plugin and playing back mms streams, so it may not be related to the flash plugin.

In any case, any help in solving this issue is greatly appreciated.

Runing Jaunty 64-bit w/ flash 10.0 r22

UPDATE: REMOVING PULSEAUDIO RESOLVED MY PROBLEMS WITH SLOW VIDEO PLAYBACK. DISABLING BY ITSELF UNDER PREFERENCES > SOUND WAS NOT SUFFICIENT.

---

### Post by supmantua on 2009-07-25
> **codeseer said:**
> Download it from here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract it using: tar zxvf libflashplayer-*.tar.gz

Clean up past installation of Flash:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
```Install the new Flash:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins
```

i ran this and got this error (towards the bottom)
[quote=mantua@mantua-laptop:~]
The following packages were automatically installed and are no longer required:
  gstreamer0.10-plugins-ugly linux-headers-2.6.28-11 gstreamer0.10-ffmpeg
  linux-headers-2.6.28-11-generic libswfdec-0.8-0 libsidplay1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 114 not upgraded.
mantua@mantua-laptop:~$ sudo rm -f /usr/lib/mozilla/plugins/*flash*
mantua@mantua-laptop:~$ sudo rm -f ~/.mozilla/plugins/*flash*
mantua@mantua-laptop:~$ sudo rm -f /usr/lib/firefox/plugins/*flash*
mantua@mantua-laptop:~$ sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
mantua@mantua-laptop:~$ sudo rm -rfd /usr/lib/nspluginwrapper
mantua@mantua-laptop:~$ sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
**cp: cannot stat `libflashplayer.so': No such file or directory**
[/quote]

i'm also having an issue with choppy video.
using the latest update, my video is 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

any help would be greatly appreciated

---

### Post by nandemonai on 2009-08-31
> **supmantua said:**
> i ran this and got this error (towards the bottom)


i'm also having an issue with choppy video.
using the latest update, my video is 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

any help would be greatly appreciated

I've had success on my new netbook (Toshiba NB200) with a Intel Mobile 945GME Express by adding this PPA and then upgrading:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Proceed at your own risk though, I'm not 100% these drivers would be best for your chipset but they certainly fixed the choppy video / flash I was experiencing.

EDIT: Btw, with the above clean up and installation of the newer Adobe Flash player, are you sure you downloaded and extracted the .tar.gz from the first two steps?

---

### Post by warshifter on 2009-09-01
Thanks this help alot :D

---

### Post by atentik on 2009-10-02
Go to [adobe]("http://get.adobe.com/flashplayer/") site and select "**Different operating system or browser?**". Select Linux from the drop down menu and continue. At the very bottom of the list is Flash player 10 for Linux (.deb). Select that one and you should be able to install it.

---

### Post by bgreenaway on 2009-10-13
As far as I am concerned, this is a show-stopper for me and I will not go to 9.10 until it is fixed. I use 8.10 on my System76 Pangolin laptop and 9.04 on my HP Compaq dc5800 at work. The choppy video problem begins with 9.04 as it is not an issue with 8.10, so I have no intention of upgrading my laptop yet. 

I have tried virtually every suggested fix that I have found on the forums with no success .

---

