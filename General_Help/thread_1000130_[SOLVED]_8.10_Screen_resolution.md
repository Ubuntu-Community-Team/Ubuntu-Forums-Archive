---
title: "[SOLVED] 8.10 Screen resolution"
date: 2008-12-02
forum: General Help
---

### Post by Tictoon on 2008-12-02
Hey everyone, I just upgraded to 8.10 and my 24" screen is running at 800x600 resolution. I have a Nvidia Graphics card, but I'm not sure which one and I really do not want to open up my computer unless 1000% neccessary, so could someone help me?

---

### Post by Grolsche on 2008-12-02
have u tried going to

system>preferences>screen resolution and changing the resolution from there?

---

### Post by Tictoon on 2008-12-02
Yes

---

### Post by dexter on 2008-12-02
- Install nvidia-settings:
```
sudo apt-get install nvidia-settings
```

- Run it
```
sudo nvidia-settings
```

- Go to the X Server Display Configuration, you should be able to set you appropriate resolution there. Once it's configured, click "Save to X configuration file" which will generate a valid xorg.conf file.

---

### Post by Tictoon on 2008-12-02
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

thats the error message I got

---

### Post by 2hot6ft2 on 2008-12-02
You should be able to go to System>Administration>Hardware Drivers and select the NVIDIA driver that it recommends. Click the activate driver button at the bottom, after it finishes installing it will tell you that it requires a reboot. Reboot, then go to System>Preferences>Screen Resolution and set it. All done

---

### Post by Tictoon on 2008-12-02
Thanks!

---

### Post by virtual_m on 2009-01-04
I have the same problem.. It's help. Thanks dexter!

---

