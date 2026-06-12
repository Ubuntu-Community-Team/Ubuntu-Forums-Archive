---
title: "Acer Aspire one - disable the webcam"
date: 2008-12-17
forum: General Help
---

### Post by grandmaster on 2008-12-17
In my quest to lower the power usage of my aspire one I want to disable the webcam (unless needed)
Has anyone done this already and if so how did you manage it?

Whats the quickest way to start said camera again if needed.

TIA

Grandmaster.

---

### Post by bgerlich on 2008-12-17
Just unload the camera driver using "sudo modprobe -r driver_name", you can load it again with "sudo modprobe driver_name"

---

### Post by grandmaster on 2008-12-17
Thanks,

I'm off hunting for the driver name.

Thank you for your quick response!

---

### Post by Aearenda on 2008-12-17
Looks like uvcvideo on mine (using 8.04/Hardy). However, I'm not sure that unloading the driver actually turns the camera off electrically. It would be interesting to see what effect removing this driver has.

---

### Post by bgerlich on 2008-12-17
Unloading the module should cause the device to go into sleep state - if motherboard is built in such a way that allows this, I think.

---

### Post by Aearenda on 2008-12-17
Looks like unloading the driver reduces power usage by about 0.2W - measured using the Power History. It's a bit hard to be sure this way.

---

### Post by grandmaster on 2008-12-17
Thanks for your replies, not had chance to sort this yet as i'm being forced to work... apprently they won't pay me to mess with ubuntu all day... oh well

What sort of power are you lot getting (if you have an aspire one).
I suppose that any saving is going to be beneficial to prolong the battery..

Regards

GM

---

### Post by bgerlich on 2008-12-17
If you are really serious about reducing power usage you should check out [http://lesswatts.org](http://lesswatts.org). Install PowerTop and play around. There is a lot of advice on the web page on how to reduce wattage demand of your system.

---

### Post by grandmaster on 2008-12-17
I'll have a look over that site, thanks.
I have powertop running and one of the suggestions was that the camera was running 100% of the time.
I'm now showing between 9.5W - 10.1W on idle.

Next on the list is to remove non essential apps and drivers I think to try and improve boot time but thats later on when I get time to play, this work thing keeps getting in the way..

Regards

GM

---

### Post by Aearenda on 2008-12-17
Pity about the work :-) 

My 1Gb RAM/120Gb HDD AA1 runs at about 9.2W idle with the screen brightness turned down (but not blanked), wireless on, using Hardy and the Netbook Remix. If I turn the screen brightness all the way up, it goes up to 10.5W.

I use the concurrency=shell option for faster startup, but I haven't measured its effect - it 'feels' faster!

---

### Post by bgerlich on 2008-12-17
If you are looking to speed up your boot time - check this out. Asus EEE booting in **five** seconds.

[http://lwn.net/Articles/299483/](http://lwn.net/Articles/299483/)

---

