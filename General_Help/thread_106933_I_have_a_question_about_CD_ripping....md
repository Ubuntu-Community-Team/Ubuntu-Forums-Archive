---
title: "I have a question about CD ripping..."
date: 2005-12-21
forum: General Help
---

### Post by XtremeGamer99 on 2005-12-21
How can I extract CD tracks to MP3 format?

As you can see, MP3 is disabled for some reason:
[http://xgamer.insder.com/bleh/mp3wtf.png](http://xgamer.insder.com/bleh/mp3wtf.png)

Any help? Thanks.

---

### Post by matthew on 2005-12-21
You will need to install the codecs that allow you to use mp3 formatted music. Read this page for more info:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Madpilot on 2005-12-21
[https://wiki.ubuntu.com/CDRipping](https://wiki.ubuntu.com/CDRipping)

has info on setting SoundJuicer up to rip mp3.

I haven't actually used it myself, because .ogg plays fine in Ubuntu and I don't have an iPod or whatever...

---

### Post by kingsidy on 2005-12-21
i use "grip". make sure that you have the right codecs though. It rips and converts to mp3 automatically

---

### Post by XtremeGamer99 on 2005-12-21
Still not working.
[http://xgamer.ath.cx/](http://xgamer.ath.cx/)
I went to Synaptic Package Manager > Settings > Repositories > Settings > enabled "Show disabled software sources".

I then enabled all sources in the repositories window, closed it, and let it download whatever it wanted to download. After it was done, I put in:

```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
```

And it gave me this:

```
root@ryan:~# sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
E: Couldn't find package gstreamer0.8-plugins-multiverse
root@ryan:~#
```

Heh, this is really frustrating... v_v

---

### Post by sjh on 2005-12-21
I set up Sound Juicer using this:

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

Seems to be a typo where "gstreamer8.0-lame" should be "gstreamer0.8-lame".  

Hope this helps
SJH

---

### Post by XtremeGamer99 on 2005-12-22
I got it working. Thanks!

---

