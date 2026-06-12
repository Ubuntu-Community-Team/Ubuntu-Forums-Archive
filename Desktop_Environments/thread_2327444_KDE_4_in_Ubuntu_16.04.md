---
title: "KDE 4 in Ubuntu 16.04?"
date: 2016-06-10
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2016-06-10
I currently use Lubuntu 14.04 with a number of KDE 4 applications.  In playing around with various flavors of Ubuntu 16.04 in VM, and trying to set it up sort of like I've got Lubuntu 14.04, I keep getting stuck on KDE 5.  First tried adding KDE 5 apps in Lubuntu 16.04, but systemsettings was totally blank and Qt 5 styling wasn't working.  So then tried Kubuntu 16.04 to see if that would solve those problems, and it did, but not only was plasma desktop crashing repeatedly, but I discovered that the ability to use custom formats for date/time was removed.   Those are show-stoppers for me :(

Is it possible to just go with what I already know here and install KDE 4 in Ubuntu 16.04, if so how?  (Or is there an equivalent of the Trinity desktop environment project but for KDE 4?)

Thanks

---

### Post by T.J. on 2016-06-11
16.04 does not support KDE 4.  The installed libraries are geared for Plasma 5.  In order to get KDE 4 to work, you would have to compile it or have someone backport it for you.  As a personal observation, I have found KDE 4 and Plasma 5 to be buggy, unless you are using a proprietary driver.  I've pretty much given up on KDE since they switched to version 4.  They never seemed to get the bugs out and when they got close, they started it all over again by switching Plasma 5.


I threw up my hands and switched to XFCE, which is a lot more stable.  I simply install and use the KDE apps under XFCE  without using KDE itself.  You can force KDE apps to appear in the same style as XFCE apps by setting GTK+ in qtconfig.

---

### Post by QIII on 2016-06-11
KDE/Plasma 5 does not work well in some VM environments.

I am currently running Kubuntu 16.04 on metal using the open source AMDGPU driver.  It works without any "bugginess" of any sort.

---

### Post by T.J. on 2016-06-11
> **QIII said:**
> KDE/Plasma 5 does not work well in some VM environments.

I am currently running Kubuntu 16.04 on metal using the open source AMDGPU driver.  It works without any "bugginess" of any sort.


Awesome!  Too bad that 4/5ths of existing AMD cards can't use the AMDGPU driver.  The only ones that are guaranteed to work are the R9 series.  There are a number of R7s that are not supported at present.  In my opinion, the AMDGPU/FGLRX situation  along with the lack of support for commercial uses is the worst mess that AMD has created in recent memory, reminiscent of their once terrible drivers. The bugs in the existing FGLRX driver and its abandonment were so annoying that I went Nvidia for the first time in years.  Their drivers have twice the support span of AMD's.

---

### Post by &amp;KyT$0P# on 2016-06-11
Thanks T.J. and QIII for the replies!

> **QIII said:**
> KDE/Plasma 5 does not work well in some VM environments.
Ugh :-& This is an even bigger show-stopper since the way I use software absolutely depends on being able to test it out in VM...

> **T.J. said:**
> In order to get KDE 4 to work, you would have to compile it or have someone backport it for you.  
That's what I was afraid of :( No one has backported it as far as I can see, and I'm not well versed enough in this stuff to backport it myself, so if it doesn't work then I'm on for using something else.
I've looked around for the source but can't find it.  Where can I get the source for latest KDE 4 release, specifically I'm interested in 1) Konqueror file manager, 2) Konqueror embedded text editor, 3) Oxygen style, 4) Konsole terminal, 5) systemsettings?

Ark would be nice too but only because of how it integrates with Konqueror file manager.  If the standard GTK archive utility can be integrated like that with Konqueror, I don't need Ark.

> **T.J. said:**
> I threw up my hands and switched to XFCE, which is a lot more stable.  I simply install and use the KDE apps under XFCE  without using KDE itself.
This sort of thing is exactly what I'm hoping to do.

> **T.J. said:**
> You can force KDE apps to appear in the same style as XFCE apps by setting GTK+ in qtconfig.
I don't especially need same style, as long as it's eye candy enough it works for me ;)
(Currently I'm using Oxygen style for the most part.  But it's looking like I might have to find some other system theme to use in 16.04.)

