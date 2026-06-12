---
title: "VGA out with Olevia 27&quot; HDTV"
date: 2006-07-20
forum: Desktop Environments
---

### Post by matthewstory on 2006-07-20
I just bought an Olevia 27" LCD HDTV with VGA input.  I'm trying to configure Ubuntu to output to the TV, but am concerned about destroying my nice new TV.  Just curious if anyone knows the VertRefresh and HorzRefresh rates for this TV, or for a similar TV.

I'm using the NVidia proprietary drivers.

Also as i mentioned above the TV features a VGA input, so i won't need to worry about getting it working with S-Video and TV-out, setting it up like an LCD should work.

---

### Post by rabiddachshund on 2008-01-20
Bump. I'm trying to do basically the same thing, but I'm using Xubuntu on a 26" tv and the only resolution I can get is 800x600. I've got it hooked up and everything, but the display is always off center. For example, the lower panel is just below the display area and I can't see it. Is there any way to force it to center the screen?
As long as I'm here, how would I set it so I can have a higher resolution? I've had problems with this before on Ubuntu Feisty, but that uses X11 and Xubuntu uses Xfce, right? There* is* a difference, right?

---

### Post by anachreon_ on 2008-01-21
This is really easy.  Just look in your manual (if you don't have it in hardcopy you should be able to find it online) for the specifications for your LCD TV.  I have a Westinghouse 27 inch TV, and my manual says that the recommended PC input signal is 1280x720 (makes sense) at 75 hertz.  

So just open up nvidia-settings as super-user (for Kubuntu, hit alt-f2 and then type kdesudo nvidia-settings), then click "X SERVER DISPLAY CONFIGURATION".  Make sure your TV is already plugged into your computer when you do this, or it won't show up.

Click on the rectangle representing your LCD TV (it will probably say "(disabled)"), click "configure" and then choose a separate X display or TwinView, whichever you need.  At that point, just enter in the display resolution your TV supports, and the refresh rate you found in your manual.  

If you choose "Separate X Display," you'll need to restart your X server, so save your settings to the X Configuration File, quit, and then hit Ctrl-alt-backspace to restart X.  Your display should now output to the LCD TV.

Let me know if that works for you.

---

