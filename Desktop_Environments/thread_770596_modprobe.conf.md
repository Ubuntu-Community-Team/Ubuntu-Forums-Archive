---
title: "modprobe.conf"
date: 2008-04-27
forum: Desktop Environments
---

### Post by dancer58 on 2008-04-27
Can someone tell me where modprobe.conf is or where the configuration is done in Ubuntu hardy

---

### Post by milosz.galazka on 2008-04-27
> **dancer58 said:**
> Can someone tell me where modprobe.conf is or where the configuration is done in Ubuntu hardy

You mean /etc/modules file or files in /etc/modprobe.d/ directory?

---

### Post by dancer58 on 2008-04-29
> **milosz.galazka said:**
> You mean /etc/modules file or files in /etc/modprobe.d/ directory?



This is what I am trying to do:

replace model=3stack by model=6stack in Modprobe options 
 /etc/modprobe.conf for Fedora 8 

I am not very knowledgeable in linux so I hope this answers your question

---

### Post by milosz.galazka on 2008-04-29
> **dancer58 said:**
> This is what I am trying to do:

replace model=3stack by model=6stack in Modprobe options 
 /etc/modprobe.conf for Fedora 8 

I am not very knowledgeable in linux so I hope this answers your question

hmm, maybe you search for file */etc/modprobe.d/options*
You can add there a line similar to
```
options snd-hda-intel index=0 model=6stack-dig
```
(I suppose you want to achieve something similar as in above example)

---

### Post by dancer58 on 2008-05-03
> **milosz.galazka said:**
> hmm, maybe you search for file */etc/modprobe.d/options*
You can add there a line similar to
```
options snd-hda-intel index=0 model=6stack-dig
```
(I suppose you want to achieve something similar as in above example)


I tried the suggestion but it did not help. Still no sound
I wish I knew enough to tell if this is a linux or alsa problem

I seems odd to me that sound worked in Ubuntu Gusty but will not work in Hardy. I guess I will have to wait and see if Ubuntu comes up with a fix

Thanks for the suggestions
Harold

---

### Post by Zorael on 2008-05-03
The file you want is **/etc/modprobe.d/alsa-base**. Edit/place that line at the very bottom and then restart the sound system.
```
$ sudo /etc/init.d/alsa-utils restart
```

---

### Post by dancer58 on 2008-05-04
> **Zorael said:**
> The file you want is **/etc/modprobe.d/alsa-base**. Edit/place that line at the very bottom and then restart the sound system.
```
$ sudo /etc/init.d/alsa-utils restart
```


I got an error:

 * warning: 'alsactl store' failed with error message 'alsactl: save_state:1251: No soundcards found...'...                                              [fail] 
 * Setting up ALSA...                                                    [ OK ] 


Any other suggestions

---