---

### Post by T.J. on 2016-06-11
> **halogen2 said:**
> Thanks T.J. and QIII for the replies!

You're welcome!

> Ugh :-& This is an even bigger show-stopper since the way I use software absolutely depends on being able to test it out in VM...

It really depends on the VM you are using.  Plasma never has run well in things like VirtualBox, that have half-baked OpenGL support. (KVM is better.) Theoretically, you should be able to force KDE to use XRender, instead of OpenGL, as well as disable effects. That should solve most of your problems...theoretically.

> 
That's what I was afraid of :( No one has backported it as far as I can see, and I'm not well versed enough in this stuff to backport it myself, so if it doesn't work then I'm on for using something else.
I've looked around for the source but can't find it.  Where can I get the source for latest KDE 4 release, specifically I'm interested in 1) Konqueror file manager, 2) Konqueror embedded text editor, 3) Oxygen style, 4) Konsole terminal, 5) systemsettings?


Well, how to answer....First, Debian 8 still supports KDE 4 if that would be more your taste.  

I don't think you will need the source for KDE 4 specifically.  You can simply use XFCE and then install and use the KDE apps you want.  Plasma is just a desktop shell.  You can run Konqueror inside of XFCE if you really wanted to.  As it as a KDE app, you will probably have to install most of or the entire KDE environment (even if you don't use it), and then use KDE's control panel to set the default apps activated inside of Konqueror.   It's not that hard, but it is seldom ever perfect. I've integrated KDE apps into other desktops before.  

As for Oxygen, the icon theme is usable virtually anywhere. There are base Oxygen widget themes for GTK2 and GTK3 to make them look like Oxygen if you really want that.  I've found it much easier to just tell Qt (which is the basis of KDE) to use GTK's widget set.  It's a lot less hassle.

While I like KDE, I've come to realize that most KDE specific applications are poorly maintained.  Basket is buggy, and basically abandoned last time I checked.  Blogilo in 16.04 crashes on startup.   The list of annoyances goes on for a while.  Where possible, I've actually switched over to GTK or Qt based apps, which have a better track record.  The fact I seldom use KDE only apps allowed me to leave KDE behind.  

It is my opinion that like Gnome, KDE's mobile ambitions have led to a decline in the overall stability and quality of the software, which is ironic. KDE has made a few half-hearted attempts, but I have yet to see even a single Plasma Mobile device that I would actually buy.  Of the ones I have actually seen as available for purchase, they were vanity items in small production runs. Given the obvious instability of Plasma on the desktop using FOSS video drivers (which should be a stable reference platform), why would I ever want a phone or tablet based on it?

---

### Post by &amp;KyT$0P# on 2016-06-11
> Debian 8 still supports KDE 4 if that would be more your taste.
Given my past experience with installing Debian, I think I'd rather stick with Ubuntu...

Or, hmm, how to attempt to install the Debian .deb's of KDE 4 in Ubuntu 16.04?

> I don't think you will need the source for KDE 4 specifically.  You can simply use XFCE and then install and use the KDE apps you want.
This will likely fix the stability problem, but it won't fix the lack of needed customizability in KDE 5.   I would still need the source for KDE 4 specifically, just won't have to build every component of KDE 4.

Actually, while writing this post I did a test install of Xubuntu 16.04, and the default XFCE file manager in 16.04 is only two steps away from being able to replace Konqueror file managing for me:
1) When dragging&dropping an archive, it's missing an option to extract it at the drop point;
2) Date format has no option '3 Jun 2016 17:32:03' (but at least '2016-06-03 17:32:03' is pretty close)

Is there a way to get (1) in default XFCE file manager?

> There are base Oxygen widget themes for GTK2 and GTK3 to make them look like Oxygen if you really want that. 
Yes it's the widget theme I like.   Ubuntu 16.04 doesn't seem to have gtk3-engines-oxygen package though?
[http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=gtk3-engines-oxygen](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=gtk3-engines-oxygen)

