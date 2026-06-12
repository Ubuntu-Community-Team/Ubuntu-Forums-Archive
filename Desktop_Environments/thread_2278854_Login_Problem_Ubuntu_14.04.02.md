---
title: "Login Problem Ubuntu 14.04.02"
date: 2015-05-19
forum: Desktop Environments
---

### Post by Mago Nick on 2015-05-19
Hello everybody,
I am experiencing a weird problem on my Dell XPS L501x with Ubuntu 14.04.02. When I have to login in graphical mode, the unity greater bounces me back. After prompting my password the screen goes black and shows the nvidia logo and goes back to the greeter again.
I am not a complete noob (I believe) and I tried the following actions, restarting lightdm and the computer when needed:
[LIST]
[*]changed owner and permissions of .Xauthority (of course the owner was set to the proper user)
[*]deleted the file .Xauthority
[*]deleted the .config/monitors.xml file (I thought I might be caused by some conflict of configurations for external monitors)
[*]removed the /etc/X11/xorg.conf and generated a new one using nvidia-xconf
[*]copied /etc/X11/xorg.conf.failsafe as /etc/X11/xorg.conf
[*]reset unity configurations using  ```
unity-tweak-tool --reset-unity
```
[*]I have tried to login with the previous kernel from GRUB, but I was unable to login. NOTE: is a "fresh" install I have only two kernel modules 3.13.0-49 and 3.13.0-32
[*]I tried to start ubuntu using the recovery mode option and starting the failsafe graphic mode, did not work
[/LIST]
I noticed that this happened when trying to login in after using my laptop in a multimonitor setup.
I ran out of ideas, any clue?
Thank you very much
Andrea

---

