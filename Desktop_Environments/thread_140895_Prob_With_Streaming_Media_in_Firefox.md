---
title: "Prob With Streaming Media in Firefox"
date: 2006-03-07
forum: Desktop Environments
---

### Post by OffHand on 2006-03-07
Hi all
I have installed the following applications/codecs:

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux  <-- This one failed to install
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

Then did: 

sudo apt-get install mplayer-386
sudo apt-get install mplayer-fonts
sudo apt-get install mozilla-mplayer
sudo cp /etc/mplayer/mplayer.conf /etc/mplayer/mplayer.conf_backup
sudo gedit /etc/mplayer/mplayer.conf

And changed it to:

vo=xv,			# To specify default video driver (see -vo help for
			# list)


Still I don't have streaming media within Firefox.
Is there anyone who can help me out? Is it the plugin that failed to install?
I can play most video's on my HD.
Thanks in advance
Subsonic

---

### Post by frodon on 2006-03-07
Never get any luck with the mplayer plugin too, try the "media player connectivity" extension of firefox, you will like it ;)

---

### Post by OffHand on 2006-03-07
Thnx. I tried it. It works although some error messages pop up and the stream don't play smoothly. My internet connection is fine.
Still this doesn't satisfy me. If others can get it to work I should be able to aswell. Still looking for a solution. Cheers

---

### Post by frodon on 2006-03-07
What pop up messages do you get ?

You can configure the plugin, for exemple i open wmv with xine-ui because it don't work with totem for me but i select totem for mpg files because in that case it works well.
You should try to change the player that the plugin use.

Otherwise you could try the vlc plugin for mozilla (it's in the repositories), some users said here that it works great but i never tried it myself since this extension is all i need.

Good luck ;)

---

### Post by OffHand on 2006-03-07
The error had something to do with af_inet 6, whatever that may be  :)
I installed the vlc plugin with synaptic.
How do I tell Firefox to use this plugin?

---

### Post by OffHand on 2006-03-07
Also nothing of the mplayer or vlc shows up in about:plugins in firefox.

---

### Post by OffHand on 2006-03-07
Solution: copy all the files in /usr/lib/mozilla/plugins to your ~/.mozilla/plugins dir

Jeez man, that's freaking simple. Glad it works now. 
This should be in the guide.

---

### Post by Maverick88 on 2006-03-07
I had similar problems with trying to get firefox to play streaming QT and WM9 videos.  I tracked it down to the totem plugin.  Once I disabled the totem plugin and let the mplayer plugin takeover, I was able to finally watch QT and WM9 videos.

I disabled the totem plugin by doing the following:

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.a_backup

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt_backup

You might also have to rename the following if they exist (they weren't on my system):

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.la_backup

sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so_backup

I wish this info was added to the WIKI. Or at minimum this post should be made sticky since I am sure others will have exactly the same problems and experience the same frustration (unless they give up and use automatix).

Rob

---

### Post by Nordoelum on 2006-04-03
I post here to make it bump :D

---