> Where possible, I've actually switched over to GTK or Qt based apps, which have a better track record.  The fact I seldom use KDE only apps allowed me to leave KDE behind.
I'm open to suggestions for alternative (non-KDE) apps which have all the needed features & customizability..

---

### Post by SeijiSensei on 2016-06-11
I'd just stick with Kubuntu 14.04.  It will be supported through [2019]("https://wiki.ubuntu.com/Releases") after all.

---

### Post by QIII on 2016-06-11
T.J.:

I am quite well aware that AMDGPU only works with certain GPUs.  I am also aware that it does not work with all R9s or R7s.  I am aware that it is not the model number that matters, but the chipset.  I am also aware that the Volcanic Islands chipsets currently available and the new chipsets out later this month will work with AMDGPU.  AMDGPU did not work with my R9 290X (Hawaii), but it does with my R9 380X (Tonga).  Radeon did work fine with my R9 290X.  So no, the R9 series are not all guaranteed to work with AMDGPU.  I am also aware that AMD and the open source community (led by Canonical) have made huge improvements in the Radeon driver.  I am also aware that fglrx still works fine -- except that Canonical decided to move on to a new X Server when AMD was not prepared to update fglrx to be compatible.  I am aware that AMDGPU only works with GCN 1.2 compatible GPUs, that an experimental version is available for GCN 1.1 compatible GPUs and that by August it is hoped that it will work with GCN 1.0 compatible cards.  fglrx may make a reappearance in Ubuntu by then (it hasn't gone anywhere for distros that did not move to this version of X Server) if AMD updates it for the current X Server.  My suspicion is that they will -- dumping so many users who have recently bought other models will not do them much good when those users refuse to buy AMD products in the future.  

AMD, despite the ritualistic bad-mouthing it has gotten (a carry over from ATI before AMD bought it), is doing exactly what we have asked it to do for years:  They are working with the open source community to produce an actual working open source Linux driver that is feature rich and performs well.  That is where AMDGPU comes from.  It does not come from an abandonment of fglrx.  Interestingly, the proprietary AMDGPU-Pro driver is based on the open source AMDGPU driver.  That is quite a feat of standing the normal world of Linux video drivers on its head.

The situation right now with AMD is not that AMD is abandoning things.  The situation right now is that they are making things right, but that is causing some temporary turmoil.

---

### Post by QIII on 2016-06-11
> **SeijiSensei said:**
> I'd just stick with Kubuntu 14.04.  It will be supported through [2019]("https://wiki.ubuntu.com/Releases") after all.

Particularly if using it in a virtual machine.

---

### Post by &amp;KyT$0P# on 2016-06-11
> **SeijiSensei said:**
> I'd just stick with Kubuntu 14.04.
> **QIII said:**
> Particularly if using it in a virtual machine.
Thanks but this isn't a matter of ditching 14.04.  I rather not procrastinate solving this problem.

---

### Post by QIII on 2016-06-11
The "problem" is most likely related to the virtualization technology you are using, what is presented to the OS by the hardware abstraction layer and whether that virtual hardware is capable of handling KDE/Plasma.

What are you using for virtualization?

If it will not run Kubuntu 16.04 as is and you want to use an earlier version of KDE, you have a lot of work in store I am sure.  I guess the question SeijiSensei and I both may have is what compels you to use 16.04.  If you must use it, then perhaps we can find a way to make this work for you with virtualization.  If there is nothing compelling you to use 16.04 (particularly in a VM), then is the effort worth it to you?

---

### Post by &amp;KyT$0P# on 2016-06-11
I'm using VirtualBox for virtualization, and can't change virtualization technology.

> If it will not run Kubuntu 16.04 as is
Sorry, I guess I haven't been clear.  I'm looking only to run the individual KDE 4 apps listed above, probably under XFCE desktop / Xubuntu 16.04

> and you want to use an earlier version of KDE, you have a lot of work in store I am sure.
(I don't mind that so much.  From time to time I'll play around with random OSes just for fun :mrgreen:)

> I guess the question SeijiSensei and I both may have is what compels you to use 16.04.  If you must use it, then perhaps we can find a way to make this work for you with virtualization.
Several reasons I need to have the latest LTS around in a VM - for example,
1) need to help friends install it, and thus need significant familiarity with the OS and what all goes wrong etc.  Meaning I need to make a setup I'm comfortable with.
2) testing various applications where the devs seem to want things reproduced in latest LTS
3) with 14.04, installing newer versions of apps than in the package repository is becoming increasingly difficult with time.
4) VM is disposable environment that is really easy to restore to a working state, so I can test out a lot of potentially "risky" fixes etc before unleashing on a not-so-disposable environment.

