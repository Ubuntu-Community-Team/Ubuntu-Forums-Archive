---
title: "Switch defaut webcam"
date: 2017-06-29
forum: Desktop Environments
---

### Post by Deanobats on 2017-06-29
Hi all, I have a Lenovo Thinkpad with a built-in webcam. When I attach an external webcam then I can select which to use in Cheese. However, the built-in webcam seems to be set as default, so when I use Skype or flash-based chat rooms then only the integrated camera is selected and I can't find a way of setting the external one to default or of accessing it anywhere. Both cameras are listed under dev/v4l and I've tried the Qt V4L2 test utility but only the default camera listed under /dev/video0 is shown and I can't seem to find another anywhere. I have:

crw-rw----+ 1 root video 81, 0 Jun 29 09:21 /dev/video0
crw-rw----+ 1 root video 81, 1 Jun 29 11:28 /dev/video1

Listed

Any ideas?

---

