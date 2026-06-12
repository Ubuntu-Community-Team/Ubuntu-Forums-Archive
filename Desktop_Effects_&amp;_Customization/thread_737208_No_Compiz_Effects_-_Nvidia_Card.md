---
title: "No Compiz Effects - Nvidia Card"
date: 2008-03-27
forum: Desktop Effects &amp; Customization
---

### Post by Chris From California on 2008-03-27
I have finally been able to boot into Kubuntu thanks to the sudo dpkg-reconfigure xserver-xorg command. 


However I still have no effects? :confused:

I went to settings>Advanced Desktop Effects Settings and they seem to be turned on just not working. Any Ideas???

Also there is a NVIDIA X Server Settings program, but when I run it, it tells me "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." 

and if I actually do that I can't get back into the GUI without going through the "sudo dpkg-reconfigure xserver-xorg" command. and restarting the computer. 

Please Help!!!! :(  Thanks in Advanced!!!!!

---

### Post by adityakavoor on 2008-03-27
Have you tried [envy]("http://www.albertomilone.com/nvidia_scripts1.html") ?

---

### Post by Chris From California on 2008-03-28
I downloaded it but I coudnt get it to load. Anyway some can lead me step by step? I'm pretty new to the linux world. Thanks for the responce!!!

---

### Post by Ub1476 on 2008-03-28
First, make sure you haven't installed any drivers from Restricted Driver Manager (should be available from Control Center>Advanced Mode, I think). 

Then, to run Envy:

```
envy -g
```

If this fails try:

```
envy -t
```

---

### Post by Chris From California on 2008-03-28
Cool it works thanks!!!!!!!!!!!!!!!! Makes Vista look like 3.1 hu? 

I have some more questions I hope you don't mind :D

First how does one get the menu bar at the bottom of the screen, and transparent look on the Konsol like in this picture 

[http://farm1.static.flickr.com/156/405394003_15b04e2c2e_o.png](http://farm1.static.flickr.com/156/405394003_15b04e2c2e_o.png)



Thanks So Much! Things are really coming along :guitar:

---

