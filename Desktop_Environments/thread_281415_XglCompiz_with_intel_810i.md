---
title: "Xgl/Compiz with intel 810i"
date: 2006-10-21
forum: Desktop Environments
---

### Post by ittiam on 2006-10-21
Hi,

I am trying to install Xgl/Compiz with intel 810i.

I did the following

apt-get install xserver-xgl compiz compiz-gnome compiz-plugins compiz-core csm

but it said csm is obsolete or missing.

Hence i first installed xserver-xgl and downloaded a seperate deb for csm and it said compiz-plugins is missing. when i installed compiz-plugins it says csm is missing. when i gave dpkg -i csm-something.deb and compiz-plugins-something.deb it worked fine. then the other steps went through fine.

I have the following .Xsession file in my home directory
#!/bin/sh
Xgl -fullscreen :1 -audit 0 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 2 && DISPLAY=:1 gnome-session
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME
exec gnome-session

After doing this i logged out and logged back in by changing the session to xgl (the checked screen appeared). And nothing happens...no xgl effects..but i can notice my comp's performance has gone down. When i log into a gnome session it performs far better.

Anyone has any ideas? Atleast does an interl 810i suppor it?

lspci | grep VGA
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)

grep Driver /etc/X11/xorg.conf
        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "i810"


These are the details i can give? Has anyone got any suggestion?

---

### Post by ayoli on 2006-10-21
> but it said csm is obsolete or missing.
csm was a part of compiz-quinn which has now forked to beryl, so now csm is beryl-settings, cgwd is emerald, compiz is beryl.
[how to's here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu")
Since you have an i810 chip i recommend you aiglx instead of xgl (better performance and easier if you're on edgy aiglx is in xorg 7.1 and doesn't suppose any packages install)[URL="http://forum.beryl-project.org/topic-4831-howto-beryl-edgy-for-intel-embedded-graphics"]
how to here[/URL]

---

