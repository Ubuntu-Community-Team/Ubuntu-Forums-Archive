---
title: "How can I get  rid of the blue video overlay border?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by sparkov on 2006-06-02
*[COLOR="Gray"]I've been trying to turn an old P450 into a media centre for playing CDs/DVDs/streaming video using the TV-out on an Nvidia graphics card (and Nvidia drivers).  I have everything working perfectly using Ubuntu 6.06, however when playing videos there is a blue line present at the top and left of the picture.  This must be the default colour of the video overlay background.  Is there a way of getting rid of this, or at least making the colour black instead of blue so that it is not noticible when playing fullscreen?[/COLOR]*

I found a way to change the colour of the overlay and so managed to solve the problem.

The colour can be changed (in totem at least) by editing the **~/.gnome2/totem_config** file.

Changing ```
#video.device.xv_colorkey:66046
```

to

```
video.device.xv_colorkey:0
```

makes the colour black.

---

