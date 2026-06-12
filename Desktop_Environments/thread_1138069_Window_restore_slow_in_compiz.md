---
title: "Window restore slow in compiz"
date: 2009-04-26
forum: Desktop Environments
---

### Post by dgel on 2009-04-26
Hi,

since upgrading to jaunty, restoring windows under compiz has been very slow. I can click the taskbar entry, then it does nothing for a while after which it restores the window at normal speed, including compiz animations.
I have no such problems under metacity. I already upgraded the ati driver to 9.04 (fglrx), but that didn't help.
btw, I'm using an ati HD4830.

any suggestions?

---

### Post by Parp on 2009-04-26
I have the same problem, I'm using ATI HD3450...  (on a Dell Studio 540, Quad Core 2.3Ghz, 4GB RAM)

---

### Post by koudelka on 2009-04-26
Same issue for me... resize windows is very slow too !!!
I have try the last ATI Catalyst&#8482; Display Driver 9.4, but no change... :(

- Thinkpad T500 - ATI Radeon Mobility HD3650
- Ubuntu 9.04 - 64 bits

---

### Post by madias on 2009-04-26
confirmed: ...same to me: laptop with ati HD2600, i searched several forums with no functionally answer for me, I think we have to wait for an update (ati-driver or compiz)

---

### Post by bjtuna on 2009-04-28
Same problem here, and in fact I've seen this in each of the last few Ubuntu releases. In each case I've ended up just disabling compiz, assuming (incorrectly, perhaps) that my computers are just too slow.

---

### Post by mgmuscari on 2009-04-28
I have been experiencing this same problem. Compiz worked perfectly for me under 8.10 with FGLRX driver.

My specs are as follows:

Lenovo w500 ThinkPad
Intel T9600 @ 2.63GHz
4GB RAM
ATI FireGL v5700 Mobility (reports in FGLRX as Radeon hd3650)

Those are the essentials. Is there any word on what application this is related to (Compiz, Jaunty itself, or FGLRX)? Where can I go to help investigate and contribute?

---

### Post by lethalfang on 2009-04-28
Same here. I notice this problem whenever I try to maximize a window. It's slightly annoying, although I can tolerate it. 

Gateway M-6862 (Intel Core 2 Duo 2.0 GHz)
ATI Mobility Radeon HD 2600

---

### Post by lesodk on 2009-04-30
Same here raden 3650. Does anyone have a solution?

---

### Post by shrndegruv on 2009-04-30
I think ati users are screwed until AMD fixes the fglrx driver.

I am pissed.  How can 9.04 go thru as many betas as it did, and noone warn ATI users that the driver just isn't ready yet. I think Canonical should be embarrassed.  Not that the driver doesn't work, because that is AMD's fault, but because there was no warning.

Going back to windows....

---

### Post by Rippy on 2009-04-30
Yeah, if it is a driver problem then it's not really their fault, but it's still kind of embarrassing to have an issue like this in an otherwise excellent release.

I'm having the same issue, fully updated fresh 9.04 install, with a radeon HD3650, and while most compiz things work just fine, window resizing and maximizing/minimizing is very slow. Works fine in metacity.

Does this affect anything other than compiz, like 3d games? And can we expect a fix sometime soon, or is it likely going to be a long wait?

---

### Post by butterdori on 2009-05-03
It doesn't seem to be fglrx alone

I have an x1300 (with open source drivers of course, since fglrx now dropped support for graphic cards before hd2xxx series) and i also have delays in minimising, alt+tabbing, and showing all windows (shift+alt+up)

On the other hand, Warcraft 3 seems to work fine with open source drivers... go figure

---

### Post by bjtuna on 2009-05-04
I actually have this problem on both my laptop and desktop; the laptop has an Intel 945 video card while the desktop has a newer ATI R3600.  My instinct is that this has more to do with my the CPU speed of these boxen than with the video chipsets or xorg drivers.  My laptop is just an old Centrino 1.4ghz, and the desktop is an old Athlon64. Both are showing their age.

---

### Post by madias on 2009-05-04
Sorry, but you are not right. I´ve a Laptop with 2.2GHZ turion (HD2600) with the same issue - this cpu´s are powerful enough, it´s ati´s fault.
Bug thread:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351186)

---

### Post by s3lekta on 2009-05-04
> **madias said:**
> Sorry, but you are not right. I´ve a Laptop with 2.2GHZ turion (HD2600) with the same issue - this cpu´s are powerful enough, it´s ati´s fault.
Bug thread:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351186)

3400 hd here, same problem

thanks for the bug link

---

### Post by stevenmansour on 2009-05-25
Has anyone seen any progress on this?

I just installed the latest drivers from the ATI website (9.5, May 18th) and the problem still exists.

