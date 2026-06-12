---
title: "Alternating between 16-bit and 24-bit color"
date: 2008-03-26
forum: Desktop Environments
---

### Post by canytech on 2008-03-26
I just finished setting up my first Linux box, a ThinkPad 600X. Aside from a few glitches regarding my inability to use standard acpi or apm, it's working pretty well. Before I give this thing to my daughter, I've got one issue I'd like to smooth out. The movie player only works when I've got the display set for 24-bit color, but flash movies in Firefox only work decently at 16-bit color.

Having failed to find a software combination that always works at a single color density, I'd like to give her some way to change the color density from the desktop. The only way I know to change color density is
  **gksu gedit /etc/X11/xorg.conf**.
This is OK for me, but definitely not for her. Is there some way to change the color density from the GUI? If not, can somebody give me a start on how to write a script that will make the necessary change?

Thanks in advance. This forum has been absolutely crucial in my success so far in getting this box working.

Best regards,
Steve

---

### Post by warp99 on 2008-03-26
That seems like an issue with your flash player since I can play flash video very easy using 24-bit settings on all of my machines. Are you using Adobe 9 Flash Player?

Try this, play a flash video in Firefox then right click on the mouse and check the video quality settings. They should be set to "High Quality". :)

---

### Post by canytech on 2008-03-26
Thanks for your ideas, Warp99. My flash player is the latest from Adobe. I didn't see a version number, but it's whatever the .tar was on their site two days ago. I gather that would be 9! As for video quality, I did your check and confirmed that it's high quality. Regardless of whether I switch to medium or low quality, the frame rate looks to be about two or three frames per second.

---

### Post by warp99 on 2008-03-26
What's your screen resolution? You may be bumping up against the maximum and don't have enough video memory to run 24-bit with all applications. ;)

Edit:

This post talks about problems with video resolution and the 600 series:

[http://ubuntuforums.org/showpost.php?p=3663723&postcount=8](http://ubuntuforums.org/showpost.php?p=3663723&postcount=8)

---

### Post by warp99 on 2008-03-26
You know that you can run 24-bit video using 16-bit color depth if you force mplayer to use the x11 driver? I do this on a Fujitsu P2120 notebook because it can't run 24-bit video in the resolution I would like. ;)

---

### Post by canytech on 2008-03-26
Oh yeah, I'm sure you're right. Seems to me I was limited to some fairly pathetic color depth when I ran Windows on this machine, and now I'm at 1024x768 with 24-bit color. So I know how to adjust to 16-bit color and make everything work well except Totem Movie Player, MPlayer or VLC media player. Totem Movie Player works great at 1024x768/24-bit.

In your last post, Warp99, you mentioned running MPlayer 24-bit video with 16-bit color depth using the x11 driver. I'll go try to look that up. I'm too much of a noob to know how to change drivers, but I assume I can find out if I look around. I really appreciate the good idea.

---

### Post by warp99 on 2008-03-26
If you change the resolution to 800x600 as suggested by the link I posted you shouldn't have any problems playing the flash video at a color depth of 24. Also that should have been 32-bit video (DVD quality) at a color depth of 16, my mistake. :( 

As for forcing x11 video you just have to change the driver in the preferences dialog of gmplayer and VLC or the settings dialog of xine if you have those players installed. All of these players can use the x11 driver.

Now with Totem you have to edit the config file since it doesn't allow you to change the driver from the GUI menu and this is how you do it:

Open the xine_config file:
```
gedit ~/.gnome2/Totem/xine_config
```

Scroll down to the video driver location:
```
# video driver to use
# string, default: auto
#video.driver:auto
```

and change the line last line to read:
```
video.driver:xshm
```

Save the file and you can now watch 32-bit video with a color depth of 16. ;)

---

### Post by canytech on 2008-04-01
Wow! Thank you for your excellent support. I apologize for my tardiness in reply, but I want to say that your advice was spot-on and now I have Flash video, Totem and VLC movie video all working without need for resetting anything.

Thank you, thank you, thank you. I am ecstatic.

---

