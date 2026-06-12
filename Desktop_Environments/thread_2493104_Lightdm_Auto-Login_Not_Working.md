---
title: "Lightdm Auto-Login Not Working"
date: 2023-12-04
forum: Desktop Environments
---

### Post by spode2 on 2023-12-04
I have moved my Xubuntu 23.10 drive to a new motherboard with Radeon graphics, rather than Nvidia, and everything seems to be working as before apart from auto-login. I have uninstalled the Nvidia drivers with apt, although there are still traces left behind.

The auto-login appears to fail because pam_unix tries to log in the user lightdm to a greeter session instead of user xxx to a lightdm session. The login keyring has a blank password.

How can I fix this? I considered removing lightdm-gtk-greeter, but it looks as if the desktop might go with it.


journalctl -u lightdm shows:

systemd[1]: Starting lightdm.service - Light Display Manager...
systemd[1]: Started lightdm.service - Light Display Manager.
lightdm[1767]: pam_unix(lightdm-greeter:session): session opened for user lightdm(uid=114) by (uid=0)
lightdm[1767]: gkr-pam: couldn't unlock the login keyring.
lightdm[1767]: pam_env(lightdm-greeter:session): deprecated reading of user environment enabled
lightdm[1891]: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" was met by user "xxx"
lightdm[1891]: pam_unix(lightdm:session): session opened for user xxx(uid=1000) by (uid=0)
lightdm[1891]: gkr-pam: couldn't unlock the login keyring.
lightdm[1891]: pam_env(lightdm:session): deprecated reading of user environment enabled

---

### Post by spode2 on 2023-12-04
I am going to mark this as solved, with fingers crossed. I found two newly created files in /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf, and /50-xubuntu-numlock.conf
Commenting out the contents of these files appears to have cured the problem but, if anyone can tell me why, I would be grateful.

EDIT:Fix lasted for 3 reboots. Auto login failed on the fourth one with the same journalctl entries.

Working journalctl entries:

  systemd[1]: Starting lightdm.service - Light Display Manager...
systemd[1]: Started lightdm.service - Light Display Manager.
lightdm[1804]: pam_unix(lightdm-autologin:session): session opened for user xxx(uid=1000) by (uid=0)
lightdm[1804]: pam_env(lightdm-autologin:session): deprecated reading of user environment enabled
systemd[1]: Stopping lightdm.service - Light Display Manager...
systemd[1]: lightdm.service: Deactivated successfully.
systemd[1]: Stopped lightdm.service - Light Display Manager.
systemd[1]: lightdm.service: Consumed 16.674s CPU time.

---

### Post by Claus7 on 2023-12-05
Hello,

I cannot shed light to your issue: just some information that might be useful.

I remember tampering with lightdm and gmd3 some time ago. Installing gmd3, which was the new installment at the time, was asking me if I wanted to switch to that. Of course, if I was not content, I had the ability to revert back to lightdm. I do not know if xubuntu supports gmd3, yet I would try to switch to that first, remove ligthtdm, install it anew and make it the default.

Regards!

---

### Post by spode2 on 2023-12-06
Thanks for the reply, Claus7. I think I might have found the answer here: [https://askubuntu.com/questions/1360285/login-screen-issue-first-lightdm-needs-to-be-killed-to-get-x-session-to-work](https://askubuntu.com/questions/1360285/login-screen-issue-first-lightdm-needs-to-be-killed-to-get-x-session-to-work)

The fact that autologin occasionally worked pointed to some kind of startup race, and adding a file with the lines:
[LightDM]
logind-check-graphical=true

- seems to be the cure, and I think it has now proved reliable enough for me to mark this as solved.

---

### Post by Claus7 on 2023-12-07
Hello,

glad to hear that you found solution to your issue.

Regards!

---

