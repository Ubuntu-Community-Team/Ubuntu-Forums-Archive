---
title: "Sharing home folder"
date: 2009-01-01
forum: General Help
---

### Post by fm1234 on 2009-01-01
Hi,
Have two 8.10 desktops sharing users home folders and I have a third with 8.04 which I would like also to access the network home shares. The question is: are the configuration files in the users homes compatible from 8.10 to 8.04?

BTW, before you suggest, the reason I haven't upgraded the machine from 8.04 to 8.10 is performance. This computer is an old Celeron which runs ok with 8.04 but is visibly slower with 8.10.

---

### Post by dcstar on 2009-01-01
> **fm1234 said:**
> Hi,
Have two 8.10 desktops sharing users home folders and I have a third with 8.04 which I would like also to access the network home shares. The question is: are the configuration files in the users homes compatible from 8.10 to 8.04?
........

Doubtful, the Gnome configuration files in the later version are usually not compatible with the previous version (in my experience). Once a new version runs on a /home directory and does any format upgrades/additions, then you usually have big problems trying to use the old version on it.

It *can* (sort of) work with the same Ubuntu version used across all systems, but not between versions.

---

### Post by fm1234 on 2009-01-02
Thanks, that's what I suspected. What about a login startup script to move files/folders around? 

Which problems have you encountered while sharing the same version?

---

