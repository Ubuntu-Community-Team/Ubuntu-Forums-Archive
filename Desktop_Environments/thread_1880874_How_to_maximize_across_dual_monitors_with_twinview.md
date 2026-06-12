---
title: "How to maximize across dual monitors with twinview in Ubuntu 11.04"
date: 2011-11-14
forum: Desktop Environments
---

### Post by aanchilto on 2011-11-14
Hi,

I am unable to find any posts out there to solve my problem.

My system:
Ubuntu 11.04
Dual monitors, one GPU: GeForce GTX 570

Problem:
I have setup twinview to have extended desktop across two monitors. It works fine with Unity and the NVidia drivers. I am using this machine to run a HMD for which _I need to have any maximized windows spread across both the monitors_, but _presently whenever I maximize a window, it does so in the same monitor it was in, be it the first or the second_.
I have attached my present xorg.conf file as a text file if you want to have a look. 

Could anyone please help me solve this problem or direct me to the right place to post this query?

Regards.

---

### Post by boast on 2011-11-14
enable xinerama as well in nvidia-settings (you won't have compositing anymore either i believe).

---

### Post by aanchilto on 2011-11-14
I have tried Xinerama already .. it breaks everything -> I had to disconnect the second monitor to get back something and then logged back in, disabled the Xinerama to fix the problem. I have removed the options I changed before from the xorg.conf file so you won't find them there .. but I have tested several times with Xinerama - it just doesn't work!

---

### Post by boast on 2011-11-14
I think xinerama is the only thing that exists to make two screens appear as one. Might want to figure out whats the issue you have with xinerama.

---

### Post by aanchilto on 2011-11-14
Alright I will get you more on what exactly were the problems when I switched xinerama on, next time I am in the lab. 
But just to let you know, I could also get the two screens appear as one using "twinview". With this everything is working fine, except for that maximizing a window spans only one monitor instead of two.

---

### Post by ezacharyk on 2011-11-14
> **aanchilto said:**
> Alright I will get you more on what exactly were the problems when I switched xinerama on, next time I am in the lab. 
But just to let you know, I could also get the two screens appear as one using "twinview". With this everything is working fine, except for that maximizing a window spans only one monitor instead of two.

If your problems with Xinerama are anything like mine, you would have logged in and had nothing on the screen except your desktop background. No keyboard commands would work and no menu options appeared.

The way I fixed my computer was to login in safe mode and manually edit the xorg file to set Xinerama to 0.

---

### Post by aanchilto on 2011-12-16
> **ezacharyk said:**
> If your problems with Xinerama are anything like mine, you would have logged in and had nothing on the screen except your desktop background. No keyboard commands would work and no menu options appeared.

The way I fixed my computer was to login in safe mode and manually edit the xorg file to set Xinerama to 0.

-I had exactly the same problem with Xinerema as you have described here - when I logged in, I had nothing except a blank background and nothing working!
I ssh'ed into the machine, changed the XORG.conf to make Xinerema 0 and then restarted X then it worked fine.

But the problem I started this thread wasn't the Xinerema thing.

Problem:
I have setup twinview to have extended desktop across two monitors. It  works fine with Unity and the NVidia drivers. I am using this machine to  run a HMD for which _I need to have any maximized windows spread across both the monitors_, but _presently whenever I maximize a window, it does so in the same monitor it was in, be it the first or the second_.

+ Xinerema doesn't help anything with this problem.

Any idea anyone?

---

### Post by thaelim on 2011-12-16
If you are running Unity, have you tried looking in compizconfig-settings-manager to see if there is a setting in there related to this? Maximising is controlled by the window manager.

---

### Post by aanchilto on 2012-01-07
Thank you for your input. I have installed the  compizconfig-settings-manager, but couldn't find the exact place in the  window manager section where I could change the setting for controlling  the maximizing of windows. 
Could you please guide me a little more?

---

### Post by tbone3421 on 2012-04-29
I'm basically trying to do the same thing right now.  Did you ever find a satisfactory solution?  If not, I am looking into Fake Xinerama right now, which looks promising so far.

---

### Post by aanchilto on 2012-04-29
I am probably just using twinview for now, and I was able to maximize the two threads for stereo rendering in the HMD using some configuration setting in the volume rendering software that I am using. So I am good for now.
But I will also try fake xinerama. Thanks for letting me know!

---

### Post by sreeakshay on 2012-05-17
Were you able to resolve this? I am in same situation but with both maximize and "xterm fullscreen".

---

### Post by aanchilto on 2012-05-17
> **sreeakshay said:**
> Were you able to resolve this? I am in same situation but with both maximize and "xterm fullscreen".

No I haven't looked into resolving this, as I have bypassed this problem with some other settings. Please see my last answer to know more about this.

I'll post here if I ever solve this. Also, I would request you to post a resolution here for the community if you happen to solve this.

Thanks.

---

