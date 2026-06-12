---
title: "Alsa - Enemy Territory"
date: 2005-11-30
forum: Gaming &amp; Leisure
---

### Post by Zodiac on 2005-11-30
Can Enemy Territory be used succesfully with ALSA?

I have a 2 sound card setup... 1 onboard the other PCI and I use ALSA. No problems anywhere but when I fire up ET I get no sound with a message in the terminal saying, "Sound Muted".

Anyone have any ideas??

---

### Post by Watcher on 2005-12-06
If got exactly the same problem. If I found a solution, I'll post it here

---

### Post by Watcher on 2005-12-23
have you done this [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) ? I haven't, but maybe that works ... (if it does let me know)

Still haven't gotten it to work :(

---

### Post by Zodiac on 2005-12-23
Yes I have tried that, unfortunately it doesn't do any good.

I believe it is because the author of that page assumes the reader has 1 sound card when in fact I have two. If I were to edit and save asound.conf with pcm.card0 it explodes mightily. 

In my opinion sound in Linux is spotty at best and it is really difficult to get older games to work with newer sound cards. 

Because of problems like this, I have had to switch back to Windows on my gaming PC. If you can, I would recommend you do the same. It is just too much stress trying to get solutions for my odd hardware setup.

If you ever do find a solution, please post it here. Maybe by then I will be willing to try Linux on my gaming PC once again...

---

### Post by mgor on 2005-12-23
quick search on google:
[http://64.233.183.104/search?q=cache:pluyED87q-QJ:gentoo-wiki.com/index.php%3Ftitle%3DTIP_Make_sound_work_with_ALSA_and_Quake3/Enemy-Territory%26printable%3Dyes+enemy+territory+alsa&hl=en&lr=&client=firefox-a&strip=1](http://64.233.183.104/search?q=cache:pluyED87q-QJ:gentoo-wiki.com/index.php%3Ftitle%3DTIP_Make_sound_work_with_ALSA_and_Quake3/Enemy-Territory%26printable%3Dyes+enemy+territory+alsa&hl=en&lr=&client=firefox-a&strip=1)

worst case would be installing artsd.

---

### Post by Watcher on 2005-12-23
Currently I still have my main pc running a dual boot system windows - ubuntu mainly for gaming (and for developping website's for which I like to use Dreamweaver, and have not yet found a better substitute).

It would be very nice if I could get this to work. I am going to try to unplug my sound card and use my onboard sound system to see if that does anything good, I'll keep you guys posted!

---

### Post by Zodiac on 2006-04-21
Hey Watcher, did you ever find a solution?

---

### Post by aktiwers on 2006-04-22
This link  [http://ubuntuguide.org/#configuresoundproperly]("http://ubuntuguide.org/#configuresoundproperly") above helped me together with this from Terminal.

```
# echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
``` 
Hope it helps :)

---

