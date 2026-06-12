---
title: "Daily software update results in unusably slow display response"
date: 2014-06-26
forum: Desktop Environments
---

### Post by brucew on 2014-06-26
This morning's daily software center updates have all but killed my system. (Thursday June 26, 2014)

I run a plain vanilla 14.04 LTS, which was installed fresh to formatted partitions from a DVD back in April.  Dual core AMD 64, ATI graphics, dual monitors in big desktop mode.

This morning after the required reboot, windows take seconds, verging upon minutes to open.  Forget even trying to move the mouse pointer across from one monitor to the other.

System monitor reports that sitting idle with no applications open, CPU load alternates between 75% and 95% per core.  The primary procecss culprit seems to be compiz, which, again at idle, floats between 60% and 70%, followed by init at 15-18% and system monitor itself at 10-13%.  This leaves very little CPU for things I want to do. :(  

Wading through the glue of the pokey system, I finally stumbled upon this: [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager) 

I've only ever dabbled beyond clueless user mode, but at the bottom I did recognize metacity, and gleaned that I could temporarily replace compiz with it using metacity --replace.  I was able to install metacity and execute the command.  This restored snappy window response, which confirms for me that the updates caused an issue with compiz, whatever that issue may be.

Trouble is, I've lost the launcher and whatever the bar is called across the top.  I'm going to have to simply power off to shut down.  But wow, is the display response snappy!

How can I fix my fix?  

Please remember, I'm fairly clueless.  Can you guide me with baby steps and monosyllables?

EDIT:  For the record, I have no interest in fancy 3D stuff or eye-candy effects.  I just want plain vanilla.

---

### Post by grahammechanical on 2014-06-27
If you are using Ubuntu 14.04 why did you follow a tutorial that stops at Ubuntu 12.04? You risk doing something that will cause other problems. And it has.

The problem might have been caused by a kernel update that was incompatible with the proprietary video driver and you may be running on an open source video driver that is being used as a fall back mode.

Open About this Computer. The Details page will tell you what graphic driver is being used. You can also go to the rest of System Settings>Software and Updates>Additional Driver tab and experiment with another driver.

If we have received a newer version of the kernel and it is causing problems like this, then at the Grub menu under Advanced Options for Ubuntu we can load into an earlier kernel. As regards Metacity, you need more than a Window Manager you need a user interface for it.

In my opinion, on 14.04 it is better to install gnome-session-flashback. It is in the software Centre (search for Gnome Session Manager). It will give two additional login screen options.  Gnome Flashback (Compiz) and Gnome Flashback (Metacity).

It does not use the Unity user interface but a different one that resembles the old gnome Panel UI but it does mean that we have an alternative UI to log into should Compiz become broken in some way.  We get Metacity with a user interface.

```
sudo apt-get install gnome-session-flashback
```

Regards.

---

