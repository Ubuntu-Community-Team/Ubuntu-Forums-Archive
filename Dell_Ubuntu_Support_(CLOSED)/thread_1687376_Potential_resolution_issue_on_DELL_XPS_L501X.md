---
title: "Potential resolution issue on DELL XPS L501X"
date: 2011-02-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by benavidz on 2011-02-13
Hello everyone, 

I'm interested in installing Ubuntu 10.10 on my recently acquired DELL XPS L501X, but I'm worried about a potential resolution issue. When I boot to the live CD, the maximum resolution I can display is 800 x 600. The native resolution of my monitor is 1920 x 1080, so needless to say I would be disappointed if this were the highest resolution I could attain. 

I have installed Ubuntu before on two other laptops, and each of those times the live CD was able to display the native resolution of that particular laptop. I'm curious as to whether anyone else has had this issue, and if so, whether it was resolved simply by installing the operating system natively, or if the proprietary nVidia drivers needed to be installed, or perhaps if this was simply unsolvable.

I've searched the forums and the internet as a whole to the best of my ability, but I haven't found anyone else with a similar issue. I apologize in advance if this is a duplicate post, and appreciate any help that any of you are able to provide. Thank you.

---

### Post by sam1948 on 2011-02-13
try this:
```
sudo apt-get install arandr
```

[COLOR="Blue"]_[more details here]("http://www.liberiangeek.net/2010/12/change-screen-resolutions-ubuntu-10-10-maverick-meerkat-arandr/") _[/COLOR]

---

### Post by benavidz on 2011-02-13
Thank you for the quick reply, this looks like exactly what I need. I'll go ahead with the install this afternoon and let you know how it turns out.

---

### Post by svast on 2011-02-14
This does not work as expected with me. 
My DELL XPS L501X native resolution is 1366x768, which I can reach with no problem.
The issue is when connecting external monitor on display-port: arandr does not show the native resolution of the external display (1920x1080 or 1280x1024, tested with several monitors), it only shows up the resolutions of the "integrated screen" (sorry for my poor english).
Maybe this is a problem of monitor detection... I really don't know, and very disappointed because I cannot connect it to my TV that way (forced to get back to M$, damn!)

---

### Post by sam1948 on 2011-02-14
> **svast said:**
> This does not work as expected with me. 
My DELL XPS L501X native resolution is 1366x768, which I can reach with no problem.
The issue is when connecting external monitor on display-port: arandr does not show the native resolution of the external display (1920x1080 or 1280x1024, tested with several monitors), it only shows up the resolutions of the "integrated screen" (sorry for my poor english).
Maybe this is a problem of monitor detection... I really don't know, and very disappointed because I cannot connect it to my TV that way (forced to get back to M$, damn!)

i can't help any more because i m with nvidia and its different
but have u been looking in the system->preferances->minitor(display in old versions)
there should be options for each monitor in there.

---

### Post by svast on 2011-02-15
@sam1948: thank you, but the options are the same that way.

---

