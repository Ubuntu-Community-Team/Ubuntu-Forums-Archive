---
title: "load gui at boot"
date: 2019-04-19
forum: Desktop Environments
---

### Post by kiralysanyi on 2019-04-19
Hi All,
i am using Xubuntu and recently played with power management and part of this "play" i removed upower and pm-utils and as a result the laptop now boots to command line. After a login i can start x with startx without problem but it is uncomfortable for me. Can someone help me how could i get back my original boot process, automatically start x?

---

### Post by kiralysanyi on 2019-04-19
Ok i was able to repair it. Maybe it can help for someone in the future
 I don't know what really happened but the resolution in a nutshell was to install lightdm and configure it to autologin.
More detailed:
First i checked in /etc/X11 which is the default display manager. Gdm3 was. Then i tried to reconfigure but dpkg said it is not present so tried the same with lightdm with the same result. I don't know which was working originally because i never had to take care about it, it just worked fine.
I decided to install lightdm. After this i get back the gui login page but i still had to enter the password. After some research i found i have to copy the sample lightdm.conf file from /usr/share/doc/lightdm/lightdm.conf.gz to /etc/lightdm and under the [Seat:*] section uncommented these lines (i am not sure if all these are necessary to uncomment but now it just works fine.

[Seat:*]
pam-service=lightdm
pam-autologin-service=lightdm-autologin
pam-greeter-service=lightdm-greeter
autologin-user=undi
autologin-user-timeout=0

What is important that these lines can be found other sections as well but we need this section to be edited.

---

