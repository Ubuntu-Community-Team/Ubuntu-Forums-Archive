---
title: "Permission denied at lock screen for AD users"
date: 2016-05-04
forum: Desktop Environments
---

### Post by mrwboilers-6 on 2016-05-04
I've already asked this question over at askubuntu here: ([http://askubuntu.com/questions/767079/lockscreen-access-denied-ad-auth-via-sssd/767515#767515](http://askubuntu.com/questions/767079/lockscreen-access-denied-ad-auth-via-sssd/767515#767515)) So I apologize if it is against etiquette to re-post it here. 

On xenial, the lock screen doesn't work for me. Whether I enter the correct password or not, it won't let me in. However, if I click on the menu at the top right corner of the screen and choose "switch user," but choose the same user as at the lock screen it lets me right in.


At the lock screen, authentication seems to work correctly. It just doesn't authorize me. Here's what I see in /var/log/auth.log:


```
May  3 11:57:44 hostname compiz: pam_krb5(unity:auth): user myuser authenticated as myuser@MYDOMAIN.NET
May  3 11:57:44 hostname compiz: gkr-pam: unlocked login keyring
May  3 11:57:44 hostname compiz: pam_sss(unity:account): Access denied for user myuser: 6 (Permission denied)

```

Authentication is from an Active Directory domain. I'm using sssd. This same configuration works fine on Trusty, Vivid, and Wily. Only seems to be broken on Xenial. I've tried on a workstation that was upgraded from Wily, as well as a fresh install. I'm having a heck of a time figuring out what needs to be done differently.


Only AD accounts are affected by this. Local accounts are not.


It also fails when running something via the gui that requires elevated privileges. For example, when installing software from the Ubuntu Software Center. It won't let an AD account authorize installation, but it will allow a local user to authorize it. Yet from the command line, AD accounts can use sudo with no issues.


Something is making pam unhappy. Any idea what it could be?

On a test box, I tried switching to gdm3 instead of lightdm, but that won't even get me to a login screen. I just get a blank screen. I think there is a known bug with gdm and Nvidia drivers.

I've got a couple of other users in my office that want to upgrade to xenial, but I've told them to hold off until I get this figured out.

---

