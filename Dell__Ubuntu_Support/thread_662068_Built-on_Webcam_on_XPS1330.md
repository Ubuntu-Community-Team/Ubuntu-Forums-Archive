---
title: "Built-on Webcam on XPS1330"
date: 2008-01-08
forum: Dell  Ubuntu Support
---

### Post by Fascination on 2008-01-08
Hi there,

Got a common issue which the usual resolutions dont appear to be solving. I recently purchased a Dell XPS M1330 with built-in webcam (using standard display, with onboard graphics) and I installed Gutsy onto it.
After installing the gspca and v4l/v4l2 sources and Camorama, I still cant get it to see the camera as being there. Instead, the light next to the camera flashes blue and I recieve the message:

Could not connect to video device (/dev/video0).
Please check connection.

Has anyone encountered issues on a similar setup (and had success)? :)

Many regards,

Fasc

---

### Post by FrankVdb on 2008-01-10
Got one too. This machine rocks.

V4L doesn't work, you have to use V4L2 for the webcam. 


See also:
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)

---

### Post by chips24 on 2008-01-10
you should try experimentingwith ekiga, thats how i got my build in camera working...

---

### Post by Fascination on 2008-01-20
Turns out that Camorama doesn't support V4L2 so even though I had everything I needed it wouldn't work. Soon as I tried Eikga or Cheese it worked perfectly. :)
Thanks for your responses though. :)

---

