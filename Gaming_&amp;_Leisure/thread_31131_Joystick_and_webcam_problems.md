---
title: "Joystick and webcam problems"
date: 2005-05-01
forum: Gaming &amp; Leisure
---

### Post by Heretic09 on 2005-05-01
Been using kubuntu for a while and I have two hardware problems

1) joystick problem
Analog joystick connected to soundcard doesn't work. Sound card works fine. I figure its because there aren't any js devices in /dev. I tried creating it with MAKEDEV, it claims it created about 4 js devices but when I look in the dev directory they are not there. Yes I am running it as root.

2) web cam problem
I have a creative video blaster 3 (kubuntu sees it as ov511) which worked fine as soon as I plugged it in when I used to run suse. If I run xawtv it works great. But gnomemeeting and vlc won't work with it. Gnomemeeting gives me a message "error opening /dev/video0". I do have load "v4l" in xorg.conf and downloaded libpt-plugins-v4l but I stilll get the same error.

Any thoughts on what maybe be causing these problems?

---

### Post by foolsh on 2005-11-13
[http://home.insightbb.com/~foolsh/]("http://home.insightbb.com/~foolsh/")

---

