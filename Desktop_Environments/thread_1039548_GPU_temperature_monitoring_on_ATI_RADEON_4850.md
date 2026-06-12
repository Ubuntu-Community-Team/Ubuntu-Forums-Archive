---
title: "GPU temperature monitoring on ATI RADEON 4850"
date: 2009-01-14
forum: Desktop Environments
---

### Post by marcgh on 2009-01-14
Hi,
is there any (easy) way to monitor the GPU temperature?

I have tried the 'hardware monitor sensor' and it works well for CPU, fan and HDD but no GPU monitoring.

My Graphic card is ATI RADEON HD 4850 and i'm using UBUNTU 8.10

Thanks in advance

---

### Post by Rotarychainsaw on 2009-01-14
as far as I know, there is no easy way right now. You can check on it from the terminal if you want... I'm assuming you are using the fglrx driver.

aticonfig --od-gettemperature

If it is running hot you can change the fan speed from the terminal as well.

aticonfig --pplib-cmd "set fanspeed 0 55"

Change the 55 to whatever % you want the fan running at.

---

### Post by marcgh on 2009-01-15
Thanks for the tip.

I am using the ATI driver from the ATI site( ati-driver-installer-8-12-x86.x86.run)

In terminal, this is the reply after entering  aticonfig --od-gettemperature :

ERROR - Could not find library: libatiadlxx.so

Is there still hope? TThanks in advance!

---

### Post by Tares on 2009-01-15
> **marcgh said:**
> Thanks for the tip.

I am using the ATI driver from the ATI site( ati-driver-installer-8-12-x86.x86.run)

In terminal, this is the reply after entering  aticonfig --od-gettemperature :

ERROR - Could not find library: libatiadlxx.so

Is there still hope? TThanks in advance!

I assume that you had an ealier version of the fglrx, removed it, builded new packages and installed them. If so, the libatidlxx is common problem ( I have it too ), but unfortunatly I don't know any cures for that :/

---

### Post by marcgh on 2009-01-15
Tares,
I'm to fresh in Ubuntu to really understand fully what I have to do and I'm not willing to put at risk my setup that, after all is working well.

Could you please tell me how I have to remove fglrx, build new packages and install it.

Sorry for the (ab)use of your time.

---

### Post by marcgh on 2009-01-16
Just a little bumb

---

### Post by marcgh on 2009-01-19
re-bumb?
Anybody please?
I'm really worried about frying the video card.

---

### Post by marcgh on 2009-01-21
anybody? pls?

---

### Post by nicobeukes on 2009-03-05
> **marcgh said:**
> anybody? pls?
I have a 4870x2 and loaded the ati 9.2 drivers right after i installed ubuntu 8.10 from the downloaded 64bit dvd, i opened a terminal and browsed to where the driver was downloaded and ran sudo sh ati-driver-installer-9.2-x86.x86_64.run, it loaded the driver and after a reboot i was able to set the fanspeed using the console, you can also follow this link for a superkaramba plugin that displays the temp and fanspeed on your desktop:
[http://www.kde-look.org/content/show.php/ATI+Fan+Control?content=91918](http://www.kde-look.org/content/show.php/ATI+Fan+Control?content=91918)

hope this helps you, I feel a lot better running ubuntu now, with a fanspeed off 50% it now runs at 42 degress, before it was running at 82 degrees

---

