---
title: "no xorg.conf  file on 10.04"
date: 2010-11-27
forum: Desktop Environments
---

### Post by geoffree on 2010-11-27
I could not find the xorg.conf in the /etc/X11 directory.  I am running Ubuntu 10.04.  I have visuals, but cannot change or adjust resolution or moniter res.
?

Geoffree

---

### Post by I'mGeorge on 2010-11-27
have you installed any drivers for your video card yet ?

---

### Post by davec64 on 2010-11-27
Current versions of X.org don't use xorg.conf, but if you create one the settings will be used. :)

---

### Post by geoffree on 2010-11-27
Havent installed additional drivers since I began using Ubuntu. I have an onboard Intel Extreme Graphic card on an IBM desktop.  What drivers would I install? And wouldn't there need to be an xorg.conf file installed?  

Thanks,

Geoffree

---

### Post by geoffree on 2010-11-27
I have a Sony Trinitron 19" monitor. Problem is when I invoke the Monitor app, it has only two choices 600x800 and 1024x768. One monitor speed 60mHz.  Used to have many more choices.  Another Monitor app returns error message: "No monitor supporting DDC/CI".  I have framebuffer installed but don't know much about the technology.  Any suggestions given this situation?

---

### Post by I'mGeorge on 2010-11-28
> **geoffree said:**
> Havent installed additional drivers since I began using Ubuntu. I have an onboard Intel Extreme Graphic card on an IBM desktop.  What drivers would I install? And wouldn't there need to be an xorg.conf file installed?  

Thanks,

Geoffree

Have you've tried the drivers from their site [http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Desktop+graphics+controllers&ProductProduct=Intel%C2%AE+82845G+Graphics+Controller](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Desktop+graphics+controllers&ProductProduct=Intel%C2%AE+82845G+Graphics+Controller)

---

### Post by geoffree on 2010-11-29
I checked. Nothing for my chipset Intel Extreme Graphic card 82865G. Reference to having drivers in the distro.  So.  There was a selection in past versions of Ubuntu for Screen and Graphic tools, but they've cleverly bypassed that in the latest ver.
So what to do? The monitor has the capacity but I can't figure out how to employ it.
As noted in previous post, I get error message when trying to get to a monitor control that there is no DDC/CI thing.  Tracking that down takes me to reels of info but no enlightenment.
Thank you for your suggestions so far.  If anything occurs to you or to others it would be appreciated.

Geoffree

---

### Post by gogolink on 2010-11-30
I have a file called **monitors.xml** in myusername/.config (I'm running 10.10).
That file lists my monitors and their resolutions, and can be modified with text editor.

Don't know whether that's helpful.

---

### Post by ben_o_it on 2011-03-04
Thank you gogolink, the **myusername/.config/monitors.xml** file is the one.
I was looking for the config to make the vga plugged to my laptop be the main monitor and setting the <primary> tag to yes did the job.

---

