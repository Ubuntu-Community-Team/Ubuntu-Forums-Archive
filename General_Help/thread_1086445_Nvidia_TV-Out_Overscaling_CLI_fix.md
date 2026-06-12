---
title: "Nvidia TV-Out Overscaling CLI fix"
date: 2009-03-04
forum: General Help
---

### Post by JoshuaRL on 2009-03-04
First, some backstory:  a friend has an issue with connecting a Nvidia 9800GTX+ via DVI-to-HDMI cable to a 46" 1080p plasma TV as the monitor.  When connected that way, there is an overscaling problem.  According to [this thread here](http://ubuntuforums.org/showthread.php?t=906807) its a problem with Nvidia.  My friend has had this issue with XP also, which confirms that.  However, apparently Nvidia released a version of nvidia-settings for Windows that has an overscaling slider that allows you to fix that manually.  Not ideal, but workable.  From that other thread, it seems that an earlier version of nvidia-settings for Linux also had that slider.  But neither I nor my friend can find it there now.

So my question is this:  isn't it likely that nvidia-settings GUI was changing settings that can be done from the CLI?  If so, how would I best go about that?   So far, ```
nvidia-settings --query all
``` and ```
nvidia-settings --assign={DISPLAY}/{attribute name}[{display devices}]={value}
``` looks promising.  But to be honest, I'm in a little over my head.  So I'd appreciate any assistance I can get for ways to fix this.

---