---

### Post by QIII on 2016-06-11
OK.  I see the scope of what you are trying to do.

There is still the problem, however, that while a VM will allow you to test a lot, its limitations may cause results that are not going to appear in a bare metal installation.  This may be one of those cases.  When installing applications designed for KDE, some KDE dependencies will be drawn in.  If the VM is incapable of handling those due to the hardware presented by the hardware abstraction layer, you may not be able to run them or you may crash the OS.

Just FYI:  The kernel developers will not act on bug reports coming out of a virtual environment.  VBox "taints" the kernel with its modules and thus the developers discount the behavior.

For what it's worth, I use Kubuntu and I never run it in a VM -- particularly VirtualBox.  If your testing is drawing in components that cause the same sorts of problems I often encounter in Kubuntu when running it in VirtualBox, that may simply be a limitation of the testing platform for you.

We might, however, be able to move forward if you create a clean installation, start installing the packages you are interested in (keeping track of what you have installed) and come back to the forums with a specific package that has created a problem for you.  Handle each problem in its own thread until you work it through to a solution (or not) and then add the next package.  I think that is half a dozen experiments if I read your list correctly.

Would that work?

---

### Post by &amp;KyT$0P# on 2016-06-11
Thanks QIII for the help.

> We might, however, be able to move forward if you create a clean installation, start installing the packages you are interested in (keeping track of what you have installed) and come back to the forums with a specific package that has created a problem for you.  Handle each problem in its own thread until you work it through to a solution (or not) and then add the next package.

Would that work?        
You mean the standard KDE 5 packages right?

Sure, I'll try it.

---

### Post by QIII on 2016-06-11
Yeah, the KDE 5 apps.

Just be aware that it might not be immediately evident if any issues you encounter are due to the VM.

---

### Post by T.J. on 2016-06-11
> **QIII said:**
> T.J.:

I am quite well aware that AMDGPU only works with certain GPUs.  I am also aware....  I am also aware...also aware that fglrx still works fine -- except that Canonical decided to move on to a new X Server when AMD was not prepared to update fglrx to be compatible.  I am aware that AMDGPU. My suspicion is that they will -- dumping so many users who have recently bought other models will not do them much good when those users refuse to buy AMD products in the future.  

AMD, despite the ritualistic bad-mouthing it has gotten...


The situation right now with AMD is not that AMD is abandoning things.  The situation right now is that they are making things right, but that is causing some temporary turmoil.


Unless I am misreading you (and I apologize if I am), you need to "chill-ax" (chill out, relax).  =) I think there has been a misunderstanding somewhere.

 I do have a bit of venom reserved for AMD, but I wasn't bawling them or anyone else out, just stating facts. Although if you want my opinion, as a programmer, I find the situation inexcusable. Setting aside the fact that fglrx has longstanding issues that have never been fully corrected, like cursor corruption on multi-head and vsync issues, the absence of a fully functional OpenGL driver for existing generations of cards, is a serious PR and technical problem. 

