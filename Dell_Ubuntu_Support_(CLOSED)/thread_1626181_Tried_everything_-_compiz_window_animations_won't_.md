---
title: "Tried everything - compiz window animations won't work period."
date: 2010-11-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sukuraidogai on 2010-11-20
I'm running a Dell Latitude E6500 with a Nvidia Quadro NVS 160 graphics card on 32 bit Ubuntu.

I have installed every compiz related program from the synaptic package manager, including compiz-fusion-plugins-main and compiz-fusion-plugins-extra.  I have tried completely uninstalling and reinstalling the individual and all compiz files.  

I have tried simple-ccsm.  The "open window" "close window" "focus window" and "minimize window" boxes under the animation tab are all greyed out and un-clickable. 

Both "Animations" and "Animations Add-On" are checked in ccsm.

Interestingly enough, I have installed Ubuntu on my room-mate's computer using the exact same process I did to install on mine, except he has a different graphics card/ different computer altogether and I installed 64 bit on his instead of the 32 bit installed on mine.  His Ubuntu's compiz settings work perfectly with all of the fusion animations while mine doesn't.

I HAVE noticed that when I go to the "animations" effect settings on his computer, he has 5 different tabs including "open window" "close window" etc. while I only have 1 tab and that's the "general" tab.  His was a point and click interface while mine I have to type "animation:Fade" or "animation:Burn" or whatever.  I have checked the version of CCSM in the synaptic package manager on his computer which says "1:0.8.6-0ubuntu9.1", and mine is the exact same.

Really Strange Thing:
I actually have seen the "burn" animation ONCE while I was in the process of figuring out how to do this stuff.  I saw it when I closed a firefox window.  I opened and closed again, but nothing happened ever again.  I find this extremely queer.

Also, to clarify, the basic animations, as well as everything else in Compiz works perfectly.  I can get the fade, glide, and such animations to work, but I know these aren't installed from the fusion extension.  Also, it's strange how I can modify these simple animations in ccsm with simple-ccsm just has greyed out boxes.

Any Linux god/goddesses out there want to tell me what's wrong?

---

### Post by sukuraidogai on 2010-11-20
Hmm it turns out I had a beta graphics driver installed.  It didn't like that.  Everything works now.

---

### Post by Godspell on 2010-11-20
How did you end up installing beta graphic drivers in the first place?

Did you download and install latest ones from Nvidia website?
If so, could you please tell me the version because I was thinking of switching drivers as well. Maybe I can avoid the version you had the problem with.

You see, I also have graphics problem with my Dell Vostro 1700 with Nvidia Geforce 8600m GT. Compiz animations (including magic lamp and cube) tend to get choppy a little bit.
It's frustrating because you know for a fact that the hardwares are more than capable of performing such things.

So, how did you get it sorted at the end? Did you just choose one of the drivers from 'System > Administration > Additional Drivers'?
I'm using the recommended one from there.

Thanks.

Regards,
GS

---

### Post by MacintoshLover on 2010-12-07
I am having a similar problem, but I don't think it is caused by my graphics card driver. It says mutter is running and it can't switch to other effects. Any ideas? See my post, my username is MacintoshLover, and the post is called Compiz doesn't work!

---

