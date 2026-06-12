---
title: "reinstall all video codecs in ubuntu"
date: 2009-03-30
forum: General Help
---

### Post by armandli on 2009-03-30
This never happened to me, I know the codecs can work perfectly on my laptop, but for some weird reason, after one reinstall of ubuntu 8.10 (don't ask me why) I tried to install my video codecs for avi and ffmpeg (gstreamer probably, for i forgot the codecs package name) manually through apt-get command line, along with vlc and all other video players.

now, strangely, whenever i play videos using vlc or any video player, the video "flashes", like the time it takes to refresh each image is too slow such that you see black screen after each image refreshed. it hurts my eyes badly. i highly suspect that it's because i might have installed some bad codecs and forgot the name of it. anyone know how to solve the problem? if not, does anyone know all the codecs names so i can remove them all and install them through the Add/Remove Applications program like how i used to install programs?

---

### Post by zvacet on 2009-03-30
In **synaptic>file tab>history you** should see packages you installed.Uninstall them and after that install **ubuntu-restricted-extras**.

---

### Post by DiegoBretti on 2009-03-30
> **armandli said:**
> This never happened to me, I know the codecs can work perfectly on my laptop, but for some weird reason, after one reinstall of ubuntu 8.10 (don't ask me why) I tried to install my video codecs for avi and ffmpeg (gstreamer probably, for i forgot the codecs package name) manually through apt-get command line, along with vlc and all other video players.

now, strangely, whenever i play videos using vlc or any video player, the video "flashes", like the time it takes to refresh each image is too slow such that you see black screen after each image refreshed. it hurts my eyes badly. i highly suspect that it's because i might have installed some bad codecs and forgot the name of it. anyone know how to solve the problem? if not, does anyone know all the codecs names so i can remove them all and install them through the Add/Remove Applications program like how i used to install programs?

Go to "Synaptic Package Manager" uninstall the codec and install again the codec. And select "gl, x11,..." in your VLC. I recommend you SMPlayer with gl.

---

