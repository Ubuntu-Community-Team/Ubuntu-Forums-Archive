---
title: "xubuntu 12.04 - change default desktop environment?"
date: 2012-08-27
forum: Desktop Environments
---

### Post by irishetalon007 on 2012-08-27
Running Xubuntu 12.04 32-bit.

for T's and G's, I recently tried out the "xfce session" as opposed to the default "xubuntu session," chosen from login screen.

However, now I can't change the default back to "xubuntu session"! 

Someone please help this is a serious first world struggle!

I tried editing .dmrc in $HOME, but that didn't do anything. And even when I open a session using "xubuntu session," after reboot it's back to defaulting to "xfce session."


Thanks for you rhelp!

---

### Post by Toz on 2012-08-27
Have a look at your /etc/lightdm/lightdm.conf file. Do you have an entry there like:
> user-session=xfce

If so, try changing it to:
```
user-session=xubuntu
```

You'll need to restart lightdm (or reboot) for it to take effect.

---

### Post by irishetalon007 on 2012-08-28
Thanks for your reply.

The lightdm.conf file is already in the format you specified, i.e. user-session=xubuntu.

I should mention that all other users on the computer still default to xubuntu session, and it is only the username that tried out using "xfce session" that can't revert its default desktop session to "xubuntu session."

Because of the above conditions, I'm assuming the configuration file is somewhere in my home directory, I just don't know what it is!

---

### Post by Toz on 2012-08-28
Oh I see. I don't think ~/.dmrc is being used anymore (see: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/823718]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/823718"))

Have a look at the /var/lib/AccountsService/users directory. I believe the default session information is stored there now.

---

### Post by irishetalon007 on 2012-09-04
FIXED! Thank you Toz!

---

