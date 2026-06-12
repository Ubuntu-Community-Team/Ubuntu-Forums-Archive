---
title: "Remote Assistance"
date: 2010-09-19
forum: Desktop Environments
---

### Post by Geffers on 2010-09-19
What is the best way a Linux user can offer remote assistance to someone who may not be confident enough to alter their own router to allow for firewalls etc.

I have used ultravnc in the past, it has a utility named sc (single click) which is a small server that automatically connects to a specific IP address.

Worked great but it is windows based so not sure if it'd work with a mixed Linux/Windows system.

Any comments appreciated.

Geffers

---

### Post by cutekazuya on 2010-09-20
> **Geffers said:**
> What is the best way a Linux user can offer remote assistance to someone who may not be confident enough to alter their own router to allow for firewalls etc.

I have used ultravnc in the past, it has a utility named sc (single click) which is a small server that automatically connects to a specific IP address.

Worked great but it is windows based so not sure if it'd work with a mixed Linux/Windows system.

Any comments appreciated.

Geffers

Ultra VNC single click works with "SSL/SSH VNC Viewer" found in software centre. I could not get any other vnc client to work with UVNC SC.

---

### Post by dirty_harry on 2010-09-20
I find Gitso (a google-host open source package) very interesting. Haven't tried it yet, but I will probably test this week... 

Also it is more for remote assistance as for remote administration -> reverse VNC, cross platform
Maybe what you're looking for?

[https://code.google.com/p/gitso/](https://code.google.com/p/gitso/)

They even want to get it into the  Ubuntu repository:
[https://bugs.launchpad.net/ubuntu/+bug/319444](https://bugs.launchpad.net/ubuntu/+bug/319444)

---

### Post by Geffers on 2010-09-28
> **dirty_harry said:**
> I find Gitso (a google-host open source package) very interesting. Haven't tried it yet, but I will probably test this week... 

Also it is more for remote assistance as for remote administration -> reverse VNC, cross platform
Maybe what you're looking for?

[https://code.google.com/p/gitso/](https://code.google.com/p/gitso/)

They even want to get it into the  Ubuntu repository:
[https://bugs.launchpad.net/ubuntu/+bug/319444](https://bugs.launchpad.net/ubuntu/+bug/319444)

Thanks for suggestion. Tried it on a local network.

First connection fine, second attempt local machine could not control remote machine :(

Will keep experimenting.

Geffers

---

### Post by Geffers on 2010-09-28
> **cutekazuya said:**
> Ultra VNC single click works with "SSL/SSH VNC Viewer" found in software centre. I could not get any other vnc client to work with UVNC SC.

Downloaded and going to try it.

Geffers

---

