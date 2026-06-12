---
title: "Gnome Is Dead"
date: 2007-06-15
forum: Desktop Environments
---

### Post by ipv9 on 2007-06-15
I decided to install edgy, beryl and some other apps on an old windows box. 

Here are the specs:
P4 2.6 HT
1GB RAM
120 GB HDD
GeForce 6200 128 MB

After getting everything up and running, I decieded to install a few auto updates after adding a few new repositories and running 'sudo apt-get update'.  After I rebooted, my desktop will not start.  I've installed OpenSSH, so I can get to the box from another machine on my home LAN using putty and WinSCP.

I've attached my Xorg.0.log and xorg.conf files for all to review.  

I would greatly appreciate it if somone could help me out with this.

---

### Post by danhm on 2007-06-15
According to your Xorg log file, it looks like you don't have nvidia drivers installed. Try:

```

sudo aptitude install nvidia-glx
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

And then reboot.

---

### Post by Gannin on 2007-06-15
Are you using the nVidia drivers from the repository, or the ones from the nVidia website?

---

