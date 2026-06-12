---
title: "z60t DVD playback issues with dcss installed"
date: 2006-08-27
forum: Desktop Environments
---

### Post by zeusfaber on 2006-08-27
I have installed dapper on my new z60t and I am experiencing the same issue as this post (can't reply, closed):

[http://ubuntuforums.org/showthread.php?t=132843&highlight=z60t](http://ubuntuforums.org/showthread.php?t=132843&highlight=z60t)

I can play unencrypted DVDs, burn DVDs and etc without issue. But if I attempt to play any DVD with encryption it doesn't work. I have tried vlc, xine, mplayer and totem-xine all of them seem to act as if libdvdcss2 is not installed. The totem-xine error says "You are trying to play an encrypted DVD....you may need to install libdvdcss". I have the dvdread and nav libraries installed as well. I have also tried installing different versions of libdvdcss2. All other formats/codecs seem to work fine. I have read the above post but my DVD drive is detected properly but as scd0 in dev since it is SATA, so it doesn't have a DMA setting, at least to my understanding.

Any help or suggestions would be great. Let me know if you need any more info. Thanks.

---

### Post by dentaku65 on 2006-08-27
mmm.. really strange... did u tried Ogle?
[http://yep.it/?z63zys](http://yep.it/?z63zys)
it is also in the repo...

---

### Post by zeusfaber on 2006-08-27
I have tried it, I forgot to mention it.

---

### Post by dentaku65 on 2006-08-27
did u try to follow this:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
?

;)

---

### Post by zeusfaber on 2006-08-27
Yes, I have this all installed, although I have the dcss installed via apt. I have tried the scripted way too, without the proper result. I also have my region set to 1. 

What permissions and groups do I need to belong to? I just want to verify its not an issue with my user privleges. Then again I suppose if that were the case it would work using sudo, it doesn't.

I have also found that it looks like it starts to play the DVD but then dies. In ogle it plays then starts the ecrypted part of the DVD and gets very heavy with artifacts then dies. 

In the terminal I see stuff this, just before it dies:

*** invalid macroblock type
*** skipped blocks in I-picture
*** skipped blocks in I-picture
(vlc) invalid huffman code 0x1 in vlc_get_block_coeff()
*** invalid macroblock type
WARNING[ogle_mpeg_ps]: Found a scrambled PES packet! (1)
ctrl: ipc_rmid: Invalid argument


Ideas? Thanks.

---

### Post by zeusfaber on 2006-08-28
ok, so, i reinstalled and installed dcss. everything is cool now.

strangeness abound.

---

### Post by zeusfaber on 2006-08-28
actually it looks like just specific DVD's.... Sin City, pi and Hitchhikers Guide and others work fine. the Squid and the Whale and thumbsucker dont work and have the same error as before. This is strange. I wonder what causes this?

---

