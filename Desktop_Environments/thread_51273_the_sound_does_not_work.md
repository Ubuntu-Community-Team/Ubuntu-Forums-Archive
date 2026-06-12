---
title: "the sound does not work"
date: 2005-07-23
forum: Desktop Environments
---

### Post by shevek on 2005-07-23
Hello:
 I have installed Ubuntu Hoary, and almost everything works fine, except for the sound. I can't listen to any audio CD, or DVD or an ogg or mp3 file. In multimedia selector I have ALSA selected. My sound card is a SB 128 PCI. I have tried with rithmbox, muine, totem and neither of them work. The thing is the dvd or the files start playing, and in the case of a film I can watch the video but I can't listen anything.

  In the Spanish Ubuntu forums, somebody has told me that perhaps is because I have too many audio devices in /dev/sndstat (I have three different devices) If that is the problem, how can I fix that?

 That's all. Thank you for your answers.

---

### Post by shevek on 2005-07-25
I have tried with the configuration from [Ubuntu Guide](http://ubuntuguide.org/#configuresoundproperly) but it has not worked. 

Most likely I will be wrong, but perhaps the problem is that configuration assumes your sound card is card0? Because in my case, I have looked in /proc/asound and I think my sound card is card 2.

Any other idea?

---

### Post by arunsub on 2005-07-25
Do a search for sound in the forum. You'll get lot of threads with the problem and solution. Also, check the how to in the tips and tricks section of the forum.

---

### Post by arunsub on 2005-07-25
Howtos:
[http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567)
[http://ubuntuforums.org/showthread.php?t=29500](http://ubuntuforums.org/showthread.php?t=29500)

---

### Post by shevek on 2005-07-25
Thank you arunsub. I have solved this. The only problem was I had enabled the sound integrated into the motherboard. I have disabled that in the BIOS and now the sound works perfectly.

---

