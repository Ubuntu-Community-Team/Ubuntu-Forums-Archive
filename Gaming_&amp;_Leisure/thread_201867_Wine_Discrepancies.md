---
title: "Wine Discrepancies"
date: 2006-06-22
forum: Gaming &amp; Leisure
---

### Post by 0okie on 2006-06-22
Alrighty, I've used Unbuntu in the past for about a week or two.. I'm trying to learn it now! :)

To my problem, i've been fighting with Wine for the past two days and have got it working at least. The problems I've been having (which i'm copying and pasting from terminal) are in the config. 

The first one is when I try to set the audio, I click on the audio tab and the config window closes and I get this error:

ookie@Kaveri:~$ winecfg
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playba ck stream
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory
Link points to "/tmp/ksocket-ookie"
can't create mcop directory
ookie@Kaveri:~$

Is there something from Synaptic that I need to get to fix this?

Thanks for taking the time to read this! (I put this is in the gaming section because i'm trying to get WOW to work)

---

### Post by seth0x2b on 2006-06-22
Since you are new to the forum I'm giving you an advice: use the search box on the top>right corner of your browser and look for
> open /dev/snd/seq failed: No such file or directory 
Cheers

[EDIT] Here's one of the searches
[http://www.ubuntuforums.org/showthread.php?t=153509&highlight=wine%3A+Assertion+failed](http://www.ubuntuforums.org/showthread.php?t=153509&highlight=wine%3A+Assertion+failed)

---

### Post by 0okie on 2006-06-22
Thank you, i've got that fixed now :)

---

