---
title: "Live screencasting to ustream"
date: 2009-11-02
forum: Gaming &amp; Leisure
---

### Post by shanee753 on 2009-11-02
I was just wondering if it was possible. I was unsure of where to post this but due to screencasting being manly used for games I posted it here; Feel free to move this topic or ask me to.

I have heard you can screencast to a webcam live using a program called vloopback. I've installed this and still can't work out how to get this to work so I was hoping for some guidance from the Linux community. :P

Thanks.

---

### Post by shanee753 on 2009-11-05
Bump.

---

### Post by Vadi on 2009-11-05
You can use VLC for it, but in my experience I never figured it out fully / used too much CPU.

vlc screen:// :screen-fps=30 :screen-caching=100 --sout '#transcode{vcodec=mp4v,vb=4096,acodec=mpga,ab=256,scale=1,width=1440,height=900}:rtp{dst=192.168.1.2,port=1234,access=udp,mux=ts}'

Not sure what does ustream accept though, might need to do tinkering/change format.

---

### Post by MaindotC on 2009-11-06
You can use the full package called [WebcamStudio](http://www.ws4gl.org/).  There's an option to stream your desktop, a movie, music, irc, even a youtube video.

> **Vadi said:**
> 
vlc screen:// :screen-fps=30 :screen-caching=100 --sout '#transcode{vcodec=mp4v,vb=4096,acodec=mpga,ab=256,scale=1,width=1440,height=900}:rtp{dst=192.168.1.2,port=1234,access=udp,mux=ts}'

Not sure what does ustream accept though, might need to do tinkering/change format.

Thanks for this info! I watch hockey on atdhe.net and one time at the end of a broadcast I saw the user's desktop (sabres wallpaper :() and although he was using vista, he was using VLC to stream video from his NHL Gamecentre subscription on justin.tv and I wondered how to do it because now I have NHL Gamecentre and I'd like to share it with others.

I'd use WS4L but I'm using the 2.6.32 kernel, and according to the changelog there hasn't been support added for that kernel yet, so I'm going to try using VLC and see if ustream or livestream accepts its input.  Thanks!

---

### Post by shanee753 on 2009-11-07
I love you strAlan!
Seems to work perfectly. I've been looking for something like this for ages.
Thanks!

Sorry Vadi but I didn't end up trying your method. Wouldn't it only record and not stream live as a webcam though? anyway thanks.

---

