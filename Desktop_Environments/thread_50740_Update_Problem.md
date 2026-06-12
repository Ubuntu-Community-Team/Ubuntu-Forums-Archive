---
title: "Update Problem"
date: 2005-07-21
forum: Desktop Environments
---

### Post by wxm505 on 2005-07-21
I used Synaptic package manager to update the system.
After I opened Synaptic, there were two windows jumped up,

One is :

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

The other is:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

Then I tried to use sudo apt-get update

same error message:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

Any help? Thanks a lot

---

### Post by wxm505 on 2005-07-21
Servers were down. It was the reason that caused the problem.

---

### Post by Mr Frosti on 2005-07-21
You can only have one invocation of "apt-get" at a time. If you were trying to enter ```
sudo apt-get update
```, while Synaptic was open, it will not be able to "lock" the upgrade, and you will see the error 

"E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory"

I think a combination of the server being down and multiple instances caused your problems.

---

### Post by wxm505 on 2005-07-21
I did not do them together. I did them individually.
Aftet about two hours. I tried it again, everything
was going well.
thanks anyway

---

