---
title: "gdm stopped working"
date: 2005-10-30
forum: Desktop Environments
---

### Post by infiltrado on 2005-10-30
Hello
gdm has been working with no problems since I installed breezy, until today: the nvidia logo appeared as usual but then the console login appeared instead of gdm. I logged in and typed startx: gnome runs ok, and Xorg log doesn't seem to have any error. In /var/log/daemon.log I saw the following:

Oct 30 20:18:08 localhost hcid[7990]: Bluetooth HCI daemon
Oct 30 20:18:08 localhost sdpd[7996]: Bluetooth SDP daemon 
Oct 30 20:18:10 localhost gdm[8118]: gdm_slave_greeter: Cannot start greeter trying default: /usr/lib/gdm/gdmlogin
Oct 30 20:18:10 localhost gdm[8118]: failsafe dialog failed (inhibitions: 0 0)
Oct 30 20:18:10 localhost gdm[8118]: failsafe dialog failed (inhibitions: 0 1)
Oct 30 20:18:10 localhost gdm[8118]: failsafe dialog failed (inhibitions: 1 1)
Oct 30 20:18:10 localhost gdm[8118]: gdm_slave_greeter: Error starting greeter on display :0
Oct 30 20:18:10 localhost gdm[7706]: gdm_child_action: Se aborta la pantalla :0

The lastest changes I remember making in my system were upgrading libgda2-3 and sudo, but i did not touch anything related with gdm.
I have reinstalled gdm but that did not work.

Anyone could help me or give any other idea to try?

Thanks

---

