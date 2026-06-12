---
title: "cant see video when beryl run"
date: 2006-12-05
forum: Desktop Environments
---

### Post by pavel_kbc on 2006-12-05
Hello, 
     i cant see video as well when i am using beryl. i am using intel on board agp . 128mb. motherboard : 945gnt intel. so what i have to do? i have insatll the driver

---

### Post by RAOF on 2006-12-05
The problem is (from memory) that the XVideo system that video players use to get smooth playback for video doesn't play well with Beryl.  Beryl never sees the contents of the window properly, so when it tries to draw it the window is black where the video should be.  (Incidentally, that would have made for a better description of your problem :)).

The solution is generally to change the method your media player uses to draw video - you want to select an OpenGL method.  How you actually do this depends on your video player.

---

### Post by pavel_kbc on 2006-12-05
The solution is generally to change the method your media player uses to draw video - you want to select an OpenGL method. How you actually do this depends on your video player.?

how do i do this ?

EDIT: i use Totem

---

### Post by kakalaky on 2006-12-05
on my laptop with an i915 OpenGL didn't work with video.  I had to use X11/shm to play video and get the effects.  How you change these options depends on the player you are using.

---

### Post by pavel_kbc on 2006-12-05
oh please help me.

---

### Post by pavel_kbc on 2006-12-05
:S help meeeeeeeee

---

### Post by kakalaky on 2006-12-05
what player are you using?

---

### Post by RAOF on 2006-12-05
Ok, **totem**.  Now, we (unfortunately) have two options here:
totem-gstreamer (the default) and totem-xine (the not-default).

For totem-gstreamer, what you want to do is install the GStreamer opengl output - the **gstreamer0.10-gl** package.  Then either run System->Preferences->Multimedia Systems Selector or **gstreamer-properties** from a terminal.

Then go to the "Video" tab, and either try a different video sink from the drop-down list, or select "Custom" and type in "glimagesink" to the custom box, to use the OpenGL GStreamer image sink.

If you're using totem-xine, you'll need to edit the ~/.gnome2/totem_config file.  There'll be a section like:
```

# video driver to use
# string, default: auto
video.driver:gl                                                                               
```

You want to make sure that it says "video.driver:gl".

---

### Post by kakalaky on 2006-12-05
Oops, missed the edit.

---

### Post by pavel_kbc on 2006-12-06
doesnt work :( still cant see video. black screen

---

### Post by nahog on 2006-12-08
For me, I have an i810, OpenGL also doesn't work.
I use the X11 output mode.

For example:

Using the VLC player (you can search for it on Synaptic). On Settings/Preferences/Video/Output Modules (activate the "Advanced Option" checkbox), select "X11 video output" from the combobox, and save. That's it.

---

### Post by pavel_kbc on 2006-12-10
its works but bad video quility.Thank you RAOF and nahog, and thank you everyone :D

---

### Post by anemon on 2006-12-11
Hi everyone!

I'm new to the whole Ubuntu business, and I've been having the same problem as pavel_kbc. And I agree: using X11 as the output mode reduces the image quality to an intolerably low level (i.e. fullscreen is out of the question)! And the OpenGL trick doesn't do it for me either: in VLC it doesn't work at all, and in Totem the image shows up, but doesn't scale up to fit in fullscreen mode. 

There must be some better workaround for this problem... But what? Please help!

Edit: I already know of two workarounds. The first one is obvious: disable Beryl (use the Beryl icon > Select window manager > Metacity). A little cumbersome, though, especially since my system tends to freeze when I try to activate Beryl again (in the same menu). The second workaround is more creative. I discovered that the image shows up when you drag a window. So here's what you do: maximize the window of your media player (not fullscreen, but almost), then start dragging it -- and then keep your left mouse button pressed down using a piece of adhesive tape or a weight or something. ;-) I actually watched an entire movie like that!

---

### Post by zgornel on 2006-12-11
> **anemon said:**
> Hi everyone!

I'm new to the whole Ubuntu business, and I've been having the same problem as pavel_kbc. And I agree: using X11 as the output mode reduces the image quality to an intolerably low level (i.e. fullscreen is out of the question)! And the OpenGL trick doesn't do it for me either: in VLC it doesn't work at all, and in Totem the image shows up, but doesn't scale up to fit in fullscreen mode. 

There must be some better workaround for this problem... But what? Please help!

Edit: I already know of two workarounds. The first one is obvious: disable Beryl (use the Beryl icon > Select window manager > Metacity). A little cumbersome, though, especially since my system tends to freeze when I try to activate Beryl again (in the same menu). The second workaround is more creative. I discovered that the image shows up when you drag a window. So here's what you do: maximize the window of your media player (not fullscreen, but almost), then start dragging it -- and then keep your left mouse button pressed down using a piece of adhesive tape or a weight or something. ;-) I actually watched an entire movie like that!

The X11 driver is the safest when running beryl/compiz and no noticeable visual degradation (i810 driver), only slightly increased CPU usage. For full screen, using mplayer, use ```
mplayer -vo x11 -zoom file.avi
```

---

### Post by kd7swh on 2006-12-11
Thanks nahog for the VLC tip. I just ran a quick search to see if anyone else had this problem and I found this thread.

My video works in totem using xine and now vlc with X11 output,

w00t! :-D

---

### Post by anemon on 2006-12-12
Thanks for your help, zgornel -- but I'm not sure that I agree. I did try the X11 mode, and the loss of quality was more than noticable in my mind... And on top of everything, it seems I need to have the fglrx drivers installed to be able to watch DVDs without MAJOR lagging, which again rules out Beryl. Right? I guess I'll just have to live without the rotating workspace cube and the wobbly windows and the zooming in and out -- at least for now! ;-)

