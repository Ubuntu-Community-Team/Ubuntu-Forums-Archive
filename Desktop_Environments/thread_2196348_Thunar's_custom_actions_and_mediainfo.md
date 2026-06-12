---
title: "Thunar's custom actions and mediainfo"
date: 2013-12-29
forum: Desktop Environments
---

### Post by dannyboy79 on 2013-12-29
I often use mediainfo on video and audio files but I always do it from a terminal, isn't there a way to add this to Thunar's custom action list so that when i right click on my video file it will run mediainfo on that file and then show me the results in some window whether it be a terminal window or a zenity window? I've already tried the following which only shows the terminal for a moment and then it dissappears. 
```
xfce4-terminal -x mediainfo -i %f
```

Any help would be appreciated. and yes, mediainfo is installed in my path so i can run it from anywhere.

---

### Post by Elfy on 2013-12-29
works here with this, tested on flac, mp3 and avi

```
mediainfo -i %f | zenity --text-info
```

in the command box 

Make sure that Appearance Conditions are set in the appropriate custom action tab.

(Thanks for pushing me to work out something I didn't know - I started from the ubuntu community wiki - [https://help.ubuntu.com/community/ThunarCustomActions](https://help.ubuntu.com/community/ThunarCustomActions) )

---

### Post by dannyboy79 on 2013-12-29
AWESOME, it works. Thank you so much! I did look at the ubuntu wiki for thunar custom actions I just didn't know how to use the pipe and zenity.

---

### Post by Elfy on 2013-12-30
> **dannyboy79 said:**
> AWESOME, it works. Thank you so much! I did look at the ubuntu wiki for thunar custom actions I just didn't know how to use the pipe and zenity.

Neither did I, hence my thanks.

Glad you're happy :)

---

