---
title: "Audio stopped working!"
date: 2006-01-30
forum: Desktop Environments
---

### Post by Niall Flinn on 2006-01-30
Hi folks,

I have a motherboard with an onboard NVidia CK804 sound device. This initially woked fine in Ubuntu 5.10, but I've installed several audio-related packages recently and now I'm not getting any sound through it. I know the card works because the bios has a voice sample gimmick on boot that works fine!

I've followed the steps here:

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

, but to no avail...

Any ideas?


Thanks,

Niall

---

### Post by mtron on 2006-01-30
more info please! 

what is your exact seeting right now, and what did you try. give us some basic info and we will try to help you for sure. 

cheers

---

### Post by Niall Flinn on 2006-01-30
OK, how do I find my audio settings?  - I'm a little unclear about how it all works on linux - there seem to be several different things all going on at once...

For example, do esd and alsa do the same thing? Do they both need to be running, or just one?

thanks,

Niall

---

### Post by mtron on 2006-01-31
there are basically 3 settings to take care of. (if you followed the tutorial you posted above) First open a terminal and type

"gstreamer-properties" and set both to alsa on the audio tab, next type "gnome-sound-properties" and disable the checkbox "enable sound server at startup" and check that your soundcard is the default one.

third type "gnome-volume-control" File - Change Device - (check the device where it says alsa mixer) and adjust the master and PCM volume 

Hope it works now.

---

### Post by Niall Flinn on 2006-02-01
Hmm, everything was already set as you specify, except "enable sound server at startup", so I checked that and restarted, but still nothing...

If I open the system monitor and look at the list of running processes, I'm not seeing anything obviously audio related... should there be an alsa daemon or something running?

Thanks again,

Niall

---

