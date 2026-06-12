---
title: "Watching PVR video in VLC"
date: 2006-09-21
forum: Desktop Environments
---

### Post by Green_Star on 2006-09-21
Is any one know how to watch TV using VLC? I tried [http://www.videolan.org/doc/streaming-howto/en/ch10.html](http://www.videolan.org/doc/streaming-howto/en/ch10.html), but no success.

---

### Post by reclusivemonkey on 2006-09-25
> **Green_Star said:**
> Is any one know how to watch TV using VLC? I tried [http://www.videolan.org/doc/streaming-howto/en/ch10.html](http://www.videolan.org/doc/streaming-howto/en/ch10.html), but no success.

You may find it easier to get TVTime working. Some more details about what TV card you have may help too! ;)

---

### Post by Green_Star on 2006-09-26
> **reclusivemonkey said:**
> You may find it easier to get TVTime working. Some more details about what TV card you have may help too! ;)

i have PVR-150, now i am able to watch tv using VLC, the problem is my ivtv stoped working after kernel update.

Now I am trying to see closed captioning on my vlc screen, any clue how to do that? my settings are
$ ivtvctl -X
ioctl IVTV_IOC_G_VBI_EMBED ok
vbi embedded in MPEG stream: on

$ ivtvctl -B
ioctl VIDIOC_G_FMT ok
vbi service_set = 00001000

$ ivtvctl -W
ioctl IVTV_IOC_G_VBI_PASSTHROUGH ok
VBI passthrough mode is 00000000

---

### Post by SuprNoodles on 2008-02-08
There's a guide here that may help people get started with viewing TV using VLC Player: [http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/](http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/)

---

### Post by reclusivemonkey on 2008-02-08
> **SuprNoodles said:**
> There's a guide here that may help people get started with viewing TV using VLC Player: [http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/](http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/)

There are also plans to make Totem compatible with MythTV in Gnome 2.22 via a plugin;

[http://live.gnome.org/RoadMap](http://live.gnome.org/RoadMap)

Also, I personally never had any trouble getting MythTV in a small windowed screen; you need to tick an option somewhere to allow it to show in a windowed screen and then adjust the screen size. Looks like you had fun learning alternatives though which is always good =]

---

