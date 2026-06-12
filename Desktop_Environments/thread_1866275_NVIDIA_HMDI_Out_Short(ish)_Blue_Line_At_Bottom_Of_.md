---
title: "NVIDIA HMDI Out Short(ish) Blue Line At Bottom Of Screen Problem"
date: 2011-10-21
forum: Desktop Environments
---

### Post by Scully on 2011-10-21
Hello

I'm having a problem with Ubuntu 11.10 (x64) on my Acer Revo 3700 (NVIDIA ION 2 graphics). There is a thin blue line at the very bottom left corner which is about 90% the length of the recycle bin when hooked up to my 32inch Hannspree JT01-32E2-000 TV via HDMI. This blue line does not appear in screenshots and does not occur when the Revo is connected via a VGA cable. The blue line does not appear when Ubuntu runs from the Live edition on a USB drive. It does not appear while booting up from the main installation until the login screen appears (I guess this is when the full NVIDIA driver takes over). 

The NVIDIA (closed source) driver is being used and I'm guessing with what I've said above, this is causing the problem. I've updated the driver to a later version available, but the problem persists. While running xrandr with the NVIDIA driver, it claims available refresh rates (at 720P, it's not a full HDMI TV) are 50, 51 and 52 - with 50 being the one used (though, setting the refresh to any of the others doesn't fix the problem - which was tried in desperation). However, when I run the same command when Ubuntu is running from the Live USB edition (not using the official NVIDIA drivers), it claims it's running at 60Hz (though setting this value in the X config and restarting prevents Ubuntu from starting up).

This short blue line is driving me nuts and any help getting rid of it will be very much appreciated!

Thanks
Aaron

---

### Post by Scully on 2011-11-09
Don't know whether this response will help anyone else, but I had the same problem using Windows, with the NVIDIA driver. The latest Windows driver just released by NVIDIA have fixed this issue ([http://us.download.nvidia.com/Windows/285.62/285.62-desktop-win7-winvista-64bit-english-whql.exe](http://us.download.nvidia.com/Windows/285.62/285.62-desktop-win7-winvista-64bit-english-whql.exe) for anyone with Windows 7 x64) so hopefully they'll roll that fix into their Linux drivers too.

---

