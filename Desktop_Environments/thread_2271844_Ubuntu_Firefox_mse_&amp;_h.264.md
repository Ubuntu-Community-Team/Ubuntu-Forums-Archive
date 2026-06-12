---
title: "Ubuntu Firefox mse &amp; h.264"
date: 2015-04-02
forum: Desktop Environments
---

### Post by Swiftjay on 2015-04-02
It's great now that mse is enabled on firefox, I'm quite happy about this, it's definitely a big up for Firefox.  However, I'm wondering if mse & h.264 can be enabled?  I've been searching around the web and I've seen posts about installing the gstreamer1.0 packages to make this happen but from doing this nothing has changed and I still can't have mse & h.264 in blue (without telling firefox to ignore it anyway).  Am I missing something to make it play?

---

### Post by TheFu on 2015-04-02
This probably won't help you, but I followed some gstreamer instructions to get h.264 support added to firefox and it "just worked" here.  If there had been any issue, I would remember more about it, but I don't.

Plugins:
* openh264 from Cicso
* VLC Web plugin
* mplayerplug-in

---

### Post by Swiftjay on 2015-04-02
I have the openh264 codec but I believe it's only for webrtc only, VLC web plugin probably installed by default after VLC correct?  This mplayer plugin which one did you try and install?

---

### Post by TheFu on 2015-04-02
Dont remember this being hard. This is the only package:
```
$ dpkg -l|grep vlc
ii  browser-plugin-vlc                         2.0.6-2                               i386         multimedia plugin for web browsers based on VLC

```  Lots of other non-web items in the list removed.

The others must have been installed using the firefox plugin/extension methods.

---

### Post by Swiftjay on 2015-04-02
I installed that but it didn't show up but I came across this thread: [http://www.ghacks.net/2014/07/25/enable-mse-h2-64-support-youtube-firefox-right-now/](http://www.ghacks.net/2014/07/25/enable-mse-h2-64-support-youtube-firefox-right-now/)

says to enable 


[LIST=1]
[*]media.mediasource.mp4.enabled to true
[*]media.fragmented-mp4.exposed to true
[*]media.fragmented-mp4.ffmpeg to true
[*]media.fragmented-mp4.gmp to true
[*]media.fragmented-mp4.use-blank-decoder to false
[/LIST]
I then was able to have mse & h.264 blue ticked :).

Some other packages I installed to help other people were:

gstreamer1.0 bad,ugly codecs also and ubuntu-restrictive

I hope this helps others.  Thanks TheFu for your help.

---

