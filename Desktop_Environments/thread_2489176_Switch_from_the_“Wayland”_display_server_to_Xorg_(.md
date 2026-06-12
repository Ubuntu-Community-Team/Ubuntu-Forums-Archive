---
title: "Switch from the “Wayland” display server to Xorg (X11) on Linux Ubuntu 22.04.2 LTS"
date: 2023-07-21
forum: Desktop Environments
---

### Post by zhaohscas on 2023-07-21
I'm using Ubuntu 22.04.2 LTS as shown below:

```shell
werner@X10DAi:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.2 LTS
Release:	22.04
Codename:	jammy
```
Now, I try to switch from the “Wayland” display server to Xorg (X11) with the following steps:

1. $ sudo nano /etc/gdm3/custom.conf

```
# Uncomment the line below to force the login screen to use Xorg
WaylandEnable=false
```
2. Restart gdm3:

`$ sudo systemctl restart gdm3`

But the above method will finally give me a very poor color contrast for desktop and login background display, as shown below:

[IMG]https://discourse-gnome-org-uploads.s3.dualstack.us-east-2.amazonaws.com/original/2X/7/76e373c4c4e166854102577fafeb73a9da715c5c.jpeg[/IMG]

How to solve this problem?

Regards,
Zhao

---

### Post by Bashing-om on 2023-07-21
zhaohscas - Oh boy

At the log in screen in the lower right corner is a gear icon.
Here when selected one may change the Desktop Environment.

[INDENT]m bit to try and help[/INDENT]

---

### Post by zhaohscas on 2023-07-21
I want to use Xorg (X11) but with nice color/background settings.

---

