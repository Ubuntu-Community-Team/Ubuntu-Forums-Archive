---
title: "sound problems upgrading to 8.04 with inspiron 1420n"
date: 2008-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kaldar on 2008-06-22
found solution under known bugs.  Should have looked more thoroughly, whoops.

---

### Post by robertbub on 2008-07-14
FWIW, I fixed my sound problems by adding this line:> options snd-hda-intel model=dell-3stackto **/etc/modprobe.d/alsa-base**.  It seems I got this solution from [http://ubuntuforums.org/showpost.php?p=4818991&postcount=6](http://ubuntuforums.org/showpost.php?p=4818991&postcount=6) .

---

### Post by oscarFrance on 2008-07-26
Hi,

Just for information, The following link gave me a solution:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

I had "Unresolved symbols" with snd-hda-intel when upgrading above 2.6.24-14.

Best regards,
Oscar

---

