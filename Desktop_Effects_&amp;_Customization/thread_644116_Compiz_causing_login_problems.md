---
title: "Compiz causing login problems"
date: 2007-12-18
forum: Desktop Effects &amp; Customization
---

### Post by ekimnarfnas on 2007-12-18
I've had login trouble ever since trying to install Compiz. I get a normal login and password prompt but after entering the correct information my system sits with a white screen and mouse pointer for a few minutes and then reboots, starting the whole process over..and over..and over. I've removed Compiz using Synaptic but the problem persists.

I get around this by using failsafe GNOME as my session but I'd like to avoid this additional step. After logging in in failsafe mode I get a warning that this session can be used to alter the initialization files (or something similar). Which files would I change and how would I change them.

Thanks,
Mike

---

### Post by overdrank on 2007-12-18
> **ekimnarfnas said:**
> I've had login trouble ever since trying to install Compiz. I get a normal login and password prompt but after entering the correct information my system sits with a white screen and mouse pointer for a few minutes and then reboots, starting the whole process over..and over..and over. I've removed Compiz using Synaptic but the problem persists.

I get around this by using failsafe GNOME as my session but I'd like to avoid this additional step. After logging in in failsafe mode I get a warning that this session can be used to alter the initialization files (or something similar). Which files would I change and how would I change them.

Thanks,
Mike

Hi, you can try and reconfigure your xorg with this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then rest x with the ctrl, alt, backspace keys all at the same time. hope this help and good luck.
P.S. It states in your profile that you are using 5.04 is this correct?:)

---

### Post by ekimnarfnas on 2007-12-19
Hi Overdrank,

Yes, I believe I'm using Ubuntu 5.04.

I tried the dpkg-reconfigure command and reset with control,alt.backspace but it hasn't corrected the problem. Additionally, I need to type "metacity --replace" to get the desktop back to normal, although this started after I used Synaptic to remove all Compiz packages and before I used the dpkg-reconfigure that you recommended. I can't move my Firefox browser window around until I use the metacity command. The browser sticks under the top margin...kind of like the top margin on a Mac.

Any other ideas - short of reloading the whole thing.

---

### Post by noisebug on 2007-12-19
You are suffering from the white cube. Your computer is actually running, but if you have compiz installed nothing will render correctly, only white in its place. 

Try hitting ALT-F2 and typing "compiz --replace". This won't solve the problem, but might make your desktop visible so you can work on it.
When you hit ALT-F2, nothing will happen, so just type blindly.

I also have a thread started here:
[http://ubuntuforums.org/showthread.php?t=644534&highlight=white+cube](http://ubuntuforums.org/showthread.php?t=644534&highlight=white+cube)

---

### Post by ekimnarfnas on 2007-12-20
Thanks Noisebug,

I've done several things - all of which have made things worse. I think I'm going to just wipe my HD clean and reload everything. I have been using 5.04 which I got at the local Linux Convention a couple of years ago. It's a bit old by now.  Maybe there is some incompatibility between Compiz and earlier versions of Ubuntu. I've downloaded 7.10 for the AMD-64 and will start anew after X-mas.

Thanks for everyone's help!

---

