---
title: "Streaming Problem in Firefox"
date: 2009-02-26
forum: General Help
---

### Post by Dbzdude707 on 2009-02-26
When I try to stream videos on Veoh.com, I get this (when running it from the terminal):
```
Loading stream: http://www.veoh.com/static/swf/webplayer/WebPlayer.swf?version=AFrontend.5.3.10.2.1001
unhandled event 9
Unable to write new config file: Failed to create file '/root/.config/swfdec-mozilla.conf.J24VPU': No such file or directory
unhandled event 10
```

It won't stream the videos at all.

When I try to stream from youtube, sometimes it will work, but half the time it will just make Firefox stop responding. I'll see if I can't get the terminal code for that too, hold on.

---

### Post by Dbzdude707 on 2009-02-26
Alright, when I load a video on Youtube, it gives me this (as well as becoming gray and forcing me to Force Quit it):

```
Loading stream: http://www.youtube.com/active_sharing.swf
unhandled event 19
Loading stream: http://s.ytimg.com/yt/swf/watch-vfl80519.swf
Unable to write new config file: Failed to create file '/root/.config/swfdec-mozilla.conf.26Y5PU': No such file or directory
Loading stream: http://s.ytimg.com/yt/swf/ad-vfl79359.swf
SWFDEC: ERROR: swfdec_font.c(378): tag_func_define_font_name: didn't find a font with id 9
Loading stream: http://www.youtube.com/crossdomain.xml
SWFDEC: ERROR: swfdec_font.c(378): tag_func_define_font_name: didn't find a font with id 7
Loading stream: http://v4.cache.googlevideo.com/videoplayback?id=6ef12541c6f36d71&itag=34&ip=24.214.188.76&region=0&signature=A93736B1C9F953E3383CC40E59FF24D931648720.D65312844DEA3711D43B9559611BD879985CE47A&sver=2&expire=1235702074&key=yt1&ipbits=0
SWFDEC: ERROR: swfdec_video_decoder.c(375): swfdec_video_decoder_errorv: error decoding video: no suitable decoder for video codec 7
SWFDEC: ERROR: swfdec_audio_decoder.c(201): swfdec_audio_decoder_errorv: error decoding audio: no suitable decoder for audio codec 10
```

Note: I have tried installing the latest flash player, and I have the latest Totem Gstreamer package installed. I have also tried uninstalling and reinstalling Firefox, and rebooting my computer. None of these worked.

EDIT: Also, this is a new installation of 8.10 Intrepid. I installed it just a few days ago. The only major change I've done is to install the ubuntu-restricted-extras package.

---

### Post by Dbzdude707 on 2009-02-26
Does anyone know what the problem is?

---

### Post by Dbzdude707 on 2009-02-26
It's been a couple hours since I made this topic... No one knows?

---

### Post by Yashiro on 2009-02-26
Uninstall all your flash plugins and then install flashplugin-nonfree from the medibuntu repository (look it up).
If you are using 64bit then get the alpha 64bit flash and install it into your home directory instead.

There are loads of threads related to flash problems. You should use the search function more rigorously before bumping for help.

---

