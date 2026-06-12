---
title: "no sound in Vostro 1400"
date: 2007-11-08
forum: Dell  Ubuntu Support
---

### Post by adecchi on 2007-11-08
Hi! I am alex recently i intalled ubuntu 7.10 .I have an intel card sound but i have not audio. My ubunto detect the card and installed the driver but i have not sound.So I download the last alsa soud driver and i run:
./configure --with-cards=snd-hda-intel
make && make install
 But i have not luck

Then i run:
#alsaconf list
intel
#alsamixer
function snd_ctl_open failed for default: No such device.

Someone can help me ?

---

### Post by Skuzniak on 2007-11-09
Hi Alex. I too have a Vostro 1400, and these steps got sound working for me.

sudo gedit /etc/modprobe.d/alsa-base

and add the line "options snd-hda-intel model=5stack" without quotes under the heading # Prevent abnormal drivers from grabbing index 0.



Then the following commands:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

You will need your ubuntu disc in your drive for the third command.

Reboot and see if sound works.

Let me know if it works!

---

### Post by obbimi on 2007-11-10
Hi, i have a vostro 1700 and initially sound did not work with ubuntu 7.10.
I followed your instructions and now it works!!

Thx!!

---

### Post by adecchi on 2007-11-10
Thz to all my solution was !

Add the following line to /etc/modprobe.d/alsa-base
options snd-hda-intel probe_mask=1 model=3stack 


Adecchi

---

### Post by eternal-one on 2007-12-04
no work fo me in ubuntu studio 7.10. make any diff that im using studio?

thanks

---

### Post by gindyo on 2007-12-06
thanks adecchi your solution worked for me : vostro 1400

---

### Post by adycopilu on 2007-12-07
i”ve got the same problem on Dell Inspiron 1720, but thanks to your instructions, it all worked out well. Thanks!

---

### Post by aldenhg on 2007-12-08
If you've got the stomach for it, I'd reccomend compiling the drivers yourself. It's not that tough - I did it first try. If you do it this way, you'll even have sound after suspending.
[http://ubuntuforums.org/showthread.php?t=635333](http://ubuntuforums.org/showthread.php?t=635333)

---

### Post by chip616 on 2007-12-26
Shuzniak:

Module Assistant is an awesome solution.  Makes things much easier for a relative newbie like myself.  Worked very well on my Dell Vostro 1700.

Do you know if there is any way to boost sound levels?  Volume on this machine is very low, and alsamixer shows the volume up to max.

Thanks.

Frank.

---

### Post by tex0514 on 2007-12-27
Thanks Skuzniak

That did the trick to getting sound to work  ; have you had any luck with the web cam ?

---

### Post by rognas on 2008-01-03
> **Skuzniak said:**
> Hi Alex. I too have a Vostro 1400, and these steps got sound working for me.

sudo gedit /etc/modprobe.d/alsa-base

and add the line "options snd-hda-intel model=5stack" without quotes under the heading # Prevent abnormal drivers from grabbing index 0.



Then the following commands:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

You will need your ubuntu disc in your drive for the third command.

Reboot and see if sound works.

Let me know if it works!

Oooooooh, a BIG thankyou to that problemsolver! :-D Jesus, what a relief to have a little sound on tha computer. :-D This is rognas on a Dell Vostro 1700 saying over and out to this problem.

---

### Post by LxAxKxI on 2008-02-09
> **Skuzniak said:**
> Hi Alex. I too have a Vostro 1400, and these steps got sound working for me.

sudo gedit /etc/modprobe.d/alsa-base

and add the line "options snd-hda-intel model=5stack" without quotes under the heading # Prevent abnormal drivers from grabbing index 0.



Then the following commands:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

You will need your ubuntu disc in your drive for the third command.

Reboot and see if sound works.

Let me know if it works!

Thanks for this , is help me to fix my sound alc883 on ubuntu-studio.:)

---

### Post by plippen on 2008-02-13
Hi, I have no sound at all on my vostro 1400. I made the installation with the Dell reinstallation DVD and everything works except the sound. I have tried every suggestion in this thread but nothing works. Im out of ideas so where should I continue?

---

