---
title: "Updated Screenlets to 0.0.14, now Screenlets Manager won't start"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2008-03-18
I just updated yesterday and now the Screenlets Manager won't start (Applications > Accessories > Screenlets). 
There was an update via Update Manager, so I guess I have the Screenlets repository though I don't see it in my sources anywhere...?

When I run "screenlets-manager" from the terminal, I get this:
> Unable to load 'Wc' from /home/riley/.screenlets/Wc: No module named numpy 
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in <module>
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 133, in __init__
    self.load_screenlets()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 259, in load_screenlets
    info = ScreenletInfo(s, meta['name'], meta['info'], meta['author'], 
TypeError: 'NoneType' object is unsubscriptable


Is anyone else having this problem? Or have any idea how to fix it?

---

### Post by FuturePilot on 2008-03-18
Try completely removing Screenlets then reinstall them.

---

### Post by rainwalker on 2008-03-18
So "mark for complete removal" in Synaptic, then install them again?

---

### Post by FuturePilot on 2008-03-18
Yes.

---

### Post by rainwalker on 2008-03-19
It didn't work.
I didn't quit the screenlets I have running or log out/back in after uninstalling them, do I need to do either of those?

---

### Post by FuturePilot on 2008-03-19
It might be worth a shot.

---

### Post by plun on 2008-03-19
Well, there is a mess with versions now....:(

Gutsy ver 0.0.10, Hardy ver 0.0.12  (in Ubuntu repo)

Gutsys version is really buggy

Please try latest from Getdeb ver 0.0.14

First remove existing

```
sudo apt-get remove --purge screenlets

```

and then Getdeb

[http://www.getdeb.net/app/Screenlets](http://www.getdeb.net/app/Screenlets)

:)

---

### Post by Whise on 2008-03-19
type in console

whereis screenlets-manager

remove those files , reinstall

---

### Post by rainwalker on 2008-03-19
> **plun said:**
> Well, there is a mess with versions now....:(

Gutsy ver 0.0.10, Hardy ver 0.0.12  (in Ubuntu repo)

Gutsys version is really buggy

Please try latest from Getdeb ver 0.0.14

First remove existing

```
sudo apt-get remove --purge screenlets

```

and then Getdeb

[http://www.getdeb.net/app/Screenlets](http://www.getdeb.net/app/Screenlets)

:)

Two things;
1. Why is it that I have to use "--purge" with that command, shouldn't Synaptic's "mark for complete removal" do that? I know it doesn't, and I'm wondering why...
2. gDebi said there is a later version in the software channel, but I installed it anyway. I'm about to log out/in to see if it worked...

---

### Post by rainwalker on 2008-03-19
Ok, so screenlets are technically working now, except that whenever I start one it says > There was a problem starting this screenlet
Try reinstalling it, if the problem continues please report the bug to the screenlet author but the screenlet will still start. I saw someone on Gnome-look had the same issue, but no solution was posted.
Also, when the screenlets start now, they don't zoom in (effect using Compiz), instead they just appear. The Update Manager is also saying I have an update for screenlets, should I install it?

P.S.
Are screenlets in the repos now? If not, I don't know where these updates are coming from...

---

### Post by FuturePilot on 2008-03-19
> **rainwalker said:**
> 
1. Why is it that I have to use "--purge" with that command, shouldn't Synaptic's "mark for complete removal" do that? I know it doesn't, and I'm wondering why...

The --purge option does the same thing that "Mark for complete removal" does in Synaptic. The only difference is that you're using the command line instead of the GUI.

> **rainwalker said:**
> Ok, so screenlets are technically working now, except that whenever I start one it says 
> There was a problem starting this screenlet
Try reinstalling it, if the problem continues please report the bug to the screenlet author 
but the screenlet will still start. I saw someone on Gnome-look had the same issue, but no solution was posted.
Also, when the screenlets start now, they don't zoom in (effect using Compiz), instead they just appear. The Update Manager is also saying I have an update for screenlets, should I install it?

P.S.
Are screenlets in the repos now? If not, I don't know where these updates are coming from...
I'm getting that error too. I'm using the latest Screenlets checked out from bzr. 
Screenlets are in the Backports repository. They were backported from Hardy.

---

### Post by plun on 2008-03-19
> **FuturePilot said:**
> 
I'm getting that error too. I'm using the latest Screenlets checked out from bzr. 
Screenlets are in the Backports repository. They were backported from Hardy.

Backported version is 0.0.10, really buggy.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=screenlets](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=screenlets)

Please use the Getdeb package instead.

---

### Post by FuturePilot on 2008-03-19
I'm not using the backported version. I keep Screenlets synced with the bzr branch. ;)

---

### Post by plun on 2008-03-19
> **FuturePilot said:**
> I'm not using the backported version. I keep Screenlets synced with the bzr branch. ;)

Well, thats something else and can be broken sometimes....:)

Getdebs release is a "stable one" with bugfixes.

---

### Post by FuturePilot on 2008-03-19
> **plun said:**
> Well, thats something else and can be broken sometimes....:)
Indeed. I remember it broke just a few days ago. :p

---

### Post by rainwalker on 2008-03-19
I'm getting this error with the getdeb one

---

### Post by FuturePilot on 2008-03-26
Just updated to Revision 216 from the bzr branch and that error seems to have gone away. :)

---

### Post by FuturePilot on 2008-03-26
Nevermind, still there.

---

### Post by Kevbert on 2008-03-27
I get the error with the getdeb version.  Even worse is the fact that I get four of the same screenlet on top of each other whenever I start one.  It doesn't matter how I start the screenlet.  I've tried a complete removal with Synaptec, reboot and then re-install via the getdeb webpage but still get the same problems.
I'm using Gutsy 64 bit.

---

