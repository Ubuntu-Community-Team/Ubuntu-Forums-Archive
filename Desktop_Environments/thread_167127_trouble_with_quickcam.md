---
title: "trouble with quickcam"
date: 2006-04-27
forum: Desktop Environments
---

### Post by nosiad2 on 2006-04-27
hi, i was just wondering if any body culd help me diagnose or even resolve some trouble i've been having trying to get my logitech quickcam 8 to work. i have followed the tutorial at [https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam).. but that didn't help..
here is a run down on what i did and the problems i'm having:
i followed the tutorial at [https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam),
i ran the setup "lauchcam2" as the normal user at first but got a permissions error so i ran it again using sudo.
the set up atomatically detected my webcam and proceded ta download the kernel headers, after which it reported that the webcam instalation was successful.
i ran camorama and was greeted with this error:
"Could not connect to video device (/dev/video0). Please check connection"
i tried running the camorama using the "-d" option and "/dev/video1" and "/dev/video"...they both gave me the same error as before.
i read some problems other people were having with camorama but they reported success with gnomemeeting.. so i went about seting up my gnomemeeting to see if it would find my webcam..this resulted in "no video device found" error.
finally, amsn gives me the "you are firewalled or behind a router" error when i go into webcam configuration. if i proceed to click on "change video settings", it results in "Currently no devices are installed"...
Please help.. i am really only interested in getting the webcam to work in amsn.

thank you

---

### Post by Sef on 2006-05-01
This thread has some links that will help you.

[http://www.linuxquestions.org/questions//showthread.php?t=419827]("http://www.linuxquestions.org/questions//showthread.php?t=419827")

---

