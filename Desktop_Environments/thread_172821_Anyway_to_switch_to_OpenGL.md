---
title: "Anyway to switch to OpenGL?"
date: 2006-05-09
forum: Desktop Environments
---

### Post by PrimoTurbo on 2006-05-09
As I understand Multimedia Systems Selector or gstream-properties determines what your system uses as output? Does Totem follow what is in this? Because I cannot figure out how to switch from XV or No XV rendering pipeline to OpenGL like I have in Mplayer.

I have been able to fix the pixelated video I get after installing fglrx in Totem by adding Option "VideoOverlay" "on" & Option "OpenGLOverlay" "off" to my xorg.conf

But I still have flikering issues, like the colors in a video slightly flicker. It's a little annoying and I really want to use Totem because I like the interface a lot. Under Mplayer and VLC I use openGL as output and have no video problems but I hate their interface, especially VLC which is really ugly.

Is there a way to have Totem use OpenGL as video output? Is there a way to have Multimedia System Selector use some type of an OpenGL plugin?...

---

### Post by PrimoTurbo on 2006-05-09
Also I noticed mplayer can mess up and the sound and image don't match if I switch to a different part of the movie. Sometimes the video slows down, any ideas?

And is it possible to make VLC look better and to give it some controls during full screen. I want to be able to skip between the video in full screen, change sound volume and pause. Thanks guys.

---

### Post by ariel on 2006-06-03
Yes there is a way: change totem video output: gedit ~/.gnome2/totem_config, add: video.driver:opengl

Now I have a problem myself with this. I am trying to use opengl for video playback, under XGL, and for some reason all media players when set to use opengl, the play OK and can be maximized with good quality, but insert white "flashes" or flickers every now and them. I think this is related to a parameter called VSYNC, but I'm still investigating. 
good luck!

---

