---
title: "video playback jagged"
date: 2005-12-15
forum: General Help
---

### Post by lysis on 2005-12-15
when i play dvds or avis or anything all the videos are jagged.  i've got fglrx installed, is there a way to get anti-aliasing or something on video?  that's the ONLY thing windows is doing better for me now . . .

---

### Post by John.Michael.Kane on 2005-12-15
do you have dma inabled on the dvd drive? sometimes is the cause of the jaged playback..

---

### Post by bb002 on 2005-12-15
What are you using to play videos with?

For me I had this problem with totem using the gstreamer backend. After enabling all repositories replacing the totem-gstreamer package with the totem-xine package in synaptic fixed my jerking video playback problems.

---

### Post by lysis on 2005-12-15
i'm using totem-xine.  it's not jerky;  it looks like a video game on a poor video card with no anti-aliasing.  all the people have little "stairs" for arms because it's making all lines jagged.

---

### Post by kaamos on 2005-12-15
In terminal: sudo gedit /etc/X11/xorg.conf
find the Section "Device" and add:
```
     Option "VideoOverlay" "on"
     Option "OpenGLOverlay" "off"
```
Then log out and back in (by pressing ctrl+alt+backspace) and make sure your applications are using the xv video-output.

Hope it works. :)

---

### Post by lysis on 2005-12-15
will that disable opengl for when i play full-screen games?

---

### Post by kaamos on 2005-12-15
No, for me it has only affected video playback.

---

### Post by lysis on 2005-12-15
this is actually how it's already setup for me (no changes were made)

should i maybe try the OTHER way?

---

### Post by jobsonandrew on 2007-09-19
I was having this problem with totem... all of my videos were playing smoothly and well, but they looked really blocky.. like lego! Then this solved my problem:

> In terminal: sudo gedit /etc/X11/xorg.conf
find the Section "Device" and add:

```
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
```

Then log out and back in (by pressing ctrl+alt+backspace) and make sure your applications are using the xv video-output.

now videos look as they should.. obviously a 320x240 video wont look great fullscreen, but they shouldnt be ultra blocky and jagged

---

