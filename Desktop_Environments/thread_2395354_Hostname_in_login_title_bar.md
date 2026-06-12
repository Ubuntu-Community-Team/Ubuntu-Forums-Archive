---
title: "Hostname in login title bar"
date: 2018-06-30
forum: Desktop Environments
---

### Post by lvanhelden on 2018-06-30
I have just installed Ubuntu 18.04 on a number of workstations, which I switch between using a KVM switch.  Currently on the (graphical) login screen there is no way to identify which workstation I am connected to, other than looking on the KVM switch, or logging in and finding the hostname.  Is there a way to display the hostname in the title bar (or somewhere else on screen) so it displays before logging into the workstation?

---

### Post by deadflowr on 2018-06-30
You can try adding it as a banner message:
[https://help.gnome.org/admin/system-admin-guide/stable/login-banner.html.en]("https://help.gnome.org/admin/system-admin-guide/stable/login-banner.html.en")
or do away with gdm and use lightdm which can set the hostname easier (I think both unity-greeter and lightdm-gtk-greeter set it as the default)
[https://askubuntu.com/questions/139491/how-to-change-from-gdm-to-lightdm]("https://askubuntu.com/questions/139491/how-to-change-from-gdm-to-lightdm")

---

### Post by lvanhelden on 2018-06-30
I'm already stuck with the banner method (no idea how to create a dconf database), so I guess I'll opt for the lightdm option.

Edit: ... and the lightdm option works like a charm.  Thanks for your help!

---

