---
title: "Marlin File Browser Crashing"
date: 2012-02-28
forum: Desktop Environments
---

### Post by bman on 2012-02-28
Anyone here using this File Manager?

Every once in awhile, when I click on something it just closes. Not errors or anything like that, just gone.

Anyone having this issue?

---

### Post by Frogs Hair on 2012-02-28
I have been using marlin with Unity and the Gnome Shell as default for a couple of weeks without any problems. There is a warning on the page that I used to install the PPA that it may be unstable . You could try to start it from the terminal and see if any errors are reported. There is always some risk when using a PPA.

---

### Post by bman on 2012-02-29
Interesting, I was hoping it was a known issue. Does not happen often, but still does happen.

---

### Post by coldjeanz on 2012-03-10
Happening way too frequently for my tastes now. Has done it probably 6 times in the last hour. As much as I like the interface of it that's unacceptable, back to nautilus for me.

---

### Post by kazztan0325 on 2012-03-12
I also like to use Marlin, however it is still not my main file manager, because I have same problem occasionally too.

I checked Bug reports in Launchpad a little while ago.

**Marlin > Bugs > Bug #912539 "Consistent Crashes when renaming files"**
[https://bugs.launchpad.net/marlin/+bug/912539]("https://bugs.launchpad.net/marlin/+bug/912539")

**Marlin > Bugs > Bug #919454 "random crash when opening folders"**
[https://bugs.launchpad.net/marlin/+bug/919454]("https://bugs.launchpad.net/marlin/+bug/919454")

As far as I read these, it seems these bugs have already be fixed on latest revision 798..., but in my case it still occurs occasionally.

---

### Post by Frogs Hair on 2012-03-12
Still working fine with version 0.1 and I have been using Gloobus preview for the duration.

---

### Post by ammonkey on 2012-03-12
@kazztan0325 in fact those bugs have been fixed in the pangolin branch (which last revision is 818 ).

[https://code.launchpad.net/~marlin-devs/marlin/pangolin](https://code.launchpad.net/~marlin-devs/marlin/pangolin)
So those bugs are fixed if you're using Ubuntu Precise Pangolin and Marlin ppa, random crashs could happen on the oneiric version.

---

### Post by kazztan0325 on 2012-03-12
> **ammonkey said:**
> @kazztan0325 in fact those bugs have been fixed in the pangolin branch (which last revision is 818 ).

[https://code.launchpad.net/~marlin-devs/marlin/pangolin](https://code.launchpad.net/~marlin-devs/marlin/pangolin)
So those bugs are fixed if you're using Ubuntu Precise Pangolin and Marlin ppa, random crashs could happen on the oneiric version.

Hi @ammonkey,

I'm sorry I should have mentioned my PC circumstance.

I am running "Xubuntu 12.04 Beta 1" in VirtualBox 4.1.8, and I have not tried Marlin on it yet.
I am running "Linux Mint 12 with Xubuntu Session" on my real machine (Lenovo ThinkPad X200s), and I sometimes use Marlin on it.

Thank you for your information about the oneiric version of Marlin.

---

