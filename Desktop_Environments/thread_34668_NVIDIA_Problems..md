---
title: "NVIDIA Problems."
date: 2005-05-15
forum: Desktop Environments
---

### Post by Tseug on 2005-05-15
Hey, just installed Kubuntu after using Ubuntu for a few months. Got everything set up how it was with gnome, and installed UT2004. Seems as though anything that uses the video card to draw gets really laggy. I dont/can't remember exactly how to tweak my xorg.conf for nvidia, but any tips would be appreciated. thanks.

---

### Post by Narg on 2005-05-15
Are you using the nvidia instead of mesa drivers?

Are you using the RenderAccel option?

etc. Memby post xorg.con?

---

### Post by crane on 2005-05-15
[QUOTE=Tseug]Hey, just installed Kubuntu after using Ubuntu for a few months. Got everything set up how it was with gnome, and installed UT2004. Seems as though anything that uses the video card to draw gets really laggy. I dont/can't remember exactly how to tweak my xorg.conf for nvidia, but any tips would be appreciated. thanks.[/QUOTE]

You shouldn't have to really tweak it. How did you install th envidia driver? apt? nvidia website?
I guess you should start off by making sure you xorg.conf has the driver set to nvidia not nv (assuming the drive is installed.

---

### Post by Tseug on 2005-05-15
xorg.conf has nvidia instead of nv. i used sudo apt-get install nvidia-glx to get it. Dont know where to go from here. Still laggy as hell.

---

### Post by Terracotta on 2005-05-16
This did the trick for me:
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

I hope you get it working.

---

### Post by Tseug on 2005-05-16
Terracotta, you rule :D :D :D That fixed it. THANKS  \\:D/  \\:D/  \\:D/

---

### Post by agsansoo on 2005-05-18
I can't get glx to run at all ...!

The only way I can get nvidia drivers to load is to comment out glx in my /etc/X11/xorg.conf file.

I'm using 2.6.10-5-amd64-k8 with the 7174 nvidia module.

If I load the glx module, X will not start !

any ideas ?

---

### Post by z-vet on 2005-05-18
GLX seems to conflict with composite extension. I found it yesterday in /var/lib/Xorg.0.log. So i just disabled composite, everything works now.

---

### Post by Terracotta on 2005-05-19
[QUOTE=Tseug]Terracotta, you rule :D :D :D That fixed it. THANKS  \\:D/  \\:D/  \\:D/[/QUOTE]
Hehe, I know :p, lol no, I've read it somewhere on this forum, and I use it since then so  the tx goes to someone else (forgot his nick :???: ...).  'bout the composite thing: it crashes on startup when I have transparencies enabled, and now (off topic) my internet connection doesn't seem to work (this problem came up when I installed guarddog, so I threw it off my pc, but during install of guarddog I had to install one other package, can anyone tell me which one it was so I can throw that off of my pc as well???) I had a clean kubuntu-desktop install.

---

