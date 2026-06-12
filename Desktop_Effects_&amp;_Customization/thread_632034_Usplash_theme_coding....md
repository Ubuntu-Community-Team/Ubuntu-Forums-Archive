---
title: "Usplash theme coding..."
date: 2007-12-05
forum: Desktop Effects &amp; Customization
---

### Post by Disz on 2007-12-05
I'm attempting to try to figure-out why the 'fingerprint' usplash theme isn't behaving correctly.
(See: [fingerprint]("http://www.gnome-look.org/content/show.php?content=50468&forumpage=8&PHPSESSID=8a4ab01d3a959b8b361a993c79a8928c")

I've verified that my environment is set-up correctly (menu.lst, build env for compilling the .so, using the latest cvs snapshot, etc) and I can compile and install the theme without any issues, but I'm getting the "black box error" - e.g. the 'text box' portion of the theme gets covered by a large, black, rectangular area during boot.

Verbose is OFF per my menu.lst...so that's not my issue. Turning it on results in a second box.

At the moment, I'm looking at the code but don't know enough about how usplash themes are supposed to act/be coded to know for sure if I've found the problem or not. It looks like it may be a  placement issue...maybe size, I'm not sure.

Anyone able to lend a hand?

-D.

---

### Post by smartboyathome on 2007-12-05
Well, the theme is also available for splashy, if you want to give that a try (you can get the theme from gnome-look.org and splashy from [here]("http://splashy.alioth.debian.org/")).

---

### Post by Disz on 2007-12-07
Thanks for the reply,

I've actually had poor luck with splashy, to be honest... It must not like my laptop.

-D.

---

### Post by celticbhoy on 2007-12-07
What Ubunutu version you using ?
I had it working fine under fiesty but couldn't get it to go right in Gutsy. All the alignment was out as well as the black box.

---

### Post by Disz on 2007-12-08
> **celticbhoy said:**
> What Ubunutu version you using ?
I had it working fine under fiesty but couldn't get it to go right in Gutsy. All the alignment was out as well as the black box.

I'm actually using gutsy - amd64.

I've tried playing with the theme code a bit, but I can't get rid of the black box. I did notice that the dimensions of the status bar matches the dimensions of the box, but I haven't messed with it too much. 

I tired the author's sourceforge site, but he seems to be bored and/or working on the 'comptus' theme. Any uber-coders willing to offer a fix for gutsy (or point me in the right direction)?

-D.

---

### Post by LinuxIsInnovation on 2007-12-14
Yeah.. same problem with me.. Looks like this theme doesnt work with amd64 architecture..

---

### Post by Tanno on 2008-02-21
I have the same issue. AMD64 and Black box issue. Everything else with it looks fine. I'm running Ubuntu 7.10.

I'm not sure how to proceed on trying to fix this just yet. I'm researching that. (I'm new to Linux - aka, Windows transplant.)

---

### Post by Apple.boi on 2008-03-26
this worked for me
[https://bugs.launchpad.net/ubuntu/+bug/86666/comments/104](https://bugs.launchpad.net/ubuntu/+bug/86666/comments/104)
i was having the same large black rectangle in between the two progress bars. 
however like stated in the article "vesafb" was probably blacklisted for a reason.
there is more info about some of this tranperency problems here
[https://answers.launchpad.net/ubuntu/+source/usplash-theme-ubuntu/+question/22579](https://answers.launchpad.net/ubuntu/+source/usplash-theme-ubuntu/+question/22579)

---

