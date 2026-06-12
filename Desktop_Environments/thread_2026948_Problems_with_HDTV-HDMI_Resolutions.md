---
title: "Problems with HDTV-HDMI Resolutions"
date: 2012-07-16
forum: Desktop Environments
---

### Post by jgulisano117 on 2012-07-16
Hi Everyone, I have been around for a long time and have never had a problem with Ubuntu until now!

What seems to be something silly that I could probably fix if I looked harder is that I am using Ubuntu 12.04 and I recently upgraded to a 19" HDTV as a monitor. It works fine in the regards that I can use it on my Windows 7 machine, although I did have to go into nVidia control panel and manually resize the desktop and set it to 1366x768 at 1080i for it to display everything correctly. And since in my monitor settings I cannot change "Wide" "Standard", "Full" etc. because I am using an HDMI to DVI cable, nothing seems to work. I have tried setting a custom resolution in Ubuntu to 1366x768 and have tried Unity and LXDE but still, edges of my screen are cut off, I have tried GPU scaling.. basically everything that can be done, I have tried. If anyone has any better info for me, I would greatly appreciate it! Thanks :)

---

### Post by dorrellkc on 2012-07-16
I know that this does not fix the problem with your current graphics card,  but I just tried out an nvidia card over the weekend and ran into the same issue.  I was never able to actually fix the issue,  but discovered that an ati card did better at finding the correct resoloution after installing the fglrx driver.

---

### Post by jgulisano117 on 2012-07-16
It seems like its an overscan issue but I can't change overscan in the nvidia-settings or the monitor settings, and no matter what i use, other than 1024x768 (which looks absolutely awful on a 19" widescreen, mind you) display incorrectly. Also, I cant choose 1366x768 as an option, if there was a way I could set 1366x768 with a refresh rate of 30 then the monitor would be set in 1080i and would scan correctly, I wish i knew what to do...

---

### Post by jgulisano117 on 2012-07-16
Does anyone know of a way to "resize" like you can in Windows 7? it seems the only way to fix this issue. Ubuntu see's my TV as being about 50 pixels bigger than what I can actually see. Win7 has no problems when I throw it in 1920x1080 at 30Hz but for some reason when I put it at 1920x1080 by 30 Hz in Ubuntu, my TV "blue screens" and says "Not Supported". I am really at a loss here, besides the fact that you can't install newer nVidia drivers with X running, and when I close X to install the new ones almost everything in the terminal is cut off on the left side so I can't see what I'm doing. I am about to give up. anything 11.04 Ubuntu has had this problem and im not willing to jump back to 10.04/10.10 just to use it. It makes no sense to me and doesnt seem to have an end to it.

---

