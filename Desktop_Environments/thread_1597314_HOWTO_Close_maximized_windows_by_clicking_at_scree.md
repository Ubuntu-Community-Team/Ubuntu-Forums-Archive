---
title: "HOWTO: Close maximized windows by clicking at screen corner in Xfce4 Bluebird theme"
date: 2010-10-15
forum: Desktop Environments
---

### Post by Lawand on 2010-10-15
I have recently downloaded and installed Xubuntu 10.10, and I really liked the new default Xfce4 theme Bluebird. However, it has one small issue which is that you can&#8217;t close a maximized window by moving the mouse cursor into the upper-right corner of the screen and clicking (with the upper panel being disabled), rather you should click at the close button which is located at the upper-right area of the screen but not exactly at the corner.

I know that this is a small issue, but I think that at least some advanced users would agree with me, because after using a certain OS for a long enough amount of time, one prefers to do things in the most easy and fault intolerant way.

Anyway, I made a modified version of the Bluebird theme which doesn&#8217;t have that issue, here are the steps necessary to install and activate it:

[LIST]
[*]Download the theme package from [here]("http://www.box.net/shared/fsxk1htpya")
[*]Unpack and copy the folder &#8220;Bluebird-Edited&#8221; into &#8220;/usr/share/themes&#8221; (you&#8217;ll need root privilege to do so)
[*]Select the theme &#8220;Bluebird-Edited&#8221; in [Settings > Appearance] and [Settings > Window Manager]
[/LIST]

Note that this version of the theme was only tested in Xubuntu 10.10, but I assume that it works with other versions of Xubuntu as well as other distributions or OSes that contain Xfce4

---

### Post by squalou on 2011-08-03
Just to tell ya you're my hero.

Forgetting those important pixels in the corner is a real pita, and a terrible GUI misdisign.

Thank you  so much !

(note that greybird has the same problem, i'll try to hack the theme myself following what's in your edited theme)


NOTE : in fact ... i cannot have your theme working properly, always some ixels lost at the top.. ??

---

### Post by cariboo on 2011-08-03
this is really in the wrong place, and it's over a year old. Closed.

**Edit**: reopened by request, in the proper sub-forum

---

### Post by Lawand on 2011-08-04
@squalou: I am glad you found my theme edit useful.

About greybird, I didn't notice the same issue in it. I am testing it right now and clicking in the upper-right screen corner closes the maximized window, maybe some setting or configuration on your machine is having an effect on it and on my edited version of Bluebird as well.

Can you post a screen shot of Bluebird-Edited to show me the problem, and it would also help if you tested it on a fresh installation of Xubuntu 10.10 or 11.04. I also need some information like the screen resolution you are using.

Keep in mind I am not a designer so I might not be able to help you...

---

### Post by squalou on 2011-08-14
That's utturely weird.
I've tried an old xubuntu live CD (10.04), featuring xfce 4.6 + theme albatross.

Top right corner works.

I've installed this theme on my xfce 4.8 (archlinux distribution in this case) : top right corner is not correct.

I'll try to post a scrrenshot of what it looks like.

Edit : here's the screenshot, while hovering the corner. The upper part of the screen decoration is clearly not sensitive.

[https://picasaweb.google.com/lh/photo/YkVGVxU4oBOz3bkkgU9BBg?feat=directlink](https://picasaweb.google.com/lh/photo/YkVGVxU4oBOz3bkkgU9BBg?feat=directlink)

---

### Post by squalou on 2011-08-14
Looking at that :

[http://www.xfce.org/about/tour](http://www.xfce.org/about/tour)

vs that :

[http://www.xfce.org/about/tour46](http://www.xfce.org/about/tour46)

makes me wonder if it's nt a 4.8 issue. Would be so surprising from xfce, but why not ? Any good results with 4.8 ?

---

### Post by Lawand on 2011-08-14
I have tested Bluebird-Edited with fresh installs of Xubuntu 10.10 and 11.04 ( which includes Xfce 4.8 ) and it worked. About other distributions, it might not work and I am unfortunately unable to help you because I just made what's called a quick and dirty solution when I edited Bluebird. I don't really know the in's and out's of Xfce themes.

Tell you what, can you contact the guys that originally designed Bluebird? Maybe they can edit the theme so that corner-clicking would work in all distributions because they can perform a global solution instead of my quick and dirty one.

Note: I can't access the screenshot you posted.

---

### Post by squalou on 2011-08-15
Oh.
My.
God.
I'm stupid.

I changed the *themes*, edited the *themerc* file, etc...
but never until this morning did I look at "Window Manager" options.
...
in which you tell the "style" of your windows....

Afterwards, I consider it a bit confusing, having a theme for the desktop in one place called "appearance", and a so called "style" in another place called "window manager".

Both should be linked under the "theme" name.


That beeing said, I'm the noob this time, 

i'll just go and hide for a while ;)

thanks anyway !

---

### Post by Lawand on 2011-08-15
You're welcome.

So, is everything ok now? If so, can you confirm which distributions Bluebird-Edited worked with? Thank you.

---