If they decided to sack it because of long term concerns about DRI3 and Vulkan, that's fine - but still I believe it was really BAD timing. Xorg 1.18 has been out for 7 months, which was well ahead of the 16.04 release. Mesa is not quite up to OpenGL 4 yet (the core profile is still 3.3) -  so there really is no offering an excuse for not updating fglrx while they get the kinks out of AMDGPU.  It would have been the sane and positive thing to do.  At the moment, a lot of users do feel abandoned and annoyed.  I do not expect support forever, but I do expect AMD to gradually phase things out in a way that does not drive customers away.  There is a new generation of cards coming out, and people are going to remember this incident poorly - asking if AMD might do it again.  I certainly did, and I also remember how poorly ATI did when their name was on the cards (and not just for Linux).  It felt like history repeating itself, and at least a certain percentage are not going to wait around while AMD takes a year - perhaps two - to get AMDGPU at the level of use that fglrx has. 

I do give AMD a lot of credit for their efforts, seriously...I think the new driver is a great idea, and I love the GPUOpen project, but it can't possibly be a huge inconvenience to update fglrx while AMDGPU gets the development time that it clearly still needs.

Of course, you could say, stick with 14.04, and that is true - but given the way that the community works - that answer does nothing to enhance AMD's reputation.

---

### Post by QIII on 2016-06-11
Chill?  I'm not hot.

And the OP seems to be on a track that might help him/her deal with what they need.

---

### Post by T.J. on 2016-06-11
> **QIII said:**
> Chill?  I'm not hot.

And the OP seems to be on a track that might help him/her deal with what they need.

Great!  Glad to hear it.  I don't like to annoy anyone. =)  Have a wonderful evening and I hope we get another chance to chat.

---

### Post by &amp;KyT$0P# on 2016-06-12
In case anyone else finds this thread in a search, I'm going to post here what I DID get working plus links to any other related threads I make.

Starting from Xubuntu and using XFCE is so far looking like it'll be a much smoother ride than starting from Lubuntu.  I *think* I've got Konsole running OK... but the first few times I tried to run it, half the time it would crash instead of running. The error report said something about window sizing I think?  Not sure how to find previously-sent error reports to check exactly what it said.

At least I'm pretty sure what all I changed between when it didn't work and when it did:
 - Install and configure Openbox, and use it as my window manager under XFCE
 - When Konsole actually launched: Settings > Configure Konsole..., un-check "Use current window size on next startup"
 - In Konsole, under Settings > Edit Current Profile..., change the settings like this, click "Apply" before changing settings tab:

