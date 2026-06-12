---
title: "Command to get firestarter working"
date: 2009-06-14
forum: General Help
---

### Post by taytayflyfly on 2009-06-14
I have been having problems with getting firestarter to work and allow my xbox 360 to connect. That, however, is another issue. 
previously, I had a command saved that, when run, would select an ip as the eth0 connect. It was something eth0 <IP> but I cannot recall it, or find it anywhere.

When I try to start firestarter now, it says that "eth0" device is not ready. eth0 is not my internet connection, but I need it to work because it runs to a router, which runs to the xbox.

Thanks

---

### Post by lovinglinux on 2009-06-14
Firestarter is not recommended anymore. You should try [gufw](apt:gufw) [apt-get] instead. Gufw is the gui for UFW (Uncomplicated Firewall), which is installed by default.

---

### Post by taytayflyfly on 2009-06-14
> **lovinglinux said:**
> Firestarter is not recommended anymore. You should try [gufw]("apt:gufw") [apt-get] instead. Gufw is the gui for UFW (Uncomplicated Firewall), which is installed by default.
Thanks for that, that seems a lot easier than firestarter, but I have not found anything online that suggests this application can enable internet connection sharing, which is what I need.

---

