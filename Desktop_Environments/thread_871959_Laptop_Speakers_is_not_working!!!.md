---
title: "Laptop Speakers is not working!!!"
date: 2008-07-27
forum: Desktop Environments
---

### Post by rithuarjun on 2008-07-27
Hi,

    I am very new to Ubuntu as well to linux. I am using Acer 5920 Laptop with Windows XP Professional and Ubuntu Hardy Heron Linux winth GNOME in dual boot mode. Ubuntu is working fine only thing is the sound is coming out from the laptop speakers but i can able to hear the sounds from the headphone when it's connected to the corresponding port. Moreover the sound effect is also not quiet good in ubuntu when i campare the same with windows. In windows the laptop speakers are working fine.

Kindly help me in this regards,

Thanking you,

Awaiting response!!!!

K.S. Arjun Singh

---

### Post by warp99 on 2008-07-27
You may have to manually set the option for your sound card. Please open a terminal and run the following:

```
lsmod |grep snd
```

You should see the module snd_hda_intel loaded, if not just post the output here to this thread. Now we check the Alsa Configuration reference guide to see which model we need:

[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#757](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#757)

According to the list  your model is listed as 'acer', so open a terminal and issue the following command:

```
echo "options snd-hda-intel model=acer" |sudo tee -a /etc/modprobe.d/options
```

You could also use this command instead:

```
sudo gedit /etc/modprobe.d/options
```

then add the string 'options snd-hda-intel model=acer' minus the quotation marks and save the file. Next time you restart your computer the headphones should work.

---

