---
title: "Inspiron 1525 Webcam"
date: 2008-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by J.T. on 2008-06-13
I set up my laptop as a dual boot. On Vista, the built-in camera works, but in Ubuntu, it isn't being recognized. Can anyone help? I really prefer Linux to Windows, so it would be nice to have everything working. 
Thanks, J.T.

---

### Post by linuxwizard on 2008-06-13
Have you tried using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If webcam does not work post the results of the command > lsusb

---

### Post by J.T. on 2008-06-13
It works with Ekiga, but it doesn't show up with Cheese.

---

### Post by linuxwizard on 2008-06-13
That's good to hear that your webcam does work in Ubuntu. I have only used Cheese 1 or 2 times never cared for it. You might want to try Camorama see if your webcam will work there.

---

### Post by J.T. on 2008-06-15
Camorama says "Could not connect to video device (/dv/video0) Please check connection".
Got any clues?

---

### Post by manishmahabir on 2008-10-27
same problem here too!
plz help.

---

### Post by linuxwizard on 2008-10-27
Camorama does not support v4l2. The Ubuntu forums are full of users asking what the "could not connect to video device (dev/video0)" error message means when they try to use Camorama. One reason is they're using a driver that requires v4l2.

---

