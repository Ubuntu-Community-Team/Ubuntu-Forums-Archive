---
title: "ubuntu dell insp. 530 w 22in flatscreen -blanks out after 4+ hours"
date: 2007-09-16
forum: Dell  Ubuntu Support
---

### Post by LesFromWaldenVT on 2007-09-16
I've had this Ubuntu Dell Inspiron 530 for about a month. Whenever I leave it on more than 4 hours (don't know exact timing), the screen is black and when I move the mouse, it gradually turns to a light grey but never comes back on. The system has not crashed I know because once I left RhythmBox running but paused, and when I pressed enter, the music continued playing. Probably the Xserver or the device driver for the video (128Mb nvidia 8300GS) died. Has anyone encountered this problem?

---

### Post by gbrainin on 2007-09-16
No.  We have the same hardware configuration (except that it's the 20-inch wide screen), and have left it on overnight without the screen doing that.

---

### Post by tgalati4 on 2007-09-16
Try control-alt-backspace

Then type 

>startx  (you will be doing this blindly of course)

The see if the display comes back.  If not, then it could be a BIOS energy-saver setting.

---

### Post by LesFromWaldenVT on 2007-09-17
Actually, control+alt+backspace wakes it up without having to enter 'startx'. But, it's like it closed my previous session, and opened a new one. It's like logging out and logging back in. So, it's probably a feature that I have on that I don't want. As far as I can tell, I have the screensaver and powersaver options turned off.

Last night, I turned the monitor off and then back on, and the screen had gone grey immediately. I haven't retested that.

---

