---
title: "alsa doesn't work properly with ac'97 (help!)"
date: 2005-02-09
forum: Desktop Environments
---

### Post by Scorpio331 on 2005-02-09
Hey,

I've an atiixp ac'97 onboard soundcard on my laptop, but (even after updating alsa) I don't get any sound ! 
For exemple: my volumebar always indicates 0% and I can't change it.

I tried upgrading alsa (even from debian), but it still doesn't work.  ](*,) 

Enybody got an idea ? Thanks for answering !

(I'm sorry if this question is asked before, but I didn't find it ...)

---

### Post by Scorpio331 on 2005-02-09
And for further info,

when I tried to play a song with xmms I got these remarks:

"Please check that:

- Your soundcard is configured properly 
- You have the correct output plugin selected
- No other program is blocking the soundcard"

I already have run alsaconf and it said that the soundcard is configured
"Have a lot of fun", but nothing changed ...  :cry:

---

### Post by mpie on 2005-02-10
the ac'97 work perfectly with alsa, it's the soundcard on my desktop , i think that another program is still using it have you changed the properties for your desktop as i think that oss is used as default not alsa - goodluck

---

### Post by Scorpio331 on 2005-02-14
How can you make sure that alsa is used and not oss ? I don't think oss is used because I installed (and reinstalled) alsa 5 times or so  :-)  but when I use xmms I can choose both oss and alsa, but none work ...

Is it normal that I don't have an alsaconf ? Or is this replaced by alsactl ? 
Anyway I don't know how to use alsactl, is says 'specify command' but don't really know how to configure my sndcard properly ... I followed a lot of howto's on the net but they don't seem to work  :-| ...

Thanks for answering !

---

