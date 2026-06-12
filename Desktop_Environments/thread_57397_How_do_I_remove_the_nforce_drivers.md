---
title: "How do I remove the nforce drivers?"
date: 2005-08-16
forum: Desktop Environments
---

### Post by zeuz on 2005-08-16
Well, I installed nvidias nforce2 drivers (don't ask me why, everything was working :p) and now i can't use any videoplayer. How can I remove the nforce2 audio drivers?

---

### Post by littlepr on 2005-08-16
did you install/self compile or did you use synaptic? If you used synaptic, start it up and search for nvidias or nforce and if it's green then it's installed. Right click and select to uninstall. If you used a .deb package then run this command as root:

dpkg -r package_name.deb


For more about installing and removing read this page:

[http://www.deeproot.co.in/community/documentation/howtos/installing_upgrading_and_removing_software_on_linux](http://www.deeproot.co.in/community/documentation/howtos/installing_upgrading_and_removing_software_on_linux)

---

### Post by mo_x on 2005-08-16
> sudo sh NFORCE-Linux-x86-1.0-0301-pkg1.run --uninstall
If you used the nvidia installer.

---

### Post by zeuz on 2005-08-16
When running:
> sudo sh NFORCE-Linux-x86-1.0-0301-pkg1.run --uninstall 

I get this message: 

> There is no NVIDIA  driver currently installed.

One thing that would be better is to solve the video problem, because some things works better than with alsa now. It probably don't have anything to do with the driver but what the heck. I can play music and still have sound on embedded videos in firefox, play enemy territory with sound and so on...

When trying to watch a video in vlc it hangs or  everything hangs so that I have to reset the computer. Totem doesn't even start, "Resource busy or not available.".

---

