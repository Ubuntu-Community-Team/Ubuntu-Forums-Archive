---
title: "Screenshotting video - Just get a blue screen"
date: 2005-02-28
forum: Desktop Environments
---

### Post by ixus_123 on 2005-02-28
How do I include what is playing in a video player when I screenshot.  I have used the Gnome & Gimp screenshot tools but keep getting a blue box instead of the video.

---

### Post by alastair on 2005-02-28
I know Xine has a special "button" to take a screenshot - perhaps mplayer as well. The problem is, the video is displayed in a different way to the rest of the screen (research) and will not appear with a normal X screenshot. You might need to do some compositing ...

P.S. I am no expert - there might well be ways round this.

---

### Post by landotter on 2005-02-28
[QUOTE=ixus_123]How do I include what is playing in a video player when I screenshot. I have used the Gnome & Gimp screenshot tools but keep getting a blue box instead of the video.[/QUOTE]

As the other poster said--there's no tool or way to take a screenshot with video in it other than to capture a still image using Xine or Totem, then composite it into the screenshot using the Gimp.

---

### Post by ixus_123 on 2005-02-28
Yes there is.  I just don't know how :(

My old slackware system could screenshot video - I am not sure what's different here?

take a look

[IMG]http://img.photobucket.com/albums/v284/ixus_123/screenshots/bbxnest.jpg[/IMG]

---

### Post by Daniel G. Taylor on 2005-02-28
Now, I'm no expert so take this all with a grain of salt.

If you are using accelerated video drivers it is quite possible that video programs are using this to their advantage and "drawing" directly on the video hardware (bypassing the screen buffer of which the screenshot is taken). I know for sure this is a problem with OSX and taking screenshots of DVD Player. The program essentially draws a blue box onto the buffer and fills it on the graphics chip. When you take a shot of the buffer you only get the blue box.

Are you currently using different drivers or other software than what you were in the original screenshot? This could be the reason...

---

### Post by cmsj on 2005-03-01
Daniel is exactly right. X provides a mechanism (Xv) for programs that are doing things like TV/movies to write the video data directly to the graphics card, this allows the card to use features like hardware scaling to make the video play fullscreen with almost no CPU usage.
That does mean that the video will not technically be on the desktop and won't show up in screenies. If you're still using the original gstreamer based totem that ships with warty (ie you *haven't* installed totem-xine) you can temporarily prevent gstreamer from using Xv for the output.
Open up a terminal and run gstreamer-properties, go into the Video tab and change the output to "XWindows (no Xv)", restart totem, play the video, take a screenshot, marvel at the splendour, put the gstreamer setting back to "XWindows (X11/XShm/Xv)" and go about your day :)

---

### Post by ixus_123 on 2005-03-01
Ah, okay.  That makes sense.  I don't think graohics drivers were installed on th slackware box - I can't really remember - that screenshot is nearly a year old.

I do have the nvidia graphics driver installed on this ubunti system though.  I'm only using mplayer & xine.  ~I couldn't get the original totem to play anything.

Thanks for help & advice guys :)

---

### Post by Qdlaty on 2005-03-01
Hi.
There is a way to get nice screenshot with mplayer working.
All you have to do is change in Video preferences display driver. Instead using XV use X11 for a while (remember to restart mplayer after change).
I made my [screenshot](http://tinyurl.com/5c7lg)  in that way.

Q

---

### Post by landotter on 2005-03-01
[QUOTE=Qdlaty]Hi.
There is a way to get nice screenshot with mplayer working.
All you have to do is change in Video preferences display driver. Instead using XV use X11 for a while (remember to restart mplayer after change).
I made my [screenshot](http://tinyurl.com/5c7lg)  in that way.

Q[/QUOTE]
 Nice hint!

Will save me Gimping time in the future.

:D

---

### Post by ixus_123 on 2005-03-02
**Qdlaty:**   That's excellent!  Thanks - nice, easy, & quick :)  

Perfect

---