[LIST]
[*]Terminal Size: 80x39 (or 80x40) 
[*]Threshold for continuous silence: [nvm.  I've now confirmed that this setting is not relevant.]
[/LIST]
Somewhere in there, I made sure to quit Konsole by File > Close Window.
Also did: XFCE Settings > Session and Startup > Advanced, select "Launch KDE services on startup", but it was working before logging out & back in.

Any ideas what of that lot would have done the trick?

UPDATE: I performed all of the Konsole configuration under xfwm, and the spotty crashing persisted.  Added Openbox again, and the crashing isn't totally gone but it's MUCH less.
I think part of it might be related to the 3D acceleration setting in VirtualBox also - the crashing is worse with that enabled than with it disabled.  I've disabled 3D acceleration and switched to the guest additions from the Ubuntu repository, and so far things seems to be OK...

---

### Post by &amp;KyT$0P# on 2016-06-13
(just collecting links, will update this post if i make more threads...)

Konsole drag&drop fails if no write permissions on the shell's cwd: [http://ubuntuforums.org/showthread.php?t=2327689](http://ubuntuforums.org/showthread.php?t=2327689)
Disabling hardware acceleration for KNetWalk (and possibly all of KDE): [http://ubuntuforums.org/showthread.php?t=2329515](http://ubuntuforums.org/showthread.php?t=2329515)
Some Qt 5 apps seem to ignore qt5ct configuration: [https://ubuntuforums.org/showthread.php?t=2343084](https://ubuntuforums.org/showthread.php?t=2343084)

---

### Post by &amp;KyT$0P# on 2016-06-13
**Fixing the Qt 5 apps appearance** (aka getting Qt Oxygen theme under XFCE)
That's easy, using qt5ct from this PPA:
```
sudo add-apt-repository ppa:hda-me/qt5ct
sudo apt-get update && sudo apt-get install qt5ct
sudo apt-get --no-install-recommends install kde-style-oxygen-qt[45] oxygen-icon-theme
```

Now that we have qt5ct & Oxygen installed, using the instructions from [http://www.webupd8.org/2015/11/configure-qt5-application-style-icons.html]("http://www.webupd8.org/2015/11/configure-qt5-application-style-icons.html") to set up XFCE to make use of qt5ct configuration:
add this line to ~/.profile
```
export QT_QPA_PLATFORMTHEME="qt5ct"
```
then log out & back in.

The rest is just a matter of changing settings in qt5ct to set it up to personal tastes.
I personally thought the default font size was so large as to be an eyesore... also, KDE 5 Oxygen has a LOT more of padding around everything than KDE 4 Oxygen, but using size 8 font seems to reduce that enough for me.


(As for GTK apps appearance, I'm actually quite liking the default Xubuntu 16.04 GTK theme (Greybird) so will be leaving that as-is. :D )

---

### Post by &amp;KyT$0P# on 2016-06-14
I tried out the KDE5 Konqueror as well as Dolphin, and concluded that it's not a matter of those apps not working - they work fine, I just don't like it.  Fortunately it looks that Thunar will work nicely:

> **halogen2 said:**
> I did a test install of Xubuntu 16.04, and the default XFCE file manager in 16.04 is only two steps away from being able to replace Konqueror file managing for me:
1) When dragging&dropping an archive, it's missing an option to extract it at the drop point;
2) Date format has no option '3 Jun 2016 17:32:03' (but at least '2016-06-03 17:32:03' is pretty close)

Is there a way to get (1) in default XFCE file manager?
Answering my own question... yes there is, have to **right-**click drag&drop.  It wants to use file-roller, but there is however an issue with file-roller command line which makes this behave unexpectedly, but KDE 5 Ark can be used to work around it:
1) in /usr/lib/x86_64-linux-gnu/thunar-archive-plugin, rename 'file-roller.tap'
2) link ark.tap to file-roller.tap:
```
sudo ln -s ark.tap file-roller.tap
```
3) edit ark.tap so that it actually works with KDE 5 Ark:
```
#!/bin/sh
#
# file-roller.tap - Wrapper script to create and extract archive files
#                   in Thunar, via the thunar-archive-plugin, using the
#                   KDE ark archive manager.
#
# $Id$
#
# Copyright (c) 2006 Benedikt Meurer <benny@xfce.org>.
#
# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the Free
# Software Foundation; either version 2 of the License, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
# FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
# more details.
#
# You should have received a copy of the GNU General Public License along with
# this program; if not, write to the Free Software Foundation, Inc., 59 Temple
# Place, Suite 330, Boston, MA  02111-1307  USA.
#

# determine the action and the folder, $@ then contains only the files
action="$1"; shift;
folder="$1"; shift;

# check the action
case $action in
create)
	exec ark --autofilename tar.bz2 --add "$@"
	;;

extract-here)
	exec ark --destination "$folder" --batch --autosubfolder "$@"
	;;

extract-to)
	exec ark --destination "$folder" --batch --dialog "$@"
	;;

*)
	echo "Unsupported action '$action'" >&2
	exit 1
esac


```
(I don't claim that to be the "best" way to edit it, but it seems to work.)

---

### Post by &amp;KyT$0P# on 2016-07-01
**KUser**
I had forgotten about this one, because I don't need to administer users very often.  Works OOB except that when run with gksu or kdesudo, the appearance is an eyesore.  Running with sudo doesn't give this problem, but people say that's "not recommended" and I don't want to cause other problems when running stuff as root!

The fix is to copy in the qt configuration:
```
sudo cp -vR ~/.config/qt5ct /root/.config
```
Then edit /root/.profile same as [this]("http://ubuntuforums.org/showthread.php?t=2327444&p=13503720&viewfull=1#post13503720")

Now running with gksu should look nice same as user account's Qt 5 style :D

---

