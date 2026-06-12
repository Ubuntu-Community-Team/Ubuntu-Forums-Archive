---
title: "Change display setting?"
date: 2009-11-19
forum: Desktop Environments
---

### Post by Btheone on 2009-11-19
I have successfully installed ubuntu, but the display setting are not set right, everything is really big? How do i change the display setting, how is this possible?

I'm using the newest version on ubuntu.
Thanks.

---

### Post by wojox on 2009-11-19
Try System > Preferences > Display

---

### Post by Btheone on 2009-11-19
I have tried this, but it says monitor unknown and doesn't allow me to change setting?

---

### Post by wojox on 2009-11-19
Okay go into System > Administration > Hardware Drivers and see if there's a driver for your graphics card.

---

### Post by Btheone on 2009-11-19
Its says; 'No proprietary drivers are in use on this system'?.

---

### Post by Btheone on 2009-11-19
Where can i find drivers or whatever i need to sort this problem out?

---

### Post by Btheone on 2009-11-19
I found the driver i need i have also downloaded it, but im not sure how to install and run it can anyone help please?

---

### Post by wojox on 2009-11-19
Where did you download the driver from and what is it's extension? .bin .deb?

---

### Post by wojox on 2009-11-19
Try:

```
xrandr -q
```

And see what it says

---

### Post by Btheone on 2009-11-19
The file i have ends in a .run

---

### Post by Btheone on 2009-11-19
What about using; NVIDIA X Server Settings would that help me? But i not sure how to install that either? :-)

---

### Post by wojox on 2009-11-20
Run update manager again and then check Hardware Drivers.

What does:

```
lspci | grep VGA
```

Tell us?

---

### Post by realzippy on 2009-11-20
> **Btheone said:**
> What about using; NVIDIA X Server Settings would that help me? But i not sure how to install that either? :-)

First install that NVIDIAxxxxx.run file....

To install NVIDIA driver (file is on Desktop):



1. Log out

2. Press Alt+Ctrl+F2

3. Log in at shell

4. Stop X by typing: **sudo /etc/init.d/gdm stop**

5. Navigate to Desktop: **cd Desktop**

6. Install driver: **sudo sh NV** (press Tab to autocomplete NVIDIAfilename)

7. Answer asked questions during installation with "yes"

8. reboot: **sudo reboot**

---

