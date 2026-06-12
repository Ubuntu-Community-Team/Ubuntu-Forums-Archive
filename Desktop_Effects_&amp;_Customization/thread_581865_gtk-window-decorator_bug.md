---
title: "gtk-window-decorator bug?"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by 4KvRMU7Nnv on 2007-10-19
I'm pretty sure I haven't seen this issue addressed anywhere before, but with the gtk-window-decorator, when you maximize the window with certain metacity themes (like the default ubuntu theme) when you mouseover the minimize, maximize and close buttons, the whole top decoration bar becomes white and terrible.  It appears to be a redraw issue with the compositing of some kind.  below is a screenshot:

[[IMG]http://img62.imageshack.us/img62/4171/screenshotir1.th.png[/IMG]](http://img62.imageshack.us/my.php?image=screenshotir1.png)

Has anyone had this problem before?  I would also like to confim the fact that it does not occur in themes that do not have a mouseover effect.  Obviously this is because the composite manager doesn't have to worry about changing the image.  But with an awesome theme like the human theme, it does.  One way or another I would like to see this error go away.

---

### Post by Robvdl on 2007-10-24
Yes, it's a really annoying bug, happens on all default Gutsy installs, both 64 and 32 bit, if you have *any* NVIDIA card using the restricted drivers (possibly other cards too, but I don't know).

I have tried playing around with a few compiz settings, using the advanced compiz configuration app, but to no luck. It gets so annoying in the end, I have to turn the 3D desktop off.

The thing is, this bug has existed for me, ever since compiz and beryl merged into compiz fusion. I used to get around the issue in Feisty by using the emerald window decorator, but not quite sure how to do so in Gutsy yet. I know emerald is in the repository, but how do I tell compiz to use emerald instead?

This bug should really be fixed though, it's been around for far too long now, and I was really disappointed to see it again in a default (clean) Gutsy install, after upgrading from Feisty.

---

### Post by DariusS on 2007-10-24
I think I may be having a similar issue:
every time I turn on any desktop effects, the whole border (that has the min/max/close buttons on it) around all windows dissapears. tried playing with all general settings and all settings in the window decorator....to no avail. and yes, am running an Nvidia setup...installed new drivers in 6.06 about 2 months ago....upgraded yesterday to 7.10 to take advantage of desktop effects with compiz fusion, and can't!

---

### Post by Robvdl on 2007-10-24
Yes, that is exactly the same problem.I have found that it's theme dependent however. I know that it happens at least with the following themes: Human, Clearlooks, Glossy.

To fix it, I installed the Foresight Linux border theme and continued using Clearlooks for my controls theme, I know it doesn't happen with that border theme. I just unzipped mine (as root) in /usr/share/themes/Foresight (if you want all users to be able to see the theme). Or if there's only one user, you can also unzip it under /home/youraccount/.themes/Foresight which means you don't have to unzip as root.

I don't know what other border themes are immune to the bug other than that one.

---

### Post by break1979 on 2007-10-27
Hi,

I fixed the missing menubar/window borders as instructed on

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

with this command, it appends some lines to your xorg.conf file:

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```


I'm running Gutsy with a Nvidia 6600GT on AMD Sempron.

**BUT i also have the same bug as mentioned in the 1st post in this thread...**

---

### Post by Robvdl on 2007-10-27
I tried running the command listed above:

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

It added to my xorg file:

```
Option "AddARGBGLXVisuals" "True"
```

However, I already had this in my xorg file and it doesn't make any difference. Still getting the issue mentioned in post #1 where the window border of maximized windows sometimes disappears/goes grey. I am running a GeForce 7950GT.

But the issue is theme dependent, some window border themes do not do it. Example of themes that show this bug are:

Human
Clearlooks
Glossy

---

### Post by yogo on 2007-11-06
I have the same problem, every time I log out or start up, my borders are screwy, I have to open up themes and toggle between two themes and then everything is fine but it seems a little bit redundant.

---

### Post by 4KvRMU7Nnv on 2007-11-08
Ok, I now know why this happens, but still no fix.  It happens to themes that have a split gradient in the titlebar.  The default human theme is vertically split down the middle with a color change. because of this, when compiz redraws the border, it sometimes messes up.  I don't know why it doesn't happen when the window isn't maximized though.  And yes it is theme dependant, so another theme will work fine, but I want to use the default ubuntu theme becuase it is the most appealing to me and I hate emerald. 

If you do use emerald, the problem is gone, but i don't like emerald.  This problem is the only thing that keeps me from using the effects. :/

---

### Post by fela on 2008-03-26
> **Robvdl said:**
> The thing is, this bug has existed for me, ever since compiz and beryl merged into compiz fusion. I used to get around the issue in Feisty by using the emerald window decorator, but not quite sure how to do so in Gutsy yet. I know emerald is in the repository, but how do I tell compiz to use emerald instead?

you tell compiz to use emerald by installing emerald theme manager, and selecting in ccsm 'window decoration'. make sure it's enabled, restart X (dunno why, i did this and it worked), then select a emerald theme in emerald theme manager. should work

or you could do it another way, by editing /usr/bin/compiz. ```
sudo gedit /usr/bin/compiz
```

scroll down to where you see this: ```
USE_EMERALD="no"
```

change "no" to "yes". restart X and emerald should be enabled. :D

---