Edit: although I will try again with X11, just to make sure!

---

### Post by zgornel on 2006-12-12
I specified, the i810 driver (my videocard is a i915). There are differences but in my case, at least from what I've seen, no upsetting differences. I'm guessing you have a ati card so you may be right, it makes sense to use hardware rendering over software.

---

### Post by pavel_kbc on 2006-12-18
thanks guys .. i got it worked .. :D but bad video quality

---

### Post by s26c.sayan on 2007-02-01
I use VLC too, and was having the same 'black screen' problem on trying to  watch movies while running Beryl . I have sorted it out using X11 as suggested by **Nahog**....Thanx mate!! :)
My card is an inbuilt intel 845G and 256 MB RAM. I dont seem to have any noticable degradation of video quality so far!!

---

### Post by mbradlcu on 2007-02-01
I had the same problem and I seem to have the same hardware,, anywho it's not a proper fix but, 
I installed totem-xine which subsequently removes totem, ubuntu-desktop and gstreamer (bummer) but I installed mplayer and the associated proggys to view streaming media via firefox.
you may find this an decent alternative

---

### Post by jeyaganesh on 2007-02-02
Hi i got the same problem:guitar: . but i can watch movies with sidebar in totem player. if i change volume or move mouse, black screen appears. then again i have to adjust sidebar to see movies. As mentioned in previous reply, the 'left-mouse-button' technique also make video appear. 

Is anyone find permanent fix for this problem? If not, those who have knowledge in this area please fix it soon.

Thanks in advance!):P

---

### Post by jeyaganesh on 2007-02-02
Hi just now i tried to watch videos after shifting to metacity windows manager (from beryl icon) and i could watch videos in good condition even if in full screen mode. After watching video i shift back to beryl window manager. it didnt creat any problem, the windows were just appeared in maximized size. Beryl works smart.
Have fun:lolflag: :lolflag:

---

### Post by shareMenaPeace on 2007-02-02
When i got to many windows open resizing or closing windows triggers black windows.
So this could be a ram issue here in some cases at least.

Disabling beryl settings increase performance - numbers of windows open at the same time.

---

### Post by Brunellus on 2007-02-02
Thread moved to relevant sub-forum.  [Beryl is off-topic in Absolute Beginners](http://www.ubuntuforums.org/showthread.php?t=349732).

---

### Post by juhanfg on 2007-02-08
hi everybody,

I have exactly the same problem with all video players except gxine. For those of you having problems give it a try. I'm talking about having good video, no weird effects, and able to full screen with good quality. 

I hope this helps.

J

---

### Post by nmincone on 2007-02-14
You rock! And for the past week I thought fiddling with my XGL, AIGXL and ATI driver settings in xorg.conf messed something up!!! i can't believe I missed this.

---

### Post by marko_4454 on 2007-04-30
Has anyone been able to fix this? 
I am still with this problem. Like many people, my videos work with gxine but if I use any other program, I have to drag the window size in order to see the video.
Is there no permanent fix for this as of now?

---

### Post by tlayton_at_work on 2007-05-01
For those of you using KDE and Kaffeine, I too had this problem when I upgraded from the xorg-xserver-video-i810 to the new xorg-xserver-video-intel package.  I'm also using the trevino beryl svn debs.

Per comments in this thread about video output, I started Kaffeine, opened Settings -> xine Engine parameters, and selected the video icon.  I changed the driver to 'opengl' in the Beginner Options, hit apply, and ok.

Movies are playing fine now with no black screen.  The only thing I really noticed is that the movie window flashes a couple times at startup, but then is smooth after that.

---

