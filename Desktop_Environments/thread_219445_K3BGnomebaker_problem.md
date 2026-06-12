---
title: "K3B/Gnomebaker problem"
date: 2006-07-20
forum: Desktop Environments
---

### Post by MakLeod on 2006-07-20
I've installed all of the codecs from Easyubuntu, but whenever I try to burn an audio cd I get the response of:

Unable to handle the following files due to an unsupported format: (the name of the .mp3 file)

The other thing is I can listen to all of my mp3's just fine, and also can view all of my avi and mpeg videos.  Any ideas as to what I am doing wrong?  Thanks.

---

### Post by croak77 on 2006-07-20
> **MakLeod said:**
> I've installed all of the codecs from Easyubuntu, but whenever I try to burn an audio cd I get the response of:

Unable to handle the following files due to an unsupported format: (the name of the .mp3 file)

The other thing is I can listen to all of my mp3's just fine, and also can view all of my avi and mpeg videos.  Any ideas as to what I am doing wrong?  Thanks.

Check to see if you have gstreamer0.8-lame (for Gnomebaker) and libk3b2-mp3 (for K3B) installed.

---

### Post by mcduck on 2006-07-20
For some reason Gnomebaker still uses gstreamer-0.8 while rhythmbox (and most of player apps) uses 0.10 so you need to install codecs for both gstreamer versions :rolleyes:

---

### Post by MakLeod on 2006-07-20
sorry, how do i go about installing those codecs?  is there an easy apt-get command?  thanks.

---

### Post by MakLeod on 2006-07-20
actually got it to work for k3b, which i like better than gnomebaker anyway, thanks!

---

