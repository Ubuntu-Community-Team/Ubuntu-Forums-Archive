---
title: "BIG nVidia problem, cant stop up =("
date: 2006-06-30
forum: Desktop Environments
---

### Post by Thanatios on 2006-06-30
Hello evey one

I right now have a very big nVidia problem, I tried to upgrade it, and after I did "Sudo nVidia-xonfig" it asked me to restart. After I restarted I coulnt visit my desktop anymore.
Only thing I get now is first an error about nvidia, after that I get a dos-like terminal, where I have to login. And I dunno what to do =(

Maybe unistalling and installing nVidia again will work? I dunno how to unistall so I myself cant do that. 

I have a nVidia GeForce FX 5600
meer info: [http://www.nvidia.com/page/fx_5600.html](http://www.nvidia.com/page/fx_5600.html)

Can anyone help me please? =(

Thanks in advance

---

### Post by grooverider on 2006-06-30
i had a similar problem, when i was medeling with xgl, if u would post the error log that would help, if the mistakes lies in the conf files, boot with live cd, copy from /etc/x!!/xorg.conf and from /etc/gdm/gdm.conf-custom onto the harddrive which u should mount by sudo mount /dev/hda1 /mnt (if hda1 is ur root directory) and place the files u copied into /mnt/etc/x11/ and /mnt/etc/gdm while still in the live cd, this did the trick for me..

---

### Post by tseliot on 2006-06-30
[QUOTE=Thanatios]Hello evey one

I right now have a very big nVidia problem, I tried to upgrade it...[/QUOTE]
Can you tell me exactly how you did it?

---

### Post by Thanatios on 2006-06-30
Thanks dude. It actually worked! :) I owe you one ;)

---

### Post by grooverider on 2006-06-30
[QUOTE=Thanatios]Thanks dude. It actually worked! :) I owe you one ;)[/QUOTE]

my pleasure :D

---

