---
title: "Unity full screen issues"
date: 2012-03-27
forum: Desktop Environments
---

### Post by artshark on 2012-03-27
Hey guys. I somehow broke unity-it isn't playing well. The dock is fixed but the apps act as if autohide is enable, masking the leftmost edge. The screenshot below should demonstrate this. I have CCSM installed and I think the hand off between the two may be the issue. Thanks!
[IMG]http://i47.photobucket.com/albums/f151/artshark/Screenshotfrom2012-03-27233938.png[/IMG]

---

### Post by Krytarik on 2012-03-28
> **artshark said:**
> The dock is fixed but the apps act as if autohide is enable, masking the leftmost edge. ... I have CCSM installed and I think the hand off between the two may be the issue.
Well, judging from the fact that your Launcher items aren't 'folding' when they extend the allocated space, currently you aren't running the regular Unity, but Unity 2D, whether or not that is intended; thus any settings in CCSM don't apply! You can check what session you are actually running with:
```
echo $DESKTOP_SESSION
```Extending further down the Unity 2D road, judging from the look of the Launcher items, you are using Oneiric 11.10, and in that, if you want the Launcher to always show, additionally to setting the "hide-mode", you need to enable the key "use-strut"; and it seems like the latter is not enabled in your case, to enable it, run:
```
gsettings set com.canonical.Unity2d.Launcher use-strut true
```Alternatively, you can, of course, set "hide-mode" to either auto-hide, "1"; or dodge windows, "2":
```
gsettings set com.canonical.Unity2d.Launcher hide-mode 2
```You can use this GUI tool to toggle those settings more conveniently, plus others:

[LIST]
[*][http://www.tuxgarage.com/2011/10/gui-for-changing-unity-2d-settings.html](http://www.tuxgarage.com/2011/10/gui-for-changing-unity-2d-settings.html)
[/LIST]

As for getting the regular Unity to run, however, you can check with the below command if it's currently supported, and also check "Additional Drivers" for any possible better fitting video drivers.
```
/usr/lib/nux/unity_support_test -p
```For anything more than this, the output of that check and any additional info reg. your current graphics setup is needed.

Regards.

---

### Post by artshark on 2012-03-28
> **Krytarik said:**
> Well, judging from the fact that your Launcher items aren't 'folding' when they extend the allocated space, currently you aren't running the regular Unity, but Unity 2D, whether or not that is intended; thus any settings in CCSM don't apply! You can check what session you are actually running with:
```
echo $DESKTOP_SESSION
```Extending further down the Unity 2D road, judging from the look of the Launcher items, you are using Oneiric 11.10, and in that, if you want the Launcher to always show, additionally to setting the "hide-mode", you need to enable the key "use-strut"; and it seems like the latter is not enabled in your case, to enable it, run:
```
gsettings set com.canonical.Unity2d.Launcher use-strut true
```Alternatively, you can, of course, set "hide-mode" to either auto-hide, "1"; or dodge windows, "2":
```
gsettings set com.canonical.Unity2d.Launcher hide-mode 2
```You can use this GUI tool to toggle those settings more conveniently, plus others:

[LIST]
[*][http://www.tuxgarage.com/2011/10/gui-for-changing-unity-2d-settings.html](http://www.tuxgarage.com/2011/10/gui-for-changing-unity-2d-settings.html)
[/LIST]

As for getting the regular Unity to run, however, you can check with the below command if it's currently supported, and also check "Additional Drivers" for any possible better fitting video drivers.
```
/usr/lib/nux/unity_support_test -p
```For anything more than this, the output of that check and any additional info reg. your current graphics setup is needed.

Regards.
I resolved this issue but another ended up being created. I'll install that GUI and see if it helps
Thanks!!

---

