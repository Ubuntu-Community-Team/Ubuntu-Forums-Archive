---
title: "Twinview Compiz wont enable: 7.10"
date: 2008-03-24
forum: Desktop Effects &amp; Customization
---

### Post by sclewis12 on 2008-03-24
I have 2 samsung 17's on ubuntu 7.10. I have an nvidia 7800gt with the latest drivers installed.

The twinview I got to work fine. At first the primary panel had the pan issue as described. I solved this by using the default display config rather than having it set to the samsung model in the data base.

The second issue is that compiz works fine when twinview is disabled. Then when I enable it. Compiz stops running and will not allow it's self to be turned back on. Any clues on how to have both enabled?

third
I can't use the nvidia console to write to x and make changes, because I believe that the Ubuntu screens and graphics applet takes authority over x. This is fine as long as I can get the screens to display.

My last question is pretty noobish, but i am fairly new to linux. When you look in the folder and see xorgconfig files named 1-6. Is the current one the one that would be considered 0? As in the one without a number given.?
__________________

---

### Post by IsawSp4rks on 2008-03-24
Make sure you're not using Xinerama3D (Nvidia's Xinerama feature) as it's incompatible with Compiz.  Either use your monitors as two independent displays (though this has some issues with Compiz at times, such Window Decoration disappearing) or one wide desktop without Xinerama3D.

Hope that helps.

---

### Post by sclewis12 on 2008-03-24
> **IsawSp4rks said:**
> Make sure you're not using Xinerama3D (Nvidia's Xinerama feature) as it's incompatible with Compiz.  Either use your monitors as two independent displays (though this has some issues with Compiz at times, such Window Decoration disappearing) or one wide desktop without Xinerama3D.

Hope that helps.

So it is safe to say that if I look into my xconfig I should see something about xinerama 3d. And I should set it to disabled.
can you tell me if the x config would be the the one without a number lable?

---

### Post by IsawSp4rks on 2008-03-24
The simplest way is to install 'nvidia-settings' via Synaptic

Then open a terminal and type

**sudo nvidia-settings**

follow the instructions in this thread

[http://ubuntuforums.org/showthread.php?t=551784](http://ubuntuforums.org/showthread.php?t=551784)

That should fix it for you.

---

