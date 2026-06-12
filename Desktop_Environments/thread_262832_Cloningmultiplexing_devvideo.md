---
title: "Cloning/multiplexing /dev/video"
date: 2006-09-22
forum: Desktop Environments
---

### Post by blazko on 2006-09-22
Hello,

I have a working V4L device /dev/video0. As soon as some app has access to it, this device is not available to others anylonger. Thus, is it possible to clone /dev/video0 to e.g. /dev/video1 and /dev/video2 so that multiple apps can access the same data?

Might this be done e.g. w/ ffserver?

Sorry, googling did not work as you get tons of other info w/ devices but not what I am loogin for...


Thanks and regards,
Timo

---

### Post by kidders on 2006-09-22
Hi there,

I doubt what you're asking is directly possible, in that creating copies of the device won't create copies of the actual data :-(

Provided all you want to do is read from the thing, you could try something like **cat /dev/video0 > /tmp/video_tmp** and direct your applications to the temporary file. How well that would work depends on exactly what you're doing with the video.

Your only alternative imo would be to set up some kind of streaming server, like you suggested. Ugh.

Hope that helps.

---

### Post by blazko on 2006-09-22
Rehi,

Okay, would have to test if applications like tvtime or XawTV could connect to the fifo, cause it has to work with other V4L tools.

Thanks for your reply, regards,
Timo

---

