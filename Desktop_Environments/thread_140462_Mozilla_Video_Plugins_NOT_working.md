---
title: "Mozilla Video Plugins NOT working"
date: 2006-03-06
forum: Desktop Environments
---

### Post by Maverick88 on 2006-03-06
I justy installed Breezy with firefox 1.0.7. I have installed the following:

gstreamer0.8-plugins
gstreamer0.8-plugins-multiverse
w32codecs
mozilla-mplayer
flashplayer-mozilla

I also installed RealPlayer.

When I enter about:plugins in firefox, firefox shows all the plugins installed.

But I cannot watch any videos.  When I try to watch movie trailers at the Apple Quicktime Movie Site, I see the embedded movie window and the following message in the status bar "Waiting for movies.apple.com".  

When I try to play Quicktime movies at [http://www.mc-internet.com/wedding/samples.html](http://www.mc-internet.com/wedding/samples.html), I get the message :"Totem cannot play fd://0"

When I try to play Windows Media Video at [http://www.mc-internet.com/wedding/samples.html](http://www.mc-internet.com/wedding/samples.html), the embedded movie window is displayed but the video does not start / display.
When I try to watch WM9 video files, firefox crashes.

What is wrong? Any ideas?

Rob

---

### Post by knalle on 2006-03-06
personally i have good experience with the **vlc player** and its **mozilla-vlc** plugin, it works on quicktime, wmv and mpeg and more.

---

### Post by frodon on 2006-03-06
Does quicktime and wmv videos works well outside of firefox ?, i mean are you able to read them.
If yes your problem is not with the codecs, the best way i found to play embedded movies is the "media player connectivity" extension of firefox, it just open the stream with the player of your choice and allow you to save it on your disk if you want.
To test this extension you need to uninstall the mozilla-mplayer plugin.

---

### Post by Maverick88 on 2006-03-06
Thanks for all the tips.  I think the problem lies with the totem plugin.  How can I remove it from Firefox?

I just want to use mplayer to play WM and QT files.

Rob

---

### Post by Maverick88 on 2006-03-07
There is a solution!!  

After I did the following, the totem plugin was disabled and the mplayer plugin took over.  I was finally able to see streaming QT and WM content in Firefox!

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a_backup

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt_backup

You might also have to rename the following if they exist (they weren't on my system):

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la_backup

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so_backup

I wish this info was added to the WIKI. Or at minimum this post should be made sticky since I am sure others will have exactly the same problems and experience the same frustration (unless they give up and use automatix).

Rob

---

