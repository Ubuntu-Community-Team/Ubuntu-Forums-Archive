---
title: "How To Make New KWallet Integration with PAM Work?"
date: 2014-05-01
forum: Desktop Environments
---

### Post by buzzingrobot on 2014-05-01
KWallet in Kubuntu 14.04 is said to be integrated with PAM. ([https://bugs.launchpad.net/ubuntu/+source/pam-kwallet/+bug/1305307](https://bugs.launchpad.net/ubuntu/+source/pam-kwallet/+bug/1305307); [http://packages.ubuntu.com/trusty/pam-kwallet](http://packages.ubuntu.com/trusty/pam-kwallet))  If the wallet's password and the user's login password are the same, this, I gather, is supposed to stop  KWallet from hounding you with incessant password requests.

Here, my Kwallet password and my log in password are identical. KMail, though, prompts for a KWallet password every time it is launched after a new log in.

Has anyone come across any guidance about making this PAM-KWallet integration work?

---

### Post by alexball on 2014-05-06
I am struggling with the same issue myself. I recently upgraded three of my machines to Kubuntu 14.04: a desktop, a laptop and a notebook. The desktop and laptop (both relatively new/powerful machines) have both stopped asking me for a password to open KWallet, but my notebook (old, slow to boot) still asks for it. I notice it is always an Akonadi resource that prompts the dialog box (not, say, kde-telepathy).

I am trying to work out why it isn't working for the netbook. I can't see any relevant differences in the packages installed. Looking at the Authentication Log, the messages from pam_kwallet are the same for both the laptop and the netbook. One thing that is different, though, is that on the laptop (where it works), there is a sequence of lines:

```
lightdm - pam_kwallet(lightdm:setcred): pam_sm_setsecred
lightdm - pam_unix(lightdm:session): session opened for user <me> by (uid=0)
systemd-logind - Removed session c1
systemd-logind - New session c2 of user <me>.
systemd-logind - Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display
lightdm - pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
```

while for the netbook (where it doesn't) the systemd-logind lines are missing. I have no idea if that is relevant.

The only other thing I can think of is that on the netbook, the boot is so slow that something 'times out' or happens in the wrong order so that KWallet doesn't open in a timely fashion.

Any suggestions from someone with more of a clue would be most appreciated.

---

