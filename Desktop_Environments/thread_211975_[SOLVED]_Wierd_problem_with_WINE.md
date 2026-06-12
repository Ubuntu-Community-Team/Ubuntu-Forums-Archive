---
title: "[SOLVED] Wierd problem with WINE"
date: 2006-07-09
forum: Desktop Environments
---

### Post by rattlerviper on 2006-07-09
Any help anyone can offer would be great. I installed wine from repository and installed echolink(ham radio software) and foxfire for windows(to test), and am not getting any sounds. I opened winecfg and when I click the audio tab it shuts down and the terminal reads this.

everyone@ubuntu:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/everyone/.kde/socket-ubuntu.
can't create mcop directory
everyone@ubuntu:~$

I changed where i got Wine from to deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main. This was a newer version and  I thought it might fix the problem, but no such luck:confused:   The weird thing is I had sound and everything was functioning, I shut the computer down and when I restarted it I had no soun on anything associated with Wine???  I hope someone out there can help and point me in the right direction[-o< 

Thanks for your time reading the post. Charlie

---

### Post by rattlerviper on 2006-07-09
It just occured to me, is this even the correct area of the forum to post this question in? I want to try and fit in well around here, because i plan to be here a very long time...Hopefully answering more questions than asking in the future after I learn the ins and outs of Ubuntu.

---

### Post by Trenchbroom on 2006-07-09
I had the same problem:  found the fix on another thread.

[http://www.ubuntuforums.org/showthread.php?t=196033&highlight=mcop+directory]("http://www.ubuntuforums.org/showthread.php?t=196033&highlight=mcop+directory")

Go to ELD's last post--that worked for me.  Make sure when you get access to the Audio tab you change it to ALSA (if that is what you are running).

---

### Post by rattlerviper on 2006-07-09
> **Trenchbroom said:**
> I had the same problem:  found the fix on another thread.

[http://www.ubuntuforums.org/showthread.php?t=196033&highlight=mcop+directory]("http://www.ubuntuforums.org/showthread.php?t=196033&highlight=mcop+directory")

Go to ELD's last post--that worked for me.  Make sure when you get access to the Audio tab you change it to ALSA (if that is what you are running).


Thank you very much, all if fine now!:D  I love Ubuntu!!!

---

