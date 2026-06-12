---
title: "Applying changes to Unity in CCSM"
date: 2012-05-18
forum: Desktop Environments
---

### Post by AnonymousJustified on 2012-05-18
So, I finally installed Ubuntu successfully. I like to think that I'm really good with Windows software, but Ubuntu Linux... I don't like it. I love it! Just, one problem. The task launcher on the left is too big, and it feels pretty forced when the whole thing pops up when you move the mouse over to it, so I figured I should save my precious horizontal space and shrink down the icons.

To do this, I had to install CCSM, and be pretty careful. I figured there was probably a reason it didn't come with Ubuntu, and these fears were confirmed by the message that popped up when I ran the program.

Somehow, I managed to carefully navigate to the Experimental tab, where I found the launcher icon size setting. So, I set it to the lowest it can, 32... and it didn't apply my changes.

How do I apply these changes? It's a simple straight answer thing, or, at least I hope it is.

Thank you in advance, should you desire to help me.

---

### Post by MG&amp;TL on 2012-05-18
...that's not good. I think you're probably running Unity2d without realising.

Can you open a terminal (find in dash, purple box thing) and paste what happens if you type:

```
echo $DESKTOP_SESSION
```

Good luck!

---

### Post by AnonymousJustified on 2012-05-18
I'm sadly typing this from a different system, so I cannot do that right now, but... isn't Unity2D faster?
I'll check when I'm back on to see if it's something else, but...

If it turns out that I'm using Unity2D, I think I'll stick with it. :/

---

### Post by mcduck on 2012-05-18
In theory Unity3D is faster, as the task of drawing the interface is moved to the GPU, which is fart more capable of that kind of things, and leaving your CPU free to do other work instead.

....nbut in reality that depends on how good your graphics card and it's drivers are. In worst case the drivers might end assigning some of the work to the CPU instead, in which case all the extra efffects would slow down your system.

Anyway, CCSM applies the settings immediatelly so you don't need to do anything there to save or apply the settings. However Unity itself only loads settings when you start it, so if you tweak the Unity-plugin's settings from CCSM you need to either log out and back again, or execute "unity --replace" to restart Unity.

---

### Post by AnonymousJustified on 2012-05-18
Ah, I guess that makes sense.

Also, it says that I'm running Ubuntu2D. Interestingly enough, I didn't really do anything to install it, but that's fine.

Is there any way I can apply CCSM's settings to Unity2D, or will I just have to settle if I want to use that?

---

### Post by MG&amp;TL on 2012-05-18
> **AnonymousJustified said:**
> Ah, I guess that makes sense.

Also, it says that I'm running Ubuntu2D. Interestingly enough, I didn't really do anything to install it, but that's fine.

Is there any way I can apply CCSM's settings to Unity2D, or will I just have to settle if I want to use that?

Unity2d (ubuntu 2d) is the fallback mode for those whose graphics capabilities aren't up to Unity. It's installed by default.

As for your second question, I believe there are tweaks available, I'm just not familiar with them. I'll have a google. Out of interest, what are your hardware specs? You may be suited to a different version of Ubuntu.

---

### Post by mc4man on 2012-05-18
There is a script to adjust launcher icon size in unity-2d, it's not perfect but works well. (You set the icon size when running script

With unity-2d likely being dropped in 12.10 it's probable that there will be no 'official' way to adjust.

For reference for anyone wishing or to help you use if desired - 
[http://ubuntuforums.org/showthread.php?t=1954637](http://ubuntuforums.org/showthread.php?t=1954637)

---

### Post by grahammechanical on 2012-05-18
Also if you are using 12.04 (you do not say what you are using) and you are in Ubuntu (Unity 3D) then you can adjust the launcher icon size from System Settings>Appearance and from the Behaviour tab you can adjust the behaviour of the Launcher in a limited way. You can set it to autohide or not.

So, to this extent we do not need to install Compiz Configuration Settings Manager (CCSM)

By the way, CCSM has never come with Ubuntu (to use your words). We have always had to install it to use its effects. CCSM is third party software. It is not controlled by Ubuntu.

Ubuntu 2D is installed by default. It is the fall-back mode. It could be that you need to install a proprietary video driver. do you have a video card that can run Unity 3D?

Run this code to find out.

```
/usr/lib/nux/unity_support_test --print
```

Regards.

---

### Post by goaliedude3919 on 2012-05-23
AJ, you seem to be having the same problem that I had. I don't know what   computer you're using, but the CPU in my laptop has a built in GPU that   messing things up and putting my session into Unity2D as opposed to   Unity3D. What I had to do was I had to disable that built in GPU.

The way to do that is through the BIOS. When you boot up your computer,  you should see somewhere either on the bottom of the screen or the top  right that tells you to hit usually either F2, F8, F10, or F12. Hit the  appropriate key and the BIOS should open. There should be an option for  Optimus. This is the built in GPU. Simply click on the option to disable  Optimus. There's actually even a description there that says Optimus  isn't meant for OS's other than Windows.

Hopefully this is what is causing your problem and you can now enjoy the full awesomeness of Ubuntu :)

---