I've grown dependent on all of Compiz' window management tools for my workflow, but now it's unusable so I've had to revert to metacity. :(

Lenovo T500 /w ATI 3650

---

### Post by svaens on 2009-06-25
Hi all, 

yep, same here. 

I am on latest jaunty fully updated as of 25/6/2009

I have ATI Mobility Radeon  HD 3470 graphics. 
And it is not a CPU speed issue. Mine is fast enough. 

My exact symptoms:

minimize action works fine. 
maximize action causes first a long paus (1 second)
then the window maximizes. However, I don't really see any of the usual animation of the window maximizing. It kind of just appears after the delay. 

Usage of compiz in this current state is not really worth it. 
The maximize action of using metacity is much better. 

And while i'd rather have the smoother graphics of compiz, (and i'd REALLY like to have back the semi-transparent ubuntu messaging, which is instead fully opaque in metacity with this ATI card), 
I have reverted to metacity (no effects) due to this bug.

---

### Post by shrndegruv on 2009-06-25
svaens

you have the catalyst 9.6 driver right?

Regardless of that, from these forums and  IRC I think the issue is caused by the xserver, not the driver.  If you search these forums for jaunty xserver patch I think you will find a way around the issue.

---

### Post by japher on 2009-07-12
This can be fixed by updating to a patched version of XServer and restarting. See sparrowkc's post here:

[http://ubuntuforums.org/showpost.php?p=7553081&postcount=9](http://ubuntuforums.org/showpost.php?p=7553081&postcount=9)

---

### Post by shrndegruv on 2009-07-13
> **japher said:**
> This can be fixed by updating to a patched version of XServer and restarting. See sparrowkc's post here:

[http://ubuntuforums.org/showpost.php?p=7553081&postcount=9](http://ubuntuforums.org/showpost.php?p=7553081&postcount=9)

I am curious as to the implications of doing this.  If you use a patched xserver, what happens when new xserver binaries are pushed out in the default repos?

---

### Post by Tom Tiger on 2009-09-04
Problem still exists,  I'm using a Quad Core 2.33, Ati Radeon 4850HD 4gb of ram, system is slow using compiz and blacks out movies with both mplayer and xine, also full screen movies are very sluggish and sometimes the system crashes when switching to full screen. 

I turned off compiz and all the problems were gone, the system was very very fast again.

Any Nvidia users with the same problem?  Or is this limited to Ati and Compiz?

---

### Post by screaminj3sus on 2009-09-04
Same thing happens to me with my hd2600 when I last used ubuntu with the 9.6 driver I think.

So they STILL haven't fixed this even by 9.8?

This is retarded, someones gotta fix something.

---

### Post by shrndegruv on 2009-09-04
you guys both use the x server with no backfill PPA?

---

### Post by screaminj3sus on 2009-09-08
> **shrndegruv said:**
> you guys both use the x server with no backfill PPA?

I have no idea what that is?

Link to ppa and what it does would be nice :) This problem is simply ridiculous and happens to pretty much everyone using ati cards and compiz, absolutely unacceptable.

edit: think i saw a link earlier in the thread I missed

---

### Post by screaminj3sus on 2009-09-13
Anyone know if the new cat 9.9 fixes this? (probably not I assume)

---

### Post by shrndegruv on 2009-09-13
the ppa is listed within 10 posts above this one.  It installs a patched xserver that fixes the issue, at least for me and probably for most or all of the people who try it.

---

### Post by screaminj3sus on 2009-09-17
Thanks that PPA fixed it. Still can't use vsync so compiz tears though *mutters angrily shaking fist at ati drivers*

---

### Post by yeehawjared on 2009-09-18
PPA fixed it for me as well.

---

### Post by cybdrw on 2009-09-30
Ubuntu 9.10 Karmic developement 32bit
Tried with atidrivers from repo and downloaded from site (9.9)
Lenovo T500

After I switch off compiz everything fine .. 

Hope an update of X or Ati will solve this issue.

---

### Post by iBurger on 2009-12-29
1. Add ppa
2. Update.

This works, however, it could be that the xserver with no backfill package ppa is outdated by a newer version in the main repositories. Then you can select the "right" version by searching for the package: **xserver-xorg-core** in sypnaptic and hit CTRL+E to select version.

Thanks to sv1cdn, who pointed this out in this [post]("http://ubuntuforums.org/showthread.php?p=8637667").

---

### Post by zhengying on 2010-02-25
Thanks for the post. I have same problem with HP elitebook 8530w ( Mobility Radeon HD 3650)


It's fixed by using backfill version

---

### Post by WDYSUN on 2010-03-04
Hi Guys

this bug affected me as well both on DELL Latitude D520 laptop (intel graphic chip) with Ubuntu 8.10 LTS, and my new Dell Inspiron Desktop with ATI4350. I tried both free and non free drivers, this didn't change the results.

Anyway even if I don't have compiz installed I had another   minimizing-window issue: in fact, setting  on non-graphic-effects and  minimizing a window produces  a shrinking sequence of black rectangles that follow the minimizing-window down to the lower bar. This is very annoying and I don't know whether this problem has the same root. 

Anyway, I could solve the problem doing:

```

gconftool-2 --type bool --set /desktop/gnome/interface/enable_animations 'false'

```

It's very annoying that such a system is limited in graphic.

Best Wishes
Pietro

---

### Post by hojjat on 2011-04-18
I'm having this same problem ATI Radeon HD 2400 Pro on Ubuntu 10.04, and I tried to install the PPA, but apparently it only supports 9.04 and 9.10. Can you please provide instructions for installing it on 10.04?

---

