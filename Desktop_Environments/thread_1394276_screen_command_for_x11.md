---
title: "screen command for x11?"
date: 2010-01-30
forum: Desktop Environments
---

### Post by SSzretter on 2010-01-30
Is it possible to have an x11 app running in a virtual screen like with the screen command?

I have an x app that I want to leave running, the machine it is running on does not have x, it is cli only.

I ssh -Y connect in to it and run the x app remotely.

But I want to be able to close the client side down and leave the app running and re-connect to it later.  Just like with the screen command for cli apps.

Is this possible?

---

### Post by falconindy on 2010-01-30
To leave the application running on the remote side, the server is going to need to have X running. There's no way around that. What you can avoid is having to deal with a "real" video output device through the usage of xvfb (virtual framebuffer). Once this is setup, you can use screen on the remote side to start the app on the DISPLAY created by X on the xvfb and then log out, leaving the screen session open.

---

