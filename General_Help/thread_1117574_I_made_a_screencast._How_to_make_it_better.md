---
title: "I made a screencast. How to make it better?"
date: 2009-04-06
forum: General Help
---

### Post by moma on 2009-04-06
Hello all,

I made three screencasts (howto videos) of my [Gscreendump...]("http://code.google.com/p/gscreendump/w/list") program. I used the "ffmpeg" program to capture the video. Added also a music to the videos.

The final result is in AVI-format because it was the smallest size format of all I tried (AVI/MPEG-4, OGV, QuickTime/MOV).

The videos are available here:
Screencast-1.avi: [http://gscreendump.googlecode.com/files/screencast-1.avi](http://gscreendump.googlecode.com/files/screencast-1.avi)
Screencast-2.avi: [http://gscreendump.googlecode.com/files/screencast-2.avi](http://gscreendump.googlecode.com/files/screencast-2.avi)
Screencast-3.avi: [http://gscreendump.googlecode.com/files/screencast-3.avi](http://gscreendump.googlecode.com/files/screencast-3.avi)

The funny thing is:
When I watch the avi-video in Totem/Ubuntu 8.10, it shows some errors and the video has *poor quality* (kind of color-shift or something).

But the same video plays just fine in Totem/Ubuntu 9.04beta.
---------

Could you take a look at the avi-videos (are they bad in your Ubuntu 8.10 too?)
What do I do wrong?

The commands to make the videos are:

a) Record the screencast
$ [COLOR="Green"]ffmpeg -r 30 -g 300 -s 1680x1050 -f x11grab -i :0.0 -vcodec qtrle screencast-1.mov[/COLOR]
I want to record the entire desktop. Its size (width x height ) is 1680x1050 pixels.

b) Convert .mov  to avi-format (here you can crop and re-scale the movie if you like. Eg. -vf scale=600:480).
$ [COLOR="Green"]mencoder screencast-1.mov -oac copy -ovc lavc -o screencast-1.avi[/COLOR]

c) Glue together video and sound. I got the music from [http://ogg.jamendo.com](http://ogg.jamendo.com) and [http://magnatune.org](http://magnatune.org) 
$ [COLOR="Green"]mencoder screencast-1.avi -o screencast-1-final.avi -ovc copy -oac mp3lame -audiofile some-free-music.mp3[/COLOR]

d) If you like, convert avi to free ogg/theora video (ogv) format.
$ [COLOR="Green"]ffmpeg2theora --sync  screencast-1-final.avi -o screencast-1-final.ogv[/COLOR]

You can adjust the audio and video quality with -a and -v options.
$ [COLOR="Green"]ffmpeg2theora --sync  screencast-1-final.avi -a 2 -v 5 -o screencast-1-final.ogv[/COLOR]
[COLOR="Red"]EDIT: [/COLOR] I had to add --sync option. Otherwise the ogv movie runs too quickly while audio is normal.
Note also that if the audio track is shorter than video then the video is cut to length of audio.
----

Yes, I've tried both Istanbul and (gtk-)recordMyDesktop, but no success.

Can you give me some advice on this issue?  How to make avi-video that plays on all operating systems in an adroit manner. How to make this right?
TIA!

---

### Post by andrew.46 on 2009-04-06
Hi,

Sorry I don't have advice just a question :-). Can I ask why you chose to output x11grab as follows:

```
-vcodec qtrle screencast-1.mov
```

A problem I encountered in a brief encounter with x11grab was deciding on a suitable output format and I am more than a little curious about your own choice.

Andrew

---

### Post by chriskin on 2009-04-06
i tried the first one and it plays fine. isn't it possible that your totem on 8.10 has a problem?

(by the way, i have the exact same appearance as you, transparent panels and dust mac theme)

edit : i might have some updated version of totem and/or codecs though, i've played with this computer a little too much

---

### Post by moma on 2009-04-06
Hello and many thanks for your answers.

> **andrew.46 said:**
> 
Can I ask why you chose to output x11grab as follows: -vcodec qtrle screencast-1.mov.
Well, I basically tried several video-codeces and qtrle (=quicktime movie format) was the codec that produced the best result.

For example I tried:
$ [COLOR="Green"]ffmpeg -r 5 -g 300 -s 1680x1050  -vcodec mpeg4 test1.avi[/COLOR]

$ [COLOR="Green"]ffmpeg -r 2 -g 300 -s 1680x1050 -f x11grab -i :0.0 -vcodec mpeg4 test2.avi[/COLOR]

But the resulting video quality was rather bad.

> **chriskin said:**
> Isn't it possible that your totem on 8.10 has a problem?
Very good news chriskin!
I was afraid for having to record both videos again and again. Good to hear that playback worked on your Ubuntu 8.10.  In my case the video performed poorly on both 32 and 64bits Ubuntu 8.10. I will now upgrade these OSes and try again.

I've practically already moved to Ubuntu 9.04 weeks ago.

---

### Post by batharoy on 2009-04-06
Can confirm they play perfectly fine in Totem and VLC on my system.

---

### Post by moma on 2009-04-06
Very good.

BTW: Here is one frame of the video as shown by Totem in my Ubuntu 8.10 (32bits). 
[[img]http://bildr.no/thumb/383675.jpeg[/img]](http://bildr.no/view/383675)
Bad colors. It may have to do with Nvidia graphic driver (old version).
The apt-get update && apt-get upgrade did not help.

The konclusion is: if the video has bad colors then it's time to upgrade/new-install to Ubuntu 9.04beta ;-) See [http://www.futuredesktop.org](http://www.futuredesktop.org)

---

