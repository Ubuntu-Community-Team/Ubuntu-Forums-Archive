---
title: "Duel screen desktop like Windows"
date: 2008-04-09
forum: Desktop Effects &amp; Customization
---

### Post by AndyParka on 2008-04-09
I recently re-started using Ubuntu but this time with 2 monitors. when you have 2 monitors in windows you have 1 desktop but 2 separate monitors which is the way i like my desktop. in Ubuntu I'm only able to have both monitors as 1 single resolution or 2 separate, non interactive desktops.

Is there a way to make both desktops as one but keep there seperate resolutions, and play full screen games on only one screen?

(Ubuntu 7.10 64bit, Nvidia GeForce 8600GTS)

---

### Post by AndyParka on 2008-04-10
is there anything i can do?

---

### Post by AndyParka on 2008-04-10
BUMP... if i cant pls just say so

---

### Post by Lantesh on 2008-04-10
Sorry I don't know the answer, but I thought I'd reply so you didn't feel the community was ignoring your question.  If nothing else this gives you another bump to the top.

---

### Post by Kiri on 2008-04-11
Yes you should be able to do that. 
1st make sure you are using the nvidia restricted drivers, then make sure you have nvidia-settings installed (search in synaptic). 
Then bring up nvidia settings by typing in the terminal
sudo nvidia-settings

setup twin view how you want with your monitors, then save to the xorg.conf file (back yours up first and make sure you know how to restore it)
Then restart X. 

There is also an apply button, but it doesnt work well for me

good luck

---

### Post by ChameleonDave on 2008-04-11
Games usually get confused when you try to convince them that you have one massive monitor.

Also, unless you intended to refer to the screens fighting it out with pistols, it is better to spell "dual" correctly, as it aids with searches.

---

### Post by mikef_542 on 2008-05-07
Thanks for this post and the answers it got me up and running with dual monitors.

One question to add: How do you set one monitor to landscape, or how do you tell the driver to rotate by 90 degrees?

Thank you
and this is my first post!

mike

---

