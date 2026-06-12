---
title: "How to turn off or disable touchpad tap"
date: 2008-09-04
forum: Desktop Environments
---

### Post by cnymike on 2008-09-04
My HP pavilion XH136 has a touchpad and the tap behavior is driving me crazy. I'm always accidentally opening apps, windows, making choices that I don't want to make because the tap feature is so sensitive. I jsut want to turn off the tap feature completely. But I don't see anyway to do that. THe mouse control panel doesn't let me turn off the tap and there does not seem to be any touchpad specific control panel. Help.

---

### Post by sayakb on 2008-09-04
Install **gsynaptics** and disable tapping using the Touch Pad Settings (gsynaptics)

---

### Post by cnymike on 2008-09-04
I installed gsynaptics and then when I went to the mouse control panel I got an error that it GSynaptics could not not initialize. That I have to set SHMCongif in xorg.conf to true or XF86Config to use GSynaptics.

I opened xorg.conf and did not see any SHMConfig.

I'm stuck.

---

### Post by Calmatory on 2008-09-05
I am having the exact same problem, except that I don't really need that software, as I was able to disable the double tap from **System->Preferences->Mouse->Touchpad**.

---

### Post by CJ56 on 2008-09-05
Have you tried going into your xorg.conf, going to the Section "InputDevice", and changing the "MaxTapTime" and "MaxTapMove" values to "0" then saving (and possibly restarting)?

It worked for me on an old Dell Inspiron...

---

### Post by mali2297 on 2008-09-05
> **cnymike said:**
> I installed gsynaptics and then when I went to the mouse control panel I got an error that it GSynaptics could not not initialize. That I have to set SHMCongif in xorg.conf to true or XF86Config to use GSynaptics.

I opened xorg.conf and did not see any SHMConfig.

I'm stuck.

You need to add a line to the appropriate input device section. Here is the relevant section in my xorg.conf:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        **Option          "SHMConfig"             "on"**
EndSection

```

---

### Post by Calmatory on 2008-09-05
What if there is no such option as **"SHMConfig"**?

---

### Post by mali2297 on 2008-09-05
> **Calmatory said:**
> What if there is no such option as **"SHMConfig"**?

You have to *add* the line in bold.

...or do you mean that you get an error if you do so?

---

### Post by markaron on 2008-09-05
try to tap that button at the middle of that touchpad that disables it. 

[laptop security]("http://www.inspice.com") , [laptop tracking]("http://www.inspice.com/en/Trace.htm") , [regulatory compliance]("http://www.inspice.com/en/Trace_Regulatory_Compliance.htm") , [data security]("http://www.inspice.com/en/trace_how_it_works.htm") , [security software]("http://www.inspice.com/en/SmartProtec.htm")

---

### Post by wladicus on 2008-09-12
> **mali2297 said:**
> You have to *add* the line in bold.

Hi mali,
Perhaps I can get some help here as well.  I have the same problem in Kubuntu.  I have tried everything mentioned in this thread and in several other threads on this very topic.  Nothing appears to be working for my particular situation.  I have a MDG VisionBook with 3GB of RAM.  The touchpad is a Logitech NOT a Synaptics, so I do not understand how that Synaptics code even got into my xorg.conf file unless this is generic stuff that is supposed to work on any make of touchpad.   Under System Settings, when I go to the Keyboard and Mouse then select Mouse, there is no indication of a touchpad or touchpad settings anywhere.  The Kubuntu development team sure seem to have missed on this very simple 'MUST HAVE' in any system. Makes for a very unhappy Linux experience.  No such problems in my Windows Vista OS running on the same machine.  
It looks like Kubuntu actually thinks my touchpad is a mouse, but why then is there code at all for a Synaptics Touchpad in my xorg.conf file.
Can someone explain this, so that people like myself can understand what is going on here?
Anyway, I have put this challenge out into the Linux World and no one has dared to take it up seriously.  I have tried the many, many suggestions provided thus far (they are all very similar, around the Synaptics Touchpad business and changing settings in the xorg.conf file and synclient and syndaemon etc..., but none of this has worked on this laptop).  If Windows can do it, why can't Linux? :)
walt :KS

---

### Post by wladicus on 2008-09-12
> **LinuxIsInnovation said:**
> Install **gsynaptics** and disable tapping using the Touch Pad Settings (gsynaptics)
I do have gsynaptics installed and when I click on it to run it I get the following message:
> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

That message is quite strange because I added "SHMConfig"  "true" to the xorg.conf file many 'boots' ago and the problem is still not solved. Many people on many forums have been unable to help with this problem.  I actually want to turn the touchpad off completely because it is a nuisance when typing, but nothing seems to work.  I am running Kubuntu 8.04 LTS (Hardy Heron) in a Wubi configuration. Are there any new suggestions?  Thank you for your time.
walt

---

### Post by mali2297 on 2008-09-13
> **wladicus said:**
> Are there any new suggestions?

Have you tried [this tip](http://ubuntuforums.org/showpost.php?p=5694509&postcount=13)?

---

### Post by speedwell68 on 2008-09-13
Touchpads are the devils work.  Why not just turn the silly thing off all together and get a mouse.

---

### Post by wladicus on 2008-09-15
> **mali2297 said:**
> Have you tried [this tip](http://ubuntuforums.org/showpost.php?p=5694509&postcount=13)?
[COLOR="Red"]***THANKS A MILLION***[/COLOR] mali2297.:KS I am typing this note with the touchpad disabled and its WONDERFUL! I am glad you found this and especially grateful that you passed it on to me.

I managed to work out a detailed HOW TO for setting up **a shortcut key version of this** can be found in the last post at the following link:
>    [http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html](http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html)  

Thank you again, :):)
walt :)

---

### Post by gmbrammer on 2008-10-01
I put this little script (called "tp") on the launch bar ("tp 0") at the top of my gnome screen to toggle the touchpad on/off:

#!/bin/bash

# Touchpad Switch
# It requires SHMConfig enabled as described in [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

TpadStatus=`synclient -l | awk '/TouchpadOff/ { print $3 }'` #0 means On, 1 means Off
if [ "$TpadStatus" -eq "0" ] 
then
  synclient TouchpadOff=1
  echo "Touchpad now disabled"
else 
  synclient TouchpadOff=0
  echo "Touchpad now enabled"
fi

---

### Post by kybKenny on 2008-12-09
Apparently, in Intrepid Ibex our xorg.conf isn't used that much anymore.

I got Gsynaptics to work by doing as suggested here:
[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig")
which is using hal rather than xorg.conf.

That didn't help me with my quest for two-finger tapping, but maybe it helps you (or anybody who walks by)...

Greetings,
kybKenny

---

### Post by persev on 2008-12-15
> **Calmatory said:**
> I am having the exact same problem, except that I don't really need that software, as I was able to disable the double tap from **System->Preferences->Mouse->Touchpad**.

Thanks, nice one.

---

### Post by Tiger770 on 2009-05-04
> **cnymike said:**
> I installed gsynaptics and then when I went to the mouse control panel I got an error that it GSynaptics could not not initialize. That I have to set SHMCongif in xorg.conf to true or XF86Config to use GSynaptics.

I opened xorg.conf and did not see any SHMConfig.

I'm stuck.

I had this problem....rebooted and it's working fine.  :-D

---

