---
title: "How to mold windows to match requirements"
date: 2011-08-24
forum: Desktop Environments
---

### Post by cyberjar09 on 2011-08-24
Hi all, 

I have a slightly peculiar request. I have an IPTV streaming MPEG2 video to Chrome browser but the stream is not very stable and I have to keep resetting the stream when it starts framing. I have looked into all the possible options as far as working with the Totem plugin is concerned and have found nothing that will keep working as desired. 

VLC media player on the other hand is excellent at playback of the stream but unfortunately I am not able to get the VLC plugin to playback in the browser. I have asked on the VLC forum too but was not able to find a workaround. 

I am now looking at a strange alternative and trust the flexibility of open source will allow me to achieve what I am trying to do. 

I wish to launch VLC with the stream running, but this instance of VLC must not have any of the application borders surrounding it (think: fullscreen). However, this instance of VLC also must also run only in a constrained resolution of the entire screen. 

Please see attached image. The red portion is the browser and the black portion is the VLC "fullscreen" instance. 

I have tried reading a little online but have not found anything of substance. Could I maybe achieve this using 
xdotool
wmctrl
any other tool you recommend?

Much appreciated.

---

### Post by aeiah on 2011-08-24
how does mplayer handle the stream? since mplayer doesnt have any gui controls, it might be easier to do what you want with it. you can launch it with a specific window size and position and no border, eg:

mplayer -noborder -geometry WxH+X+Y

---

### Post by cyberjar09 on 2011-08-24
> **aeiah said:**
> how does mplayer handle the stream? since mplayer doesnt have any gui controls, it might be easier to do what you want with it. you can launch it with a specific window size and position and no border, eg:

mplayer -noborder -geometry WxH+X+Y

mplayer also uses the same codecs as Totem (gstreamer/ffmpeg) if im not mistaken. The problem lies in the way the codecs are able to handle breakages in the IPTV signal and recover. Gstreamer and ffmpeg cannot recover from a signal interruption (various causes like foul weather ...) whereas VLC is almost seamless in recovery.

However I will try GNOME mplayer and report back with results. 
Thanks.!

---

### Post by cyberjar09 on 2011-08-25
Incredible, 

Thank you very much aeiah. The info you provided proved invaluable to me. 

This is why open source rocks! :guitar:

I have one last question though, how do I keep the mplayer window "always on top" whenever it is launched? 
Should I add another argument to the terminal command? 
or should I be using some other tool like wmctrl?

Thanks.

---

### Post by cyberjar09 on 2011-09-07
> **cyberjar09 said:**
> 

I have one last question though, how do I keep the mplayer window "always on top" whenever it is launched? 
Should I add another argument to the terminal command? 
or should I be using some other tool like wmctrl?

Thanks.

*bump*

---

### Post by aeiah on 2011-09-07
try mplayer's -ontop flag

---

### Post by cyberjar09 on 2011-09-07
> **aeiah said:**
> try mplayer's -ontop flag

perfect. Thanks a ton aeiah!

---

