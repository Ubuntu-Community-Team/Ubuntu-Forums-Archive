---
title: "xandr &amp; lxandr error indications (post moved from flaggmann2 UID)"
date: 2014-03-10
forum: Desktop Environments
---

### Post by Flaggmann on 2014-03-10
In attempting to change screen resolutions I get the following error:

XRandR failed:
XRandR returned error code 1: xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed


xrandr appears to accept the change and shows so in it's miniscreen but when "apply" is checked it generates this error. Prior to this the login splashscreen was reduced in size with two vertical black bars, one on each side; once logged in selecting xrandr would adjust it to the correct size. lately that functionality has been lost.

Intel adapter with samsung monitor AMD

where do I find file that provides size of gamma for output and how can I regenerate it?

I have uninstalled/purged X and reinstalled to no avail.

when I connect using xvnc server resolution appears correct problem occurs on main tty login monitor

would also appreciate a tip on setting a custom layout as default thnx

Thanks in advance

---

### Post by Flaggmann on 2014-03-12
107 views and no replies?? hmm I am I missing something obvious or is this Xserver , xrandr, lxrandr so compicated that only those educated at engineering levels can answer t and don't need to access forums?

---

### Post by matt_symes on 2014-03-13
Hi

I'm rather confused. Are you setting the resolution from the terminal or are you using the GUI ?

Have you tried setting it from the terminal as a test ? 

You know about the ```
--gamma  red:green:blue
``` switch you can pass to the xrandr command ?

What resolution are you trying to set ?

There may be a work around if the correct resolution is not being discovered for you.

Kind regards

---

### Post by Flaggmann on 2014-03-13
I am using the gui as I have since I installed ubuntu; it always worked previously. The original login screen would be reduced in width but once I logged in xrandr allowed me to change to 1440x900. then all was well with the world. Some thing has occurred in one of the latest updates it appears as xrandr no longer succeeds.

xrandr opens and allows me to select the 1440x900 or a previously saved successful file but as soon as I 'apply' the selection I get the error related to gamma data.

when I use x11vnc defaults or using the --geometry switch the remote screen is fine; but again it has to be set each time.

I have never been able to adjust the default start so that using xrandr is not needed.

Some posts have indicated the latest changes are rendering the config file obsolete yet there is precious little info available on that.

---

### Post by matt_symes on 2014-03-13
Hi
> 
Some posts have indicated the latest changes are rendering the config  file obsolete yet there is precious little info available on that.

If you're talking about the xorg.conf file, that has been deprecated for a long time and is no longer used.

KMS (kernel mode setting) is now used to set the resolution of the display and, as far as i am aware, uses the EDID information from the monitor to get the resolutions.

Let's see where you are though.

Open a terminal and type

```
xrandr
```

Copy and paste the output from the terminal into your next post.

I'm almost off for the day though so it may be tomorrow we look at this.

Kind regards

---

### Post by Flaggmann on 2014-03-18
using nvidia console now but still has a problem as it appears to use the EDID as you say, however I originally set up to tv's via hdmi/DVI inputs to set it up for 1920 x 1080 and it worked, I simply unplugged the second hdmi cable and plugged it into an LG monitor and it worked at 1920x1080 normally. when rebooted it appears to have reread the hardware and changed the LG's resolution to a smaller screen instead of just picking up the last good saved config data from nvidia.

---

