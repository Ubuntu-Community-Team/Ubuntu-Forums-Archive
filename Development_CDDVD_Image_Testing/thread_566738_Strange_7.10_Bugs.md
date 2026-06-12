---
title: "Strange 7.10 Bugs"
date: 2007-10-03
forum: Development CD/DVD Image Testing
---

### Post by Echo35 on 2007-10-03
Last week I decided to give the 7.10 beta a whirl. It installed correctly, booted correctly and worked fine. When I rebooted however, it all went downhill. First off, my monitor resolution tanked (from 1440x900 to 1024x768). I tried editing xorg to include my resolution (since xorg was apparently overwritten) but that did nothing, because it would just rewrite on the next boot. I set my nVidia driver to recognize my resolution, but that wouldn't work either. I even tried setting compiz to take my resolution but that didn't work. After trying all this, it eventually let me set 1440x900, but the screen itself was still 1024x768, so I had to scroll around the screen. Then, after booting again, it randomly decides to work. Whatever, its ok now, except that the log in screen is STILL 1024x768 even though its set at 1440x900. Next, after that all worked, I tried to customize my compiz through the configuration editor. I set stuff up, and clicked Custom for the visual effects settings, but that won't work. Every time I click it and hit ok, it reverts back to Extra. After it reverted back to extra, I even lost some previous functionality like expose. There is also an issue when I log in. As soon as I do, I get a crash report for "upsplash" and the top panel on my desktop is not visible. I have to actually click in the area to make it show up. What the heck is going on?!?!

EDIT: I should also point out that I get no system level audio effects. When I log in, log out, click any buttons, etc. none of the system sounds work except for the drums when the log in screen opens. Normal audio does work however.

---

### Post by chocbar31 on 2007-10-03
Did you uninstall "ubuntu-desktop" at any point? 

Code:

sudo apt-get install ubuntu-desktop

---

### Post by Echo35 on 2007-10-03
No, I haven't touched any packages since upgrading.

---

### Post by Naatan on 2007-10-04
Same here on the compiz "custom" setting.. doesn't do anything..

---

### Post by Perpetual on 2007-10-04
> **Echo35 said:**
> the top panel on my desktop is not visible. I have to actually click in the area to make it show up. What the heck is going on?!?!


I know that this has been reported as a bug and the Compiz people are working on it.

[I]post by Danny Baumann on Compiz's mailing list this evening
(post at
[http://lists.freedesktop.org/archives/compiz/2007-October/002697.html):](http://lists.freedesktop.org/archives/compiz/2007-October/002697.html):)

Unfortunately I noticed    today that release 0.6.0 contains a bad problem
that allows e.g. desktop windows being stacked over normal windows when
they are mapped. This results in normal windows and/or panels not being
visible when compiz is launched with the Gnome or KDE session until the
desktop window is restacked once (e.g. by clicking on it if the "Raise
on click" option is enabled).

I will release a 0.6.2 ASAP that fixes that problem, but until then,
please either apply this commit to the release tarball:
[http://gitweb.freedesktop.org/?p=xorg/app/compiz.git;a=commit;h=b6c6acc70261d0942977441914c23e7a1c99215e](http://gitweb.freedesktop.org/?p=xorg/app/compiz.git;a=commit;h=b6c6acc70261d0942977441914c23e7a1c99215e)
or continue to use the compiz-0.6 branch.[/I]

---

### Post by Delvien on 2007-10-04
> **Echo35 said:**
> 
EDIT: I should also point out that I get no system level audio effects. When I log in, log out, click any buttons, etc. none of the system sounds work except for the drums when the log in screen opens. Normal audio does work however.

If you were running a specific kernel before you upgraded there should be one that is 2.6.22-x-<your previous kernel version> whether it be i386, k7 or i686, generic ( for me it was i686 generic) once you boot to this kernel your sound should be working fine.

---

### Post by Echo35 on 2007-10-04
I was not using any specific kernel before, and I only have one now.

---

### Post by Delvien on 2007-10-04
do a ```
 uname -r 
``` in terminal and paste the results

---

### Post by Echo35 on 2007-10-04
```
$ uname -r
2.6.22-12-generic

```

---

### Post by fingerle on 2007-10-10
Strange behavior indeed....

Tell "Screens and Graphics" what my monitor is (Well as close as I can due to SyncMaster 245bw not being on the list)

So, set LCD 1920x1200 (Native res for my monitor). O.K., so far so good. Go to screen resolution and argue with that till it "decides" to set that particular resolution.  Cool. got it..

NOPE!  reboot the system, and it pulls a microsoft on me and sets the res to what appears to be 1280x1024.  And does the old pan/scan thing to give me a 1920x1200... Settings still say 1920x1200...  
Very annoying.

---

### Post by Echo35 on 2007-10-10
Well, I managed to fix a few of my problems. Firstly, if you install the compizconfig-settings-manager from atp, it'll not only allow you to customize the settings, but it'll make the "Custom" bubble in the appearance manager work and add a little button next to it so you can set it up. To fix my resolution, I simply opened the nVidia manager as root (from the terminal) set up my screen resolution and hit "Save to Xorg conf file" and it worked after a reboot. The recent updates also fixed a few of the sounds, but once I'm actually in, none of the system sounds work. Audio works normally however. And the upsplash still doesn't work. Other than that it's all good.

---

### Post by WijbrandSchaap on 2007-10-11
Hi 
Just did my upgrade, and already miss good old Beryl on my feisty Desktop. Compiz started bij repeating the same bug i had a year ago: It made my window borders disappear. Tinkered around with  the graphic settings, and have now ended up without eyecandy. But at leasrt my windowborders are back.
I have an NVidia Geforce 5700 LE, which worked flawlessly on Beryl, but does nothing on Compiz. And something has happened to Firefox also. I get these ugly fonts and choppy graphics like back in 1995. 
I've set my graphics driver to nv, as the nvidia ones didn't do anything good after the upgrade. Hope this helps. And is there eventually any possibility to get Beryl back, as an option? I don't trust Compiz as it lets me down again and again, and seems to be harsh on my old Celeron processor (only 1.8 Ghz).
Thanks in advance

---

### Post by fingerle on 2007-10-13
Well, I went from the Beta to the RC of Gutsy 32bit.  Seems that my little issue with the screen resolution has been corrected. Once I enabled the nVidia driver and restarted the rig, All was well in the world and the prefered res for my monitor was already applied. (That was quick)  Cudos to the Dev team..

Compiz-Fusion with it's related issues works as expected, and tho I still think the settings manager should be loaded at install time it looks like that would cause a CD-ISO size problem.


Looks good, Works great, nice and stable for me...  (Tho it can't locate my Epson scanner that's not surprising as none of the other distros I've played can either) LoL...

Nice and quick for running Boinc projects too. 

Keep squishin those bugs y'all...  Looks like this one is a keeper.  [img]http://www.cosgan.de/images/midi/froehlich/a070.gif[/img]

---

### Post by WijbrandSchaap on 2007-10-13
Indeed, the latest updated nvidia-glx-new driver works flawlessly. I found that out yesterday. Only problem remaining are the fonts in firefox. I already have set the rss-layout thing in about:config to 0, but that only fixes the size, not the looks. Have now changed my default browser to Opera. Works great.

---

### Post by Echo35 on 2007-10-13
Also seems like the latest update fixed the top bar disappearing issue. For me anyway.

---

### Post by fingerle on 2007-10-13
Hahahahhaa!!!   I totally missed that... :lolflag:

---

