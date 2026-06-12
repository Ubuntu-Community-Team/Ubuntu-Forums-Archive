---
title: "Low Latency Kernel?"
date: 2005-02-08
forum: Desktop Environments
---

### Post by bobmitch on 2005-02-08
I have recently installed jack, audacity and hydrogen.  With the help of the author of audacity (Paul Davis) I got everything working properly through jack and my pro-soundcard. (Terratec ews 88 mt)

Having been stoked at getting this far, despite my unfamiliarity with linux, I am now looking to try getting the low latency patches/modules for my kernel installed.

Can anybody point me in the right direction?  Is it even advisable? :)

I am aware of the main livecd's which are audio specific, but I`d like to be able to use my main ubuntu box if possible.

I am also aware of the security problem these kernel alterations imply - but that is a secondary concern at the moment.

So, are there any ubuntu users / devs out there who have made this drastic step successfully who are willing to share their experience / advice?

Thx,
mitch

---

### Post by ioliver on 2005-02-08
I'm pretty sure that the 2.6 kernel already has preemption as standard and unless you're going for "real time" I'm not sure what else there is.

Do you have a URL to some more information about these patches?

Regards

Ian

---

### Post by ioliver on 2005-02-08
Ah, maybe you mean realtime LSM? A web search suggests this is available for Ubuntu (in universe) but you might have to build the module yourself (and then do the same whenever you change kernel).

Maybe this thread will help? [http://ubuntuforums.org/archive/index.php/t-3024.html](http://ubuntuforums.org/archive/index.php/t-3024.html)

It's not a particularly drastic step. You can always remove the module again!

This thread has a basic "how to" a few messages down - [http://kerneltrap.org/node/4471](http://kerneltrap.org/node/4471)

Hope this helps. Not using it myself so sorry if I got the wrong end of the stick and ma just confusing matters!

Regards

Ian

---

### Post by p!=f on 2005-02-08
You might also want to try Con Kolivas patchset:
[http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/)
with audio hints here
[http://ck.kolivas.org/audio_hints.txt](http://ck.kolivas.org/audio_hints.txt)

More info can be found on his page.

If you're about to build a kernel based on this patchset be sure to turn preemption off. 
Default Hoary kernel as of 8.2.2005 (D.M.Y).
```

[~] > grep -i preempt /boot/config-2.6.10-3-k7
CONFIG_PREEMPT=y

```
should be set to "n" when using Con Kolivas patchset.

---

### Post by bobmitch on 2005-02-08
[QUOTE=ioliver]Ah, maybe you mean realtime LSM? A web search suggests this is available for Ubuntu (in universe) but you might have to build the module yourself (and then do the same whenever you change kernel).

Maybe this thread will help? [http://ubuntuforums.org/archive/index.php/t-3024.html](http://ubuntuforums.org/archive/index.php/t-3024.html)

It's not a particularly drastic step. You can always remove the module again!

This thread has a basic "how to" a few messages down - [http://kerneltrap.org/node/4471](http://kerneltrap.org/node/4471)

Hope this helps. Not using it myself so sorry if I got the wrong end of the stick and ma just confusing matters!

Regards

Ian[/QUOTE]

Ian,

That is exactly what I was looking for. Thanks! :)   

Mind you, when you say 'not a particularly drastic step', for someone as new to linux (note: not computers ;) ) as me, it looks kinda drastic. :)   
I thought I was Berti Big Bollocks when I got ndiswrapper working with my wireless card, but this is a different kettle of fish.  

Cheers,
mitch

---

### Post by ioliver on 2005-02-08
Everything is daunting until you do it the 1st time.

A couple of months ago, I had never installed Linux, never used it on the desktop (though used Unix at univ yonks ago) and had certainly never built kernel modules! However, as I'm currently running a project to port Linux to a new architecture, I'd read many books on the kernel and device drivers. But book learning is no substitute for taking the practical!

So now I've set up a home media server using Debian (all cli, no x) and have tried various desktop distros before hitting on Ubuntu.

Last week I built my first kernel module, one called fuse.

I installed all the dependencies (I listed a load but you'll also need gcc. Try it, google when errors fly out, and then use synaptic to grab other bits)
I downloaded fuse to /usr/local/fuse with cvs (downloading a tar/tgz/etc. is fine but if you figure using cvs then it's easier to keep up to date)
Configured with "sudo ./configure"
Built with "sudo make"
Installed with "sudo make install"
Got the kernel to load it with "sudo modprobe fuse" (realtime has loads of command line options at this stage)
To remove it I use "sudo rmmod fuse"

I have also added it to /etc/modules, but I understand you can use modconf for this. If anyone else has tips on using non-binary kernel modules with Debian/Ubuntu, then I'd love to hear them!

Good luck!

Ian

---

### Post by 23meg on 2005-05-05
for right now i'd suggest waiting for the 2.6.12 kernel, which it seems will be around in a few weeks.

---

### Post by MetalMusicAddict on 2005-05-05
bobmitch. I have been watching your posts regarding Ardour/audio recording on linux  and have been exploring it myself. Im sure youve talked to those guys on their IRC channel. They pointed me [HERE](http://ccrma.stanford.edu/planetccrma/software/introduction.html). I would rather not use FC so I am very interested in how your doing with this.

I am a Pro-Tools trained engineer. I would love to do multitrack recording in linux. :)

Heres a new screenshot:
[IMG]http://ardour.org/img/main-screenshot-small.png[/IMG]
[Bigger](http://ardour.org/img/main-screenshot-big.png)

---

