---
title: "ATI drivers on 9.04"
date: 2009-06-10
forum: General Help
---

### Post by CaptainMark on 2009-06-10
Ive got a problem with my new graphics card, ive always used ATI/AMD over intel or Nvidia for as long as I can remember so when i refurbed an old pc and installed Ubuntu 9.04 I bought a nice shiny new ATI Radeon HD 2400, being an ex windows user i didnt even think about compatabilty issues. Now I have the card I cant get it to work, Ive tried installing the ATI propietary driver and it installs ATI catalyst, which works until I turn my machine off and then resets to default settings and i have to change the settings again. I dont know what to do, Ive heard that its possible to make any graphics card work using the xorg.conf file but I didnt know where to start. 
Any advice would be helpful as I dont know my next step to take.

---

### Post by Legace on 2009-06-10
Try to install the drivers manually:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

---

### Post by pritamps on 2009-06-10
After installing the drivers, try typing this in a terminal

```

sudo aticonfig --initial 

```

---

### Post by CaptainMark on 2009-06-10
this is the point i have gotten to on my second try and the file doesnt exist, ive ran a search on the whole filesystem it isnt there,

---

### Post by CaptainMark on 2009-06-10
Okay ive run through again this time catalyst isnt there, instead ive got loads of deb files plonked on my desktop. The guide didnt say anything about this. Any help??

---

### Post by blackSP on 2009-06-10
I have the ATI Radeon HD 2400 in my Asus laptop and everything runs smooth with the Catalyst 9.5 drivers!

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=English)

---

### Post by revelationman on 2009-06-10
I am one those unlucky ones with ATI Radeon Xpress Series  with my HP Compaq NX 6325 with the 1100 ATI Express, was going to updated it to 9.04 but was advised that the drivers are not supported or will work something like that.
This to me is terrible on ATI 's part, 
Could anyone shed any light on what to do, right I am running 8.10 and stopped using  the restricted driver,
This is still a good working laptop perfect for Linux and Ubuntu in general no sense going back to XP or even Vista. 
So will Ubuntu develop drivers for this or is this laptop soon to be history ?

---

