---
title: "Framebuffer confusion"
date: 2009-03-22
forum: General Help
---

### Post by JohnFH on 2009-03-22
I'm a bit confused about framebuffers, X and graphics in general.  Once upon a time I thought that X had to be running to watch movies, see images, etc. but mplayer can use the framebuffer video driver in a virtual terminal to display a movie.  I don't understand that and I have a few quesions relating to it.  

1. If mplayer doesn't need X to run in order to display movies, why can't the framebuffer be used all the time to display graphics?  

2. If movies can be run in a virtual terminal without X11 running, can images be displayed as well?  I would have thought so, but haven't found a way to do it.

3. Similarly, if movies and images can be displayed in a virtual terminal, so can the graphics of a web page surely?  

If you have any answers, let me know.  Thanks!

---

### Post by Dr Small on 2009-03-22
I use cacaview to view images in framebuffer. For Ubuntu, you need to install `caca-utils`. And then these should be installed:
```
caca-config  cacademo     cacamoir     cacaview     
cacaball     cacafire     cacaplas     
```

---

### Post by JohnFH on 2009-03-22
Thanks, but that's using ascii art rather than displaying the actual image.  'mplayer -vo fbdev' will play the actual movie file in a virtual terminal.

---

### Post by lloyd_b on 2009-03-22
> **JohnFH said:**
> I'm a bit confused about framebuffers, X and graphics in general.  Once upon a time I thought that X had to be running to watch movies, see images, etc. but mplayer can use the framebuffer video driver in a virtual terminal to display a movie.  I don't understand that and I have a few quesions relating to it.  

1. If mplayer doesn't need X to run in order to display movies, why can't the framebuffer be used all the time to display graphics?  

2. If movies can be run in a virtual terminal without X11 running, can images be displayed as well?  I would have thought so, but haven't found a way to do it.

3. Similarly, if movies and images can be displayed in a virtual terminal, so can the graphics of a web page surely?  

If you have any answers, let me know.  Thanks!

You're confusing two different things.  The framebuffer is a video device, period.  X is a set of routines for accessing a video device, as well as other things (cursors, mouse click events, keypress handling, window creation and management, etc.).  

You *can* use the framebuffer device as an X video device (it's usually less efficient than using the device specific driver, though).

As for your web page example, that not only requires video and input handling, it also requires a rendering engine to display the web content properly.

In short - it's *possible* to do anything without X that is done with X.  It's just a heck of a lot more work for the developer.  And good developers understand the concept of "don't reinvent the wheel" - they aren't going to do the work required to duplicate something like Firefox unless there's a heck of a good reason for doing so.

Lloyd B.

---

### Post by JohnFH on 2009-03-22
Ah, I see!  So mplayer is being smart by accessing the video device directly (fbdev) without X, when really the X (interface?) makes it a lot easier and more efficient to develop graphical front ends?  That makes sense to me - thanks!

---

