---
title: "wine crashing"
date: 2006-06-25
forum: Desktop Environments
---

### Post by RajivNair on 2006-06-25
i just installed the latest version of wine 0.9.16 today.i did winecfg and the configuration window opened but as soon as i clicked on the "Audio" tab the wine crashed giving the following error:-

"rajiv@Rajiv-Nair:~$ sudo winecfg
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /root/.kde/socket-Rajiv-Nair.
can't create mcop directory
"
Can any tell me what is happening.

Thanks in advance.

---

### Post by Xzallion on 2006-06-25
[QUOTE=RajivNair]ALSA lib seq_hw.c:456snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory[/QUOTE]
I have this same problem, I think it has something to do with it not trying to access the right sound drivers.  No ideas how to fix this though.

---

### Post by RajivNair on 2006-06-25
well i found how to fix it.so silly of me for not to search information.
Just do: -
 
cd /usr/lib/wine
sudo mv winearts.drv.so winearts.drv.so.old

---

### Post by scotsboyuk on 2006-06-26
@RajivNair

  Muchos Gracias old boy! :) I was having this problem myself and that did the trick. :)

---

