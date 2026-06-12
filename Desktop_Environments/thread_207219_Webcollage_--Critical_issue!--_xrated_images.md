---
title: "Webcollage --Critical issue!-- xrated images"
date: 2006-07-01
forum: Desktop Environments
---

### Post by nithska on 2006-07-01
I am running Ubuntu 6.06, upgraded from 5.10: I had the more robust screensaver module before the upgrade and now have the gnome-screensaver.  I am not concearned about that, but what does concearn me is the WebCollage screensaver.

I walked in on our family computer with XRATED images all over the screen.  I have children in the house and this is unacceptable.  I have also helped colleges at work install Ubuntu on their laptops and if this screensaver starts while we are at work we could get fired.  If it starts while they are home: their wives or kids might see this trash.  

I see no way too disable this screensaver: what is an immediate solution for this?  I don't mean to sound demanding: I get the fact that the coders who make this software possible do it without compensation for the most part, AND this is critically important to fix.

Thanks all.

Brandon

---

### Post by aysiu on 2006-07-01
Can you explain what webcollage is? I'm not seeing it as an option in the screensaver preferences.

---

### Post by Raavea on 2006-07-01
The closest I have found so far is the 'Pictures Folder' screensaver, which is displaying all the pictures in my pictures folder..

 Will report back.

EDIT: I haven't found it. I'll check the repos next.
EDIT2: Nothing in the repos.
 'I don't mean to sound demanding:' Don't worry about it, I'm sure everyone here understands completely. Is there no way you downloaded this screensaver elsewhere? Which desktop environment are you using? I'm in ubuntu gnome, and couldn't find it. Perhaps it's only found in another *buntu, such as edu, xub, kub...?

---

### Post by aysiu on 2006-07-01
I still don't know what this "webcollage" thing is. I see GLSlideshow, but that's not the same thing, right?

---

### Post by nithska on 2006-07-01
[QUOTE=aysiu]Can you explain what webcollage is? I'm not seeing it as an option in the screensaver preferences.[/QUOTE]

Aysiu,

Thank you for your help.  WebCollage is in my screensaver list in gnome screensaver.  I ran Synaptic to see if I inadvertantly installed this and nothing comes up when I run a search for WebCollage.  Note that until recently, possibly post upgrade to 6.06 (or I just didn't notice) I had a different screensaver module that either did not have this or it was not configured (the old screensaver let me select the screensavers that were enabled.

In screensaver preferences, WebCollage is right between Wander and Whirlwindwarp.

Brandon

---

### Post by aysiu on 2006-07-01
Hm. Except that I don't have webcollage, wander, *or* whirlwindwarp.

Did you, by chance, install *xscreensaver-data-extra* or *xscreensaver-gl-extra*?

And when you say "xrated images," do you mean scantily clad people or people engaged in actual sexual acts?

---

### Post by nithska on 2006-07-01
[QUOTE=aysiu]Hm. Except that I don't have webcollage, wander, *or* whirlwindwarp.

Did you, by chance, install *xscreensaver-data-extra* or *xscreensaver-gl-extra*?

And when you say "xrated images," do you mean scantily clad people or people engaged in actual sexual acts?[/QUOTE]

Actual sex acts.  The kind of thing in the ubuntu calendar doesn't bother me so much, but these are pretty nasty: it looks like it pulls random images from the web... I will checkk on the data-extra and reply back.

BB

---

### Post by nithska on 2006-07-01
[QUOTE=aysiu]Hm. Except that I don't have webcollage, wander, *or* whirlwindwarp.

Did you, by chance, install *xscreensaver-data-extra* or *xscreensaver-gl-extra*?

And when you say "xrated images," do you mean scantily clad people or people engaged in actual sexual acts?[/QUOTE]

This is what I have installed that is screensaver related (I use Ubuntu but also have kde installed to use some apps from that environment):

gnome-screensaver
kscreensaver
rss-glx 
screenaver-default-images
xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl

I'm not too picky about what screensaver module I have running, but right now its gnome screensaver based on system monitor.

---

### Post by compwiz18 on 2006-07-01
Howdy...

Looks to me like xscreensaver is installed.  This problem can be fixed by running xscreensaver (open a terminal, type xscreensaver, and hit enter).  Once the box pops up, click settings, then scroll down to the offending screensaver, and uncheck the little box next to it.

Hope that helps.

EDIT: Didn't see the most recent post.  Try **sudo apt-get remove xscreensaver-data** ... that might fix it.

---

### Post by aysiu on 2006-07-01
Apparently, that's the way it's supposed to work...

I couldn't find this warning except through XFCE, though (there's no way to find it in Gnome).

It seems you can filter images using something called VidWhacker?

---

### Post by nithska on 2006-07-01
[QUOTE=aysiu]Apparently, that's the way it's supposed to work...

I couldn't find this warning except through XFCE, though (there's no way to find it in Gnome).

It seems you can filter images using something called VidWhacker?[/QUOTE]


Thanks for your help everyone.  I removed xscreensaver-data-extra and kscreensaver (the later may not  have been necessary and if I ever decide to go back to kde i will reinstall that).  Incidentally, the pacakge was already deselected in screensaver properties, but it would still run in gnome screensaver.  I could only get rid of it from the gnome screensaver by removing the data-extra package.  Too bad, b/c it had some other screensavers that I liked.

Oh well: problem solved.  thanks again!

BB

---

