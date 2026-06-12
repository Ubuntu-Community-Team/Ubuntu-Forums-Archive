---
title: "Installing Cinnamon desktop issues"
date: 2012-04-27
forum: Desktop Environments
---

### Post by Senior_Buckethead on 2012-04-27
Hello All,

I have installed 12.04, and got rid of that dreadful unity desktop, reverting back to 10.04-10.10 menu environment.
I thought I installed cinnamon, but upon rebooting, after logging in under cinnamon, I get the desktop background and nothing else. No menu, no bars, nothing.
So, I log out, and log in under gnome classic, and and all loads great.

How do I install cinnamon correctly? Can anyone point me in the right direction? 

And what is stopping the desktop from loading correctly?

and note *Please don't lecture me on why you love unity. Its not the question*

---

### Post by RichardCain on 2012-04-28
I have Cinnamon working perfectly on 11.10 and love it, so no lectures here!

How did you install Cinnamon?  Through a PPA or from tarball?

You could try logging into classic, deleting the folder *~/cinnamon* and logging in again.  If that doesn't work, uninstall Cinnamon and install [this way]("http://maketecheasier.com/cinnamon-alternative-for-gnome-shell/2012/03/19").

---

### Post by Senior_Buckethead on 2012-04-28
Thanks Richard

I removed the old cinnamon installation with:
```

sudo apt-get remove cinnamon
sudo apt-get autoremove
sudo apt-get purge cinnamon

```I logged out, then logged back in under gnome-classic.

Then I reinstalled cinnamon:
```
[COLOR=#c20cb9][B][FONT=monospace]
[/FONT][/B][COLOR=Black]sudo [/COLOR][/COLOR][COLOR=Black]add-apt-repository ppa:gwendal-lebihan-dev[COLOR=#000000]**/**[/COLOR]cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
[/COLOR]
```Then I logged out and logged back in under cinnamon

But nothing looks any different. There is no menu at the bottom. I can't figure out why that is.

Glenn.

---

### Post by RichardCain on 2012-04-28
Hi Glenn,

Well, it's obviously not a problem with cinnamon, if that hasn't worked, so we'll have to dig a little deeper.

Do you have Unity installed?  If so, log into that and purge gnome-shell and cinnamon, then re-install cinnamon.

I've just done a clean install of 12.04 and while Unity displayed the same symptoms as you had, I was able to drop back to 2D, install Cinnamon as described and now everything is working fine.

2 further questions:
Did you upgrade or clean install?
32- or 64-bit? (not that that should matter too much; I've had it working on both)

---

### Post by Senior_Buckethead on 2012-04-29
Hi Richard,

Thanks for the reply. I had to reinstall, I got the desktop in such a knot, it was easier to just start again. Soon as I got rid of unity, installing cinnamon was a snap.
Still, I do everynow-and-again get a freeze-up desktop and cinnamons to blame. No doubt they will fix this, I mean 12.04 is so new.

Glenn.

---

### Post by RichardCain on 2012-04-29
That's the thing I love about Linux in general and Ubuntu in particular.  You're never more than 20-30 minutes away from a clean, fresh install; then you're up & running as before - assuming you back up regularly, of course!  :)

Please click on Thread Tools at the top and Mark as Solved.

---

