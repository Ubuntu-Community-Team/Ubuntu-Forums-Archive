---
title: "dpkg --config"
date: 2008-11-12
forum: Desktop Environments
---

### Post by raunhar on 2008-11-12
I updated Ubuntu 8.04 through Update manager. Only the reqd. files were updated and not Ubuntu (to 8.10)

After that I changed the user password.

After that, I am unable to open Add/ remove application or synaptic Manager

I am getting the screen to manually run dpkg --configure -a  
But when I try to run this command through terminal, it says that only administrator can do it.

Please help

---

### Post by Steve1961 on 2008-11-12
sudo dpkg --configure -a

---

### Post by raunhar on 2008-11-12
Thanks.
It worked

---

