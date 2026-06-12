---
title: "usplash"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by arisejesus on 2007-11-18
i am using ubuntu 7.10 and i assume that ubuntu comes together with usplash installed. but when i boot, i cant even see the progress bar....it is juz a blank screen. so i thought there is some error, nwm. i tried installing another usplash theme, i even manager to configure the usplash-artwork.so to make my new usplash theme as default. later on i updated my system booting process by using this command: sudo update-initramfs -u, no problem, everthing ran well
when i rebooted, again there is no usplash, juz a blank screen. when i reach my desktop, i open a terminal and type in this command: sudo usplash -c to check the installation and i got this back

usplash: can't get console font: Invalid argument

wat is wrong?

---

### Post by JBAlaska on 2007-11-18
Type this in a terminal;
```
sudo gedit /etc/usplash.conf
```
Change the resolution to 1024x768

Then type this;
```
sudo update-usplash-theme usplash-theme-ubuntu
```

That should do it.

---

### Post by arisejesus on 2007-11-18
thanks but it does't work for me. i still get the same error, and during boot time, it is still a blank screen. any more other solution?

---

### Post by Dirty Ole on 2007-11-19
> **arisejesus said:**
> thanks but it does't work for me. i still get the same error, and during boot time, it is still a blank screen. any more other solution?

Try setting the vga mode that suits you monitor. Take [this]("http://ruslug.rutgers.edu/~mcgrof/grub-images/configs/linux/menu.lst") as an example.

---

### Post by arisejesus on 2007-11-19
well, i did try adding "vga=791" in the configuration file, but a blank screen still come out.

---

### Post by picpak on 2007-11-24
I'm having the exact same problem. Can anybody please help?

---

### Post by MasterJS on 2007-11-24
i had had this exact problem. The solution given is the right one, but if urs is "vga=791" try "vga=790". It worked for me.

---

### Post by arisejesus on 2007-11-25
i tried setting vga to 790 but it still dun work. when i boot, it give me this message: you have passed an undefined mode number

---

### Post by fooman on 2007-11-25
> **JBAlaska said:**
> Type this in a terminal;
```
sudo gedit /etc/usplash.conf
```
Change the resolution to 1024x768

Then type this;
```
sudo update-usplash-theme usplash-theme-ubuntu
```

That should do it.

thats sort-of how i fixed mine.

i guess it depends on your monitors screen size.  on my laptop,  the default screen size is 1280 x 800.  my /etc/usplash.conf was set @ 
xres=1280
yres=1024

i changed the yres to 800 so it reads:
xres=1280
yres=800

then i ran the command:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

rebooted and i got the splash screen back + a much quicker boot.  :)

---

### Post by arisejesus on 2007-11-28
earlier i did edited my usplash conf to 1024 x 768, but then it still dun work, cant figure out why

---

### Post by apothecaryaaron on 2007-11-28
I read this [ [COLOR="Blue"]thread[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=580903") and the post by **LeeAdkins** helped a good bit.  I had done everything mentioned in this thread, but that post pointed out that the file needs to be rebuilt.  Once I did that, it worked well upon reboot.

---

### Post by AlanRogers on 2007-11-28
FWIW, I was having the same problem; bid red [COLOR=red]**INPUT NOT SUPPORTED**[/COLOR][COLOR=dimgray] on a white background in the middle of the screen, until the graphics drivers had loaded. [/COLOR][COLOR=dimgray]Editting upslash.conf to the next valid 4:3 screen resolution down, 800 x 600 in my case. That brought back the boot graphics; I'm not sure that it actually boots quicker but it seems quicker when you're watching something other than a failure screen :D[/COLOR]

---

### Post by arisejesus on 2007-11-30
well, i did configure and rebuild the boot loader, but it stills dun work.

---

