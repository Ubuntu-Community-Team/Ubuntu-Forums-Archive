---
title: "Youtube - No Sound"
date: 2009-02-03
forum: General Help
---

### Post by michael91 on 2009-02-03
Currently, I'm running Ubuntu 8.10, and have installed Flash, so when I watch videos on YouTube, there's video. For some reason, however, there's no sound. Why would this be so? I've watched DVDs and listened to music on this computer, and they've had sound.

---

### Post by cyclobs on 2009-02-03
try going into "system > pref.... > sound"

and setting all of the settings to ALSA or something.

i "think" this solved the same problem i had. tho don't count on it :)

---

### Post by michael91 on 2009-02-03
Nah, didn't work. Thanks for the effort, though.

---

### Post by cyclobs on 2009-02-03
alright, probably has somethign to do with the plugins then. i remember it took a bit to get flash working properly the first time for me

---

### Post by michael91 on 2009-02-03
I did have a problem with Flash where I actually had to reinstall it to get it working. And, I just clicked Test on the Sound Options, and this:

"gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource."

or this:

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource."

comes up. Do you know what it means?

---

### Post by cyclobs on 2009-02-03
yup.... that something is broken >.<


try all of the sound settings till you find one that works best. thats what i did

---

### Post by michael91 on 2009-02-03
Would I need to keep reloading the video when changing the settings?

---

### Post by cyclobs on 2009-02-03
you'll have to restart firefox for the new settings to take effect. but using the test button in the sounds menu should work if you find a sound system that works

---

### Post by linux_tech on 2009-02-03
Try installing alsa-oss, then either reload alsa or reboot
```

sudo apt-get update

sudo apt-get install alsa-oss


```

---

