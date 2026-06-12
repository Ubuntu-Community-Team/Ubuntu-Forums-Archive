---
title: "Steam missing 32-bit  libGL.so.1; running 64-bit proprietary drivers"
date: 2016-05-14
forum: Gaming &amp; Leisure
---

### Post by sean119 on 2016-05-14
I'm trying to use steam, but I keep getting this error message: ```
You are missing the following 32-bit libraries, and Steam may not run: libGL.so.1
``` I tried to install the *libgl1-nvidia-glx-i386* package, but it depends on all of the packages that go along with the 32-bit nvidia driver, and I'm running the 64-bit 352.79 driver. Does anyone know a workaround? Thank you.

---

### Post by deadflowr on 2016-05-15
*Thread moved to **Gaming & Leisure**.*

---

### Post by MikeCyber on 2016-05-15
There's a newer Nvidia driver. Simply download from Nvidia, execute after shutting down x and select install 32bit libs.
something alike:

[LIST]
[*]Use ctrl + alt + F1 to switch to terminal,
[/LIST]
sudo service lightdm stop
cd /home/downloads
chmod +x nvidi*
./Nvidi*
sudo reboot

---

### Post by sean119 on 2016-05-15
This fix worked, but I went about it a different way. Here's what I did for anyone who is having this problem. I added experimental to my /etc/apt/sources.list, and installed the experimental *nvidia-driver* package using the command ```
sudo apt-get install -t experimental nvidia-driver
``` This way you don't have to worry about checking the nvidia site every once and a while for updated drivers, and apt will take care of everything. Thanks!

---

### Post by oldrocker99 on 2016-05-15
Experimental drivers can have weird artifacts sometimes; your mileage may vary.

---

