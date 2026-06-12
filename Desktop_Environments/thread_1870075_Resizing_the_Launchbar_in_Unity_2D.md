---
title: "Resizing the Launchbar in Unity 2D"
date: 2011-10-26
forum: Desktop Environments
---

### Post by MoonLitOwl on 2011-10-26
I know that if you wanna resize the launchbar and even the icons in 3D, you need the program called ccsm.

But is it the same for 2D? I'd like to resize it as I have a small screen and it's rather clunky.

Thanks!

---

### Post by MoonLitOwl on 2011-10-27
Giving this a bump. I'd really like some help!

---

### Post by raja.genupula on 2011-10-27
First install dconf-tools 

Code:
sudo apt-get install dconf-tools

Then in the terminal (or you can use ALT+F2 to bring up the run dialogue box) type

 dconf-editor

When the dconf-editor appears, navigate to Desktop > Unity and fix the form factor to "Desktop", that way the dash will not take up the whole screen. If the form factor is fixed at netbook the dash will always open fullscreen, if it is automatic then the system would decide for you.

All the best

---

### Post by Frogs Hair on 2011-10-27
You can add a few more options with this ._[http://www.omgubuntu.co.uk/2011/10/unity-2d-tweak-app-updated-for-11-10/](http://www.omgubuntu.co.uk/2011/10/unity-2d-tweak-app-updated-for-11-10/)_[]("http://marianochavero.wordpress.com/2011/10/14/unity-2d-settings-ui-for-ubuntu-11-10-oneiric-ocelot/")

---

### Post by mc4man on 2011-10-27
There is currently no way to do that in unity-2d other than rebuilding.
Previously when rebuilding one could pick one new size, there is now a branch/commit that enables the user to adjust similar to unity-3d

See here for an example
[http://ubuntuforums.org/showthread.php?t=1870029](http://ubuntuforums.org/showthread.php?t=1870029)

If this doesn't make it into 11.10 at some point then you could build for yourself or no doubt there will be a ppa or 2

---

### Post by MoonLitOwl on 2011-10-27
> **raja.genupula said:**
> First install dconf-tools 

Code:
sudo apt-get install dconf-tools

Then in the terminal (or you can use ALT+F2 to bring up the run dialogue box) type

 dconf-editor

When the dconf-editor appears, navigate to Desktop > Unity and fix the form factor to "Desktop", that way the dash will not take up the whole screen. If the form factor is fixed at netbook the dash will always open fullscreen, if it is automatic then the system would decide for you.

All the best

You lost me at "fix the form factor" bit.

I took a screen shot to show it all.

---

### Post by MoonLitOwl on 2011-10-27
> **Frogs Hair said:**
> You can add a few more options with this ._[http://www.omgubuntu.co.uk/2011/10/unity-2d-tweak-app-updated-for-11-10/](http://www.omgubuntu.co.uk/2011/10/unity-2d-tweak-app-updated-for-11-10/)_

Installed and got it to work! Thanks for sharing.

---

### Post by raja.genupula on 2011-10-28
hmm again .....may be i should .....

Hi man 

   Now could please tell where you lost ? I will try

open your terminal and do this 

**gsettings set com.canonical.Unity form-factor &#8220;Desktop&#8221;**

all the best.

---

### Post by MoonLitOwl on 2011-10-28
> **raja.genupula said:**
> we are glad that your issue solved. please mark your thread as solved from thread tools.

But it hasn't been solved. I was saying thanks for the link to something else.

---

