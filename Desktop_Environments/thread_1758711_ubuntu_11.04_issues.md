---
title: "ubuntu 11.04 issues"
date: 2011-05-15
forum: Desktop Environments
---

### Post by NexusN on 2011-05-15
Hello everyone, 
I have just moved to ubuntu 11.04 yesterday,
but I have some issues in customizing the environment.

First, I have been trying unity since beta, and regrettably it does not fit my need eventually, I can't even move to to the bottom, scroll the icon won't hide the active windows, cannot drag reorder, many reasons pushed me back to classic mode + AWN.

On rolling back things worked fine except a few things, th mouse edge binding.

On 10.10, I used to set that when I click the left click of my mouse touching the right edge, I can get into the scale windows switcher.

Second, I cannot change the mouse point theme.
I used to use the big red glass pointer theme, but now whatever I select it stuck at the default.

I am sorry to say that but ubuntu 11.04 does look unpolished and buggy, hope that 11.10 would be something improved much.

Thank you for reading, if you have the ideas why, may you leave me a message here.

---

### Post by NexusN on 2011-05-15
For part of the issue, I think I have figured out why.
The mouse pointer theme sucks after I updated my system right after the installation.

Immediately after the fresh install without internet, setting the mouse is fine, but actually after I have updated the system by update manager, the theme gone.
But I can still see the theme when moving my pointer into the browser.

So would anyone take this bug into account?
Thank you.

---

### Post by NexusN on 2011-05-16
Bump.........

Noone is sharing the same issue with me?
Did I miss out anything that I can set?

Anyway, ubuntu 11.04 does disappoint me, I did not ask for an OS that works for me out-of-the-box, but this time it even lacks the quality of customization....which have been painless in its ancestors.

---

### Post by wildmanne39 on 2011-05-16
> **NexusN said:**
> Bump.........

Noone is sharing the same issue with me?
Did I miss out anything that I can set?

Anyway, ubuntu 11.04 does disappoint me, I did not ask for an OS that works for me out-of-the-box, but this time it even lacks the quality of customization....which have been painless in its ancestors.
Hi, I have not seen this problem before, it looks like no one else is reporting this issue, but you could look and see if there is a bug report file on this issue. :D

---

### Post by NexusN on 2011-05-16
Thank you for your reply,
I have been trying to figure out why,
I installed the first time as it was beta, the cursor theme was not changing and edge trigger was not working.
Later I fresh installed a release, the same happens, as I was installing with internet available, I did not spot the cause.
I clean install the second time after a day without internet, I find that I can actually do what I intended in ubuntu classic, but after I have updated my system, all of them disappered after the restart.
I was testing on the same computer and at the moment I don't have another computer to try.
 
Although quite unlikely to be caused by my system, laptop, Lenovo Y450a, I should try on another system.

---

### Post by Copper Bezel on 2011-05-17
I'm not really understanding the specifics of the problem, here. What exactly are you trying to do? 

It sounds like using the Classic desktop or at least disabling the Unity plugin is going to be the best option for you, if you want to retain some customizability, but you mention that your Compiz settings in the Classic desktop didn't seem to save, yes? If this is the case, it's most likely that Compiz simply isn't running at startup in Classic, in favor of the fallback Metacity. Does compiz --replace bring back your settings in Classic?

---

### Post by Allavona on 2011-05-17
After playing around a bit with Compiz settings and such I was able to shrink the dock to a more reasonable level, change its opacity, same with the top panel. AWN for window management to let me know whats open, etc...And suddenly Unity doesn't seem like the headache thats its made out to be.

---

### Post by NexusN on 2011-05-17
> **Copper Bezel said:**
> I'm not really understanding the specifics of the problem, here. What exactly are you trying to do? 
 
It sounds like using the Classic desktop or at least disabling the Unity plugin is going to be the best option for you, if you want to retain some customizability, but you mention that your Compiz settings in the Classic desktop didn't seem to save, yes? If this is the case, it's most likely that Compiz simply isn't running at startup in Classic, in favor of the fallback Metacity. Does compiz --replace bring back your settings in Classic?
I am sorry for my poor presentation, English is not my mother tongue, I will try my best to tell what I faced and feel free to tell if you find it hard to understand.
 
When I was in ubuntu 10.10, I used to remove all the panels, using AWN as the docking, setting the mouse cursor theme to big red glass.
Addition to the appearance, I also set the mosue that, when touching the right edge of the screen, clicking the left click of the mouse, I can trigger the scale switcher that allows me to pick my desired working windows.(Just on the current workplace)
 
While having upgraded to 11.04, I can no longer do the same with the same computer.
At the beginning, I thought the Unity is the casue so I did try to switch to the Ubuntu Classic mode, but no luck.
 
After a fresh installation of ubuntu 11.04 without internet(no update during installtion), on first logging in to my system I find that the mouse theme can be changed.
I was glad to have it back, and I start to update the system via internet using the Update Manager, on finishing, I restarted my computer. Then the cursor theme is gone.
 
In compiz, I can still tune many things, like wobby windows, application switcher by keyboard........many things are working well.
By the way, though not important, I used to set the refresh rate to 60 and tick the box of vsync to make my windows move smoothly, but now I have to set it to 120.
I don't know why neither, but it is minor as I can get it work, still.
 
Now I just hope there can be a method so that I can restore the edge mouse clicking trigger function that I highly depend.
 
Thank you all for your kind consideration.

---

### Post by Copper Bezel on 2011-05-17
The left-edge bindings seem to conflict with the Unity plugin, but they should work in Classic, and the other edge bindings shouldn't be posing a problem at all. I'm not sure what's causing the problem, here, especially after a fresh reinstall and especially since you're certain Compiz is running. So edge bindings in Compiz just don't work at all?

As for replacing the panels with AWN, you can do that in the same way in the Classic desktop, or I think by simply disabling the Unity plugin in Unity.

---

### Post by NexusN on 2011-05-17
Thank you for your reply, 
actually I am now using the Ubuntu Classic mode(with effect),
and removed all the panels, disabled unity, installed AWN.
But the edge binding yet doesn't work, no matter scale switcher nor shift switcher,
while they can still be triggered by keyboard if I set so.
The cursor theme still stuck at default no matter what theme I have selected.
 
Are you talking about the ubuntu Classice (without effect) option?
I may try tonight as I am not near my computer.

---

### Post by huggis on 2011-05-17
I have some other broblems in 11.04 with unity:

1.Sometimes I can't click notification area icons. I have to click some on the right side and slide with mouse to those on the left to activate their options.
2.I have multiple keyring password prompts when systems logs in (autologin) and I don't know which program needs it. When I cancel all, everything starts correctly.
3.Animations where laggy until I've installed Equinox engine and applied some theme using it (now everything works smooth but sometime it seems that theme doesn't apply correctly after system start)

Anyone knows how to solve them?

---

### Post by Copper Bezel on 2011-05-17
No, the "No Effects" option uses Metacity instead of Compiz, and we need Compiz.

I wonder if the edge binding problem has to do with _[this bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/761616")_. Damn.

---

### Post by NexusN on 2011-05-17
> **Copper Bezel said:**
> No, the "No Effects" option uses Metacity instead of Compiz, and we need Compiz.

I wonder if the edge binding problem has to do with _[this bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/761616")_. Damn.

Thank you for your notification, finally I know I am not alone:KS

---

### Post by NexusN on 2011-05-17
And I just found that switching back to metacity(without effect) I can change the cursor them to what I want, 
and at the fresh install without internet my display card driver was not installed so I think that time I made it work as I was also in no effect mode, where compiz is not working.
That way, compiz should be the only cause, not the updates.

---

