---
title: "No sound in HP 6730s"
date: 2009-04-07
forum: General Help
---

### Post by Mimoo_Tz on 2009-04-07
hi , 
I'm just beginner in Ubuntu world, ... 
I installed this great  operation sys  few days ago, ... I have prob with sound card , .... I don t know what 's  thesolution 

I uninstall/ install  Alsa , .... but the same prob   

PLZ I need help

---

### Post by Mimoo_Tz on 2009-04-07
.. I search in ubunt community , the suggest to remove ALSArchitetucre by OSS , ... I do these this evening ... but no sound in these case ,

i must install now Alsa , but these didn t work with me 'I mean the install operation'
I haven t solution , ... I have HP laptope , sound card Intel corporation 82801I

no one to help

---

### Post by poncije on 2009-05-30
Now i got the internal speakers working on my 6730s with Ubuntu 8.10.
(before only the headphone jack did work)
just add to /etc/modprobe.d/alsa-base the following line:

options snd-hda-intel model=laptop enable=1 index=0

This is usually the solution. Check if you have sound with earphones plugged into the laptop. I didn't have to install the new alsa version for it to work. Just put in the line and REBOOT! :-)

---

### Post by poncije on 2009-05-30
Oh... I forgot:
You need to edit "/etc/modprobe.d/options" as well.

options snd-hda-intel model=mobile

Now reboot!

---

