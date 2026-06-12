---
title: "WoW+vent"
date: 2007-01-28
forum: Gaming &amp; Leisure
---

### Post by noenter1 on 2007-01-28
Im having alott of trouble with getting sound comming from WoW and Ventrilo at the same time. i followed this giude here: [http://www.ubuntuforums.org/showthread.php?t=254286&highlight=wow+vent](http://www.ubuntuforums.org/showthread.php?t=254286&highlight=wow+vent)
and here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
Can someone help me please?

---

### Post by noenter1 on 2007-01-30
Not only WoW and Ventrilo, but ANY 2 programs that have sound that are running for that matter. I have a AMD mother board(M2N32sli-deluxe) with integrated sound card(HD 8 channel).

---

### Post by K.Mandla on 2007-01-30
(I'm going to shift this to Gaming, where it will likely get better responses. ;) )

---

### Post by Ferrat on 2007-01-30
I've never had a problem running WoW and Vent ect. at the same time but I know some ppl use alsa-oss so try and install that then before wine in the launch you just add aoss I think not 100% but if you seach for it you will find it here on the forums.

---

### Post by noenter1 on 2007-01-30
I have already done this and it still wont work :(

---

### Post by noenter1 on 2007-01-30
Ok when I goto the audio tab in winecfg i get this: winecfg
```
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

```
would this be the reason/how do i fix this? Also winecfg seems to freeze for about 30sec after I goto the audio tab.

---

### Post by Mongoose on 2007-01-30
No, that just means you don't have jack for lib32.  What you should do is open winecfg and go to the audio tab and setup alsa.   You might want to update your asound32 also.

---

### Post by noenter1 on 2007-01-31
Ventrilo freezes when i set the driver to alsa.

EDIT: i forgot to set it for emulation. Working but sound is a bit messed up.

---

