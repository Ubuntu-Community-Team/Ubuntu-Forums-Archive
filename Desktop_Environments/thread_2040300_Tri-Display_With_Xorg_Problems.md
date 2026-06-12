---
title: "Tri-Display With Xorg Problems"
date: 2012-08-10
forum: Desktop Environments
---

### Post by ubun2d00d on 2012-08-10
Hi everyone, I have an Nvidia Geforce GT 620 with 2x DVI-i and 1x mini HDMI and I  want a tri-display, one monitor on each graphics output (although I am  having to use a DVI-I to VGA converter on one of the monitors as it has  no DVI input and a HDMI to DVI-D converter on the HDMI interface as none  of the monitors have HDMI inputs). I know that you cannot have more  than two monitors on twinview, so I  want one twinview made up of my 2x DVI-I interfaces and one seperate x  display on the mini HDMI interface. Now, the Nvidia control panel does  not allow you to setup this configuration (either everything is twinview  which kicks up an error because you cannot have three monitors on  twinview or everything has a seperate x display which is not what I want and I don't really want to use xinerama if possible). 

To get around this limitation I followed the brief instructions here: [http://askubuntu.com/questions/53971/separate-x-screen-twinview-on-nvidia-gt-440](http://askubuntu.com/questions/53971/separate-x-screen-twinview-on-nvidia-gt-440).  I think that this is the way to go and it has produced some positive  results. When I rebooted the machine after making the necessary changes  to xorg.conf the screen assigned as the separate x display was blank.  When I went into the Nvidia control panel I noticed that the offending display was disabled. I enabled it and set it to separate x screen and I  noticed, critically, that it retained the twinview setting on the other  two monitors, however, after a reboot there was no change for the  better. 

So, my question is: why is the separate x screen being disabled? Or am I barking completely up the wrong tree? I have attached the contents of my xorg.conf file in a file called xorg.txt.

Thanks in advance for all of your help.

---

