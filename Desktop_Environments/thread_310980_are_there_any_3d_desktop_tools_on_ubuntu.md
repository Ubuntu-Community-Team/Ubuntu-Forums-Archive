---
title: "are there any 3d desktop tools on ubuntu?"
date: 2006-12-02
forum: Desktop Environments
---

### Post by holr on 2006-12-02
Hi,
  I have been using mandriva 2007 for a little while now and really like their "drak3d" tool which lets you easily enable and disable the 3d desktop. Are there any tools like this for ubuntu (more specifically kubuntu), or is it a case of following the guides and working it by hand?

thanks!

---

### Post by nandasunu on 2006-12-03
I've also been using Mandriva 2007 for about a month now and was impressed with the easy 3d desktop setup. I believe that Mandriva is unique in this regard, for sure there is nothing like that for ubuntu/kubuntu yet, it is supposed to be in the next release though. For now you will have to find some tutorials to get it working. I can't help you much more as I never got compiz or beryl working properly with ubuntu.

---

### Post by GreenHawkIA on 2006-12-03
I use Beryl - and the beryl-manager you can use with it sits in your task bar and enables you to switch between window managers, window decorators, along with easy access to emerald themes and setting your fall-back window manager in case of a crash.  If you used Edgy Eft, it's actually quite easy to install.
This thread should be a good starting poing:
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)
I used the guide from the wiki for my Intel 855 GM card and it worked flawlessly.  Look there for more info.
It's very similar to this:
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
Hope this helps.

> **nandasunu said:**
> I've also been using Mandriva 2007 for about a month now and was impressed with the easy 3d desktop setup. I believe that Mandriva is unique in this regard, for sure there is nothing like that for ubuntu/kubuntu yet, it is supposed to be in the next release though. For now you will have to find some tutorials to get it working. I can't help you much more as I never got compiz or beryl working properly with ubuntu.

---

### Post by igknighted on 2006-12-03
> **GreenHawkIA said:**
> I use Beryl - and the beryl-manager you can use with it sits in your task bar and enables you to switch between window managers, window decorators, along with easy access to emerald themes and setting your fall-back window manager in case of a crash.  If you used Edgy Eft, it's actually quite easy to install.
This thread should be a good starting poing:
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)
I used the guide from the wiki for my Intel 855 GM card and it worked flawlessly.  Look there for more info.
It's very similar to this:
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
Hope this helps.

Beryl-manager is just a part of beryl.  The mandriva drak3d tool helps with not just settings but also some of the setup.  I think Mandriva uses compiz tho, so I don't know how well you could port it to Ubuntu.

---

### Post by drphilngood on 2006-12-03
3Ddesktop may be what you´re looking for as it is somewhat easier to install.

See this thread:

[HOW TO: Switch desktops in 3D view! Cool!]("http://ubuntuforums.org/showthread.php?t=100169")

---

### Post by Cynical on 2006-12-04
[quote=nandasunu]I believe that Mandriva is unique in this regard, for sure there is nothing like that for ubuntu/kubuntu yet, it is supposed to be in the next release though.[/quote]

nah, suse and fedora also have one click desktop acceleration. It really shouldn't be implemented imo unless it lets you choose between xgl/aiglx/compiz/beryl.

---

### Post by Old Pink on 2006-12-04
Has to be the easiest:```
sudo aptitude install 3ddesktop
```(in terminal)

---

### Post by 3rdalbum on 2006-12-04
The 3ddesktop package is just a 3D-style workspace switcher. What the OP is asking for is a setup program for Beryl.

---

### Post by xpod on 2006-12-05
I started with the 3ddesktop in synaptic which just made me want Beryl all the more... They dont compare but it`s a good starter for getting the taste

---

### Post by igknighted on 2006-12-05
> **Cynical said:**
> nah, suse and fedora also have one click desktop acceleration. It really shouldn't be implemented imo unless it lets you choose between xgl/aiglx/compiz/beryl.

Mandriva's gives you a choice between AIGLX and XGL, however I believe it only ships with Compiz, and I don't know if you install beryl whether or not it gives you a choice.  NOTE: ATI and NVIDIA users wont get the choice to use AIGLX until after they install the proper drivers, Mandriva does not ship with a 9xxx driver for NVIDIA, nor will it properly set up the Radeon driver for ATI.

---

