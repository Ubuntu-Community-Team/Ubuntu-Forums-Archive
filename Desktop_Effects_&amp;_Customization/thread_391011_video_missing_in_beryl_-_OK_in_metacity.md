---
title: "video missing in beryl - OK in metacity"
date: 2007-03-22
forum: Desktop Effects &amp; Customization
---

### Post by thomaswp on 2007-03-22
When I watch a video within beryl, the video goes missing.  

In Movie Player: When I move the window one frame appears to flash up, otherwise I am looking at a blank screen.

In real player:  the picture flickers badly showing the real logo behind.

When I switch to metacity the problems go away.

I am using an DELL Inspiron 1300 with the i915 drivers.

No idea how to fix this.  Anyone got any ideas?

---

### Post by Gargamella on 2007-03-22
the same for me i have the same video card but using a lenovo 3000 c100, anyway I was going to find an answer but i join the post for a solution

---

### Post by Yoooder on 2007-03-22
Try this, at least for the sake of further diagnosis.  With beryl running, open beryl-manager, and try turning off a single Visual Effect and then playing a video, turning off another and replaying the video, etc...

See if the problem is specific to a particular effect within Beryl, or if it's present across the board.  I run a 6600 and have issues whenever using the Blur effect (which is known to have problems when combined with nvidia cards).

---

### Post by reacocard on 2007-03-22
You need to use a different video driver. No, not a hardware driver, a rendering driver. Look in your video player's Preferences for a video driver option. Xshm/X11 works best with beryl, but it's rather taxing on your CPU. I have found Xv works reasonably well, with extremely low cpu usage. Don't even try the OpenGL option, it just won't work under beryl.

---

### Post by thomaswp on 2007-03-23
I tried switching everything off in Beryl.  No joy.

I had already looked in Movie Player for some other options.  No joy.  

MPlayer was refusing to play the ogg "ubuntu" file in the "examples" folder but with the GStreamer codecs installed this does play now (with a codec error). 

Anyway, digging in MPlayer I found the option (Right click > Preferences) to change the driver and selected X11.  It works fine now - even Real Player works (just about).  I had found that before but just assumed it was "available" drivers, not selectable.

So, I am happy(er) now.

---

### Post by icemanblues on 2007-03-27
What I found is that if you run the MPlayer window in its own virtual desktop, it will display fine.  But once another window (including the MPlayer controls window) is on the same desktop, the issue returns.

Now, I like the X11 fix.  But then when I resize the video or fullscreen it, it doesn't expand.  Any other configurations I can make there?

---

### Post by reacocard on 2007-03-27
> **icemanblues said:**
> What I found is that if you run the MPlayer window in its own virtual desktop, it will display fine.  But once another window (including the MPlayer controls window) is on the same desktop, the issue returns.

Now, I like the X11 fix.  But then when I resize the video or fullscreen it, it doesn't expand.  Any other configurations I can make there?

You'll have to tell mplayer to allow software scaling.

---

### Post by sonny on 2007-04-01
> **reacocard said:**
> You'll have to tell mplayer to allow software scaling.

Where do I check that option? or is it through the CL?

---

### Post by ector on 2007-04-19
> **sonny said:**
> Where do I check that option? or is it through the CL?

I had the same problem.. answer here ;)

[http://ubuntuforums.org/showpost.php?p=642615&postcount=6](http://ubuntuforums.org/showpost.php?p=642615&postcount=6)

---

