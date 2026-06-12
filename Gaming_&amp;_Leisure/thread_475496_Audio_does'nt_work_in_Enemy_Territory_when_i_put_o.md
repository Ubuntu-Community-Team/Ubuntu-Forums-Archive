---
title: "Audio does'nt work in Enemy Territory when i put on TeamSpeak.."
date: 2007-06-16
forum: Gaming &amp; Leisure
---

### Post by Garret88 on 2007-06-16
I have this problem with TeamSpeak. I have tried other tricks but nothing.
(I can hear the audio on teamspeak but not in ET).

I have an integrated audio card.

---

### Post by Rafty on 2007-06-16
have you tryed this: [http://tcesupport.tc.ohost.de/forum/viewtopic.php?t=91](http://tcesupport.tc.ohost.de/forum/viewtopic.php?t=91)

---

### Post by syväpaahto on 2007-06-16
Both Teamspeak and Enemy Territory use OSS. Since only one program can use OSS at one time, the one started later will be mute. I relly don't know how to fix this. I just run TS in computer thats next to mine. TS-audio comes in to my computer through the 3mm mic input.

---

### Post by Rafty on 2007-06-16
> **syväpaahto said:**
> Both Teamspeak and Enemy Territory use OSS. Since only one program can use OSS at one time, the one started later will be mute. I relly don't know how to fix this. I just run TS in computer thats next to mine. TS-audio comes in to my computer through the 3mm mic input.
yep, and to fix this prob you need to run this
```
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```
in a terminal before starting TS/ET ;)

---

### Post by Garret88 on 2007-06-16
Doesn't work in this manner. But i resolve with a guide found now on google(this guide was created yestrday!! but it's in italian..). I don't know if i can post the link(for spam reasons).

---

### Post by hikaricore on 2007-06-16
> **Garret88 said:**
> Doesn't work in this manner. But i resolve with a guide found now on google(this guide was created yestrday!! but it's in italian..). I don't know if i can post the link(for spam reasons).

It's pretty safe to post a link to an outside guide if other users might find is useful.
As long as it's not someone trying to sell the guide/services to ya.

It might even help to link it using translation from google: [http://translate.google.com/translate_t](http://translate.google.com/translate_t)
The translation won't be perfect but most competent humans will be able to get a rough idea even if the wording is a little odd.  ^_^

---

### Post by Garret88 on 2007-06-18
This is the link of the guide -> [http://ulisse.wordpress.com/2007/06/15/enemy-territory-teamspeak-e-alsa/](http://ulisse.wordpress.com/2007/06/15/enemy-territory-teamspeak-e-alsa/) (**[COLOR="Red"]IN ITALIAN[/COLOR]**)

[COLOR="Red"]**TRANSLATION WITH GOOGLE**[/COLOR] -> [http://66.249.91.104/translate_c?hl=it&langpair=it%7Cen&u=http://ulisse.wordpress.com/2007/06/15/enemy-territory-teamspeak-e-alsa/](http://66.249.91.104/translate_c?hl=it&langpair=it%7Cen&u=http://ulisse.wordpress.com/2007/06/15/enemy-territory-teamspeak-e-alsa/)

---

### Post by omegvermelho on 2009-05-22
> **Rafty said:**
> yep, and to fix this prob you need to run this
```
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```in a terminal before starting TS/ET ;)



Omg i can't thank you enough for this, i already tried some 200 diferent aproaches to this problem without any success finally a solution....KUDOSSSSSSSSS


btw every time i use ctrl key in a combo with a numeric key (while playing ET) nothing happens, and if the key combo is CTRL + 3 it's like pressing ESC and the menu opens up.Why does this happen and how can i fix this???Tks in advance..........

---

