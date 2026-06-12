---
title: "wmv and mpgs don't work after video driver fix"
date: 2006-09-08
forum: Desktop Environments
---

### Post by redpants on 2006-09-08
I had been having some trouble with my video driver installing properly (Radeon Mobility x1400 on a Dell 6400 laptop) and narrowed the problem down to CLAM Antivirus.  After uninstalling the antivirus, I was able to get my video driver installed properly, but now none of my wmv files will play--when I double click on them the movie player pops up and immediately goes away, and many of my mpgs and other video formats have poor quality, usually with a green bar of distortion on near the top of the video.  All of those files were playing fine before I upgraded the video driver.

The way I got the video codecs working the first time was by running automatix, so I went ahead and ran it again just to see (only the video and DVD codecs part) and it didn't make a difference.

Anyone have any ideas they can give an ubuntu newb?

---

### Post by redpants on 2006-09-08
Looks like everything works when I swith from Totem to MPlayer, so I just went ahead and set MPlayer as my default for all my video types.  The only file type that seems to have problems, regardless of the player, is .qt format, which is an older format anyway so don't know if it is even supported or not.

Oddly enough, I do have one avi that doesn't want to play in MPlayer...just the one.  But that one works fine in Totem...weird.  I guess it has to do with what codec they were encoded with.  That particular avi I made with Adobe Premiere Elements, so maybe it encodes it with a non-standard codec.

VLC doesn't want to play most of my files, either, for some reason, but will play more than Totem.

---

