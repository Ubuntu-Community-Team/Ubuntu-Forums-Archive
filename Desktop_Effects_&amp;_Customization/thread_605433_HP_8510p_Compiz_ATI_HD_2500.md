---
title: "HP 8510p Compiz ATI HD 2500"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by rivera82 on 2007-11-07
Ok this will be my first post 
I just got my HP 8510p with a ATI HD 2500 and i did not find anything that would help me get it up and running, i did how ever find several post that did help me achieve this since im a Linux n00b my self, so hopefully this can help some people that have this problem.
So here it goes.

I had a fresh install of ubuntu gusty and the first thing that i did was install "ENVY" you can get that [**[COLOR="Red"]here[/COLOR]**]("http://albertomilone.com/nvidia_scripts1.html") and here is the direct link to the .deb package[ **[COLOR="Red"]http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb[/COLOR]**]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb") once it is installed you can try the ATI automatic install but it gave me some errors so i did it with the manual installation of the ATI video driver version 8.42.3, install it and once it is finished you will need to reboot it, after that, you will nee to run ```
sudo apt-get install xserver-xgl
``` install and reboot or do the Ctrl+Alt+Backspace to restart ( the video session??) well you can try what ever you want. and that is it. you should now be able to run compiz with no problems.

Best of luck!!!

Alex

---

