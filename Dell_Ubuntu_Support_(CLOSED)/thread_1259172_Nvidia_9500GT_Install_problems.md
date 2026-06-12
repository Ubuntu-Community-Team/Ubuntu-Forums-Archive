---
title: "Nvidia 9500GT Install problems"
date: 2009-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by akrobert on 2009-09-06
Hello
I just installed an Nvidia 9500GT Graphics card in the PCI Express slot. I have it up and running on my primary screen but cannot get the second screen on unless I use Truview which I dont like.

When I try to set it up as a seperate X Screen it gives me the following error.

> The current settings cannot be completely applied due to one or more of the following reasons

The Location of an X screen has changed
The location type of an x screen has changed
the color depth of an x screen has changed
An x screen has been added or removed
Xinerama is being enabled/disabled

For all the requested settings to take effect, you must save the configuration to the x config file and restart the x server.

I have an apply what is possible and a cancel

If I hit apply whats possible it does nothing. If I try to hit save to x configuration file it says

> 
Unable to create new X config backup file '/etc/X11/Xorg.config.backup'

I have a Dell 530 that I purchased preloaded with Ubuntu 8.04
Im running Ubuntu 9.04 now. Kernel 2.6.28-15 and Gnome 2.26.1

I have tried enabling the proprietary drivers and installed the nvidia drivers via the Synaptic package manager. 

What do I need to do to get the second monitor up and running?

thanks for the help

Robert

---

### Post by RedRat on 2009-09-06
The quote:
"Unable to create new X config backup file '/etc/X11/Xorg.config.backup' 			 		"
seems to indicate that you are not running the program with admin privileges or as root. In order to write xorg.config.backup you need to run as root.

Is this in nvidia-settings? If so, try running it with:
gksudo nvidia-settings
or 
sudo nvidia-settings

.

---

### Post by akrobert on 2009-09-06
Thanks for the answer.
Your right I wasnt doing it in admin...when I went in as an admin I did let me save the changes without the error but still throws up the same error that I listed at the top..do you have any ideas what Im doing wrong?

thanks

Robert

---

### Post by RedRat on 2009-09-06
> **akrobert said:**
> Thanks for the answer.
Your right I wasnt doing it in admin...when I went in as an admin I did let me save the changes without the error but still throws up the same error that I listed at the top..do you have any ideas what Im doing wrong?

thanks

Robert
Robert,
I have never done this. But when I run nvidia-settings, there is a provision for another monitor attached. I believ it must be plugged into the card and should be seen in nvidia-settings. However, this is something I have never done so I would rely on help from others who have done this. I don't want to mislead you down a path that blows your video. It seems tenuous in Linux at best.

---

