---
title: "Boot to CLI, not X"
date: 2005-04-23
forum: Desktop Environments
---

### Post by neilthemonster on 2005-04-23
HI all

I would like my laptop to boot to a CLI rather than straight into X. . .

Googling indicates that I can edit /etc/inittab to change it, but the information I have says the default id for X is 5 and CLI is 3.

/etc/inittab on my Warty installation says default id is 2.

What id do I need to boot to CLI, please?

Many thanks

Neil

---

### Post by nad on 2005-04-23
There is no need to play with inittab. The default Debian runlevel for X is 2. However, ubuntu starts an X server in /etc/rcS.d.

All system services are started by shell scripts. The location for these startup scripts is /etc/init.d. The runlevel specific directories (rc?.d) are composed of numbered links to the actual shell scripts so that they can be called in a particular order.

I do not have a warty install online at the moment, however, hoary shows /etc/rcS.d/S70xorg-common followed by the sudo script as the final two. Simply remove the links that you wish and the service will not be started. To start the script from the command line, issue ' /etc/init.d/xorg-common start '.

Dan M

Dan M

---

### Post by nad on 2005-04-23
Sorry for the bad form in replying to my own post, but I'm even sorrier about my bad advice.

Upon reviewing my answer, I realized that the X server is actually started by gdm which is so early in the init scripts, I didn't notice it. Xorg-common starts the services necessary for X. As the display manager is in a non-standard location in ubuntu, I am going to have to research this. If you have already applied my earlier advice, please post your results. I will duck any flying debris.

In the past the display manager was always the last service started. Even now I can apply a gnome or kde desktop to a straight debian install and start the X server last. This way I can choose which desktop I wish to use by editing my .xsession script. This is not available in ubuntu and is what clued me in to my error. These full fledged desktop environments are something new to me. I am not sure of the ubuntu method and will take a look. The server install for ubuntu will be one of my first resources as will removing the gdm script in a test install.

Dan M

---

### Post by neilthemonster on 2005-04-24
Thanks for letting me know, Dan.

This n00b needs all the help he can get!

Regards

Neil

---

