---
title: "Beryl = no video playback?"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by Fylk on 2007-04-29
Rather simple problem. Every time I load up beryl, I completely loose the ability to play back any type of video.

---

### Post by davidgarcin on 2007-04-29
having the same problem with the default installation of Compiz in Feisty Fawn.  It's rather annoying.

---

### Post by davidgarcin on 2007-04-29
seems like others are having the same problem, but I found a fix.  The video quality isn't great though.

[http://ubuntuforums.org/showpost.php?p=2434848&postcount=6](http://ubuntuforums.org/showpost.php?p=2434848&postcount=6)

Where he says change the output line, I had to change the "Plugin" under the "Default Output" section

---

### Post by Fylk on 2007-04-29
Thanks! That works great. I'm not getting any loss of video quality. 

What are your specs?

---

### Post by davidgarcin on 2007-04-30
Radeon X300 on a Thinkpad R52.

At fullscreen, the playback is somewhat pixelated and choppy.  There's a couple other people in the forums who seem to have the same problem with the loss of quality.  Oh well, it's better than nothing.

---

### Post by obbe on 2007-04-30
have you tried to install mplayer? i had the same problem ;)

---

### Post by davidgarcin on 2007-04-30
someone actually suggested that to me at school today, so I'm going to try it out later.  thanks.

---

### Post by SLIMwoogi on 2007-05-01
> **davidgarcin said:**
> seems like others are having the same problem, but I found a fix.  The video quality isn't great though.

[http://ubuntuforums.org/showpost.php?p=2434848&postcount=6](http://ubuntuforums.org/showpost.php?p=2434848&postcount=6)

Where he says change the output line, I had to change the "Plugin" under the "Default Output" section

Thank you so much.
I've spent horrible time to fix this problem. 
Thanks again. This way perfectly works.

---

### Post by tlayton_at_work on 2007-05-01
For those of you using KDE and Kaffeine, I too had this problem when I upgraded from the xorg-xserver-video-i810 to the new xorg-xserver-video-intel package.  I'm also using the trevino beryl svn debs.

Per comments in this thread about video output, I started Kaffeine, opened Settings -> xine Engine parameters, and selected the video icon.  I changed the driver to 'opengl' in the Beginner Options, hit apply, and ok.

Movies are playing fine now with no black screen.  The only thing I really noticed is that the movie window flashes a couple times at startup, but then is smooth after that.

Note: I also posted this in the Ubuntu Desktop Environments forums.

---

### Post by davidgarcin on 2007-05-01
yeah, MPlayer definitely solves the quality problem.  Thanks, obbe!

---

