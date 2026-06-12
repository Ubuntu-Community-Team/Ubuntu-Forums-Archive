---
title: "Terminal Download"
date: 2009-03-04
forum: General Help
---

### Post by ExplicitViper on 2009-03-04
if the Terminal is downloading something... and i close it... does it do like the Packet Manager and save where it left off? or.... does it erase EVERYTHING its done?

---

### Post by SuperSonic4 on 2009-03-04
If you used wget it will be in the directory you started the download from. cd to the directory you started the download in and do ```
wget -c 'same_url'
``` -c = continue

---

### Post by ExplicitViper on 2009-03-04
i used the code

apt-get update && apt-get upgrade

to get what im downloading..

---

### Post by liamnixon on 2009-03-04
I don't believe the package manager will save its progress.  You have to start it over if you close the terminal window.
                                                                                          ^                         ^   
                                                                                          |                         |
                                                                                                    EDIT

---

### Post by SuperSonic4 on 2009-03-05
I think it depends if you rebooted or not.

```
sudo dpkg --configure -a
``` might work if you closed it without quitting

---

