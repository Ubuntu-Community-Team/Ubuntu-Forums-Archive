---
title: "Webcam help needed"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Maelgwyn on 2006-08-28
Hey guys,

I'm trying to get my digital camera to connect as a webcam on Ubuntu - it works without a problem on the Windows laptop, but Ubuntu doesn't even recognise that it's plugged in... It's a Fujifilm F420 and does still pics & functions as a webcam...

Can somebody please help me?

---

### Post by peabody on 2006-08-28
> **Maelgwyn said:**
> Hey guys,

I'm trying to get my digital camera to connect as a webcam on Ubuntu - it works without a problem on the Windows laptop, but Ubuntu doesn't even recognise that it's plugged in... It's a Fujifilm F420 and does still pics & functions as a webcam...

Can somebody please help me?

For it to work as a cam it'll have to be recognized as a video device under /dev/video#.  With the cam plugged in, type "ls -l /dev/video*" in a terminal and list what you get.

Edit:

I think I may have found something for your model:

[http://www.zago.net/v4l2/finepix/](http://www.zago.net/v4l2/finepix/)

Doesn't look straight forward though.

Edit 2:

On second thought, it looks as though this driver may be built into the linux kernel on dapper.  The web site is still useful, lists a few ways to interface software with the camera.

---

