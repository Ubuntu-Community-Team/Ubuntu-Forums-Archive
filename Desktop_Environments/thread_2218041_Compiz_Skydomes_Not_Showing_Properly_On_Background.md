---
title: "Compiz Skydomes Not Showing Properly On Background"
date: 2014-04-19
forum: Desktop Environments
---

### Post by milliman on 2014-04-19
Another new release, more Compiz plugin issues.  I have learned to live with the fact that 3D windows don't work any more but I like to use Desktop Cube.  After upgrading to 14.04, my Skydomes do not display properly on the background.  If I deactivate the feature, the black background shows properly, I'd just like to display a nice graphic behind my rotating cube.  I was wondering if anyone else is having this same issue.

I have an integrated Intel i915 graphics controller with OpenGL version 1.4.  It worked before the upgrade so I don't imagine that anything graphics driver is causing the problems.  Has anyone else using Unity encountered and solved this problem?

Thanks,
Mark

---

### Post by george45 on 2014-04-20
Hi, Today i installed 14.04 I had many years to use ubuntu,but i remember last time i was using them i had no issues with my skydome.Now i have exactly the same problem as you..I am using an old Nvidia 7900GT with Nvidia legacy binary driver version 304.117....

---

### Post by fattyz on 2014-04-26
Same problem.  I see something but not the skydome image the way it should display.  I really miss the 3D windows as well.  :  (  I also have an issue with screen dimming when I turn up the cube Transparency.  I have had the suspicion that the fact that desktop effects settings no longer can be adjusted under appearence has to do with some of these problems?

Thx

---

### Post by theller on 2014-04-30
I installed 14.04 on an Acer Aspire. I installed the prorietary video drivers. Then I tried open source drivers No Change. The background is black if I turn off skydome. If I use Cube Reflection and Deformation The cube will rotate smoothly and the reflection works but still I cannot set the Skydome picture (background of the cube). The background is the original desktop screenshot. When I ctrl Alt mouse The screen shrinks in 3 or for series of desktop snapshots. I did shut off fading windows.

Any ideas?

Need more info?

---

### Post by Alan Bradley on 2014-05-05
The same thing is happening to me also. I upgraded to 14.04 and the skydome does not work

---

### Post by theller on 2014-05-05
Is this enough people to report a bug?

---

### Post by grumblebum2 on 2014-05-05
I don't think anyone is working on the unsupported plugins in the **compiz-plugins** package and
this is just the way it will be as compiz develops for unity.

---

### Post by theller on 2014-05-06
I remember reading a quote from Linus Torvalds "Do it yourself." Any ideas where I could start? Is this a problem with Compiz or Unity? My thought is it's a Unity issue. Anyone have ideas for troubleshooting?

---

### Post by grumblebum2 on 2014-05-06
I think you would have to rewrite the plugin.
The plugins in the compiz-plugins package are not officially supported so unless you or some one else has 
the know how and inclination to fix, when they break they'll most likely remain broken.

---

### Post by fattyz on 2014-05-18
I'm willing to go back a few versions if it means getting this to work and the extra animations that are also now missing.  Anyone else?  I don't see any compelling reason to stay at 14.04.  Compiz + Emerald are a large % of running Ubuntu at all, at least for me.   I am running flashback anyway and could be at 10.04 if everything else worked the same, and I'm fairly sure it would.  (I still have IOS 6.1 on my iphone and I'd still have the 3gs if I had known enough not to upgrade :  ))  If someone went to the trouble to make Emerald work I don't see why not this as well.

Just my thoughts, thanks all.

Yours

---

### Post by egeezer on 2014-05-18
I'm another for whom Compiz is a prime reason for using any Linux distro.  Right now I have two installations of 14.04: one is pure Xubuntu, the other installed as Ubuntu+xubuntu-desktop.  Both run the Cube/Sphere/Cylinder just fine (as long as I don't use raised windows) and the Skydome also is fine.  I think the problems arise because although Unity requires Compiz, it uses it differently than the stuff we like.  With Xfce/Xubuntu, the Unity part is shut off.  BTW, I don't install Emerald - could that be part of the problem?

---

### Post by roxfoxpox on 2014-06-21
;) Please voice your issue with the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1330080](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1330080)
I've got the same problem as described, 
and I think we'll need a larger list of people affected before this gains more attention.

---

### Post by grumblebum2 on 2014-06-21
> **roxfoxpox said:**
> ;) Please voice your issue with the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1330080](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1330080)
I've got the same problem as described, 
and I think we'll need a larger list of people affected before this gains more attention.

Are you aware that plugins you install from the compiz-plugins package
are not officially supported?

---

### Post by QIII on 2014-06-21
These are not bugs and they are not caused by Unity.

They are features that have been turned off because the Compiz developers simply are too few and have too little time to continue to develop the features along with changes in newer distributions.

Again:  Don't blame the wrong people.  If you want those features back, volunteer to maintain them.  The Compiz developers (I think there are two left) were begging for help three or four years ago.  Too late now, probably.

---

### Post by theller on 2014-07-11
I just started going through some compiz files and I found in /usr/share/doc/compiz-plugins/authors.gz a file with 129 authors. are these the authors of the plugins?

Should I email them directly to ask for help or is that rude?

Has anyone gotten cubegears to work?

---

### Post by fattyz on 2014-08-07
I uninstalled tweak tool and it looks much better.  I still think the lack of the effects settings is a key in this because you used to be able to turn the effect settings to high to make all this work.  If you have tweak tool installed remove it and let me know if things display better.  I am still fooling around with it.

Thanks,  Yours

---

### Post by fattyz on 2014-08-09
Ok so they work and look better but I don't think 3d rendering is working properly (or whatever).  They show and look ok but not !!! wow  !!! which is how they used to look.  I am sure it is a tweak in the settings somewhere but getting rid of tweak tool made them look at least 50% better.

---

### Post by d.vanheeckeren on 2014-08-26
Just as a side note, I don't think it's only Unity.  I'm having the same problem with Gnome, and it's always worked beautifully before.

Maybe it's related to upgrading instead of fresh install?  Sometime in the coming month I'm going to be reinstalling 14.04 LTS from scratch and trying, and I'll definitely post the results when I do get to do it.  Just not sure exactly when that will be since time is in such short supply for me.

And on a personal note, with all the standards and conventions out there, you'd think that all desktop managers would be written to use the plugins in the same way...or at least if one is going to do something custom with it, then start another branch or "flavor" of the plugins that they build from.  Just a thought.  :o)

---

### Post by peddanet on 2014-09-24
> **fattyz said:**
> Ok so they work and look better but I don't think 3d rendering is working properly (or whatever).  They show and look ok but not !!! wow  !!! which is how they used to look.  I am sure it is a tweak in the settings somewhere but getting rid of tweak tool made them look at least 50% better.

For me that worked:
dconf reset -f /org/compiz/

which resets compiz settings (maybe they were messed up during distro update vom 12.04). So it is probably not a bug...

@fattyz: how did you get the cube more far away in the screen, mine is so damn big! And how did you set that background behind the cube, I have never seen that before ? :-)

---

