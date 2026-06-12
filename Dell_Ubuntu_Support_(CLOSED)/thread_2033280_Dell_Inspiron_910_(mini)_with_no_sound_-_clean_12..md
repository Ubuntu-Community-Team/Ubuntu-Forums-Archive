---
title: "Dell Inspiron 910 (mini) with no sound - clean 12.04 Ubuntu install"
date: 2012-07-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mylolligirl on 2012-07-25
Hi - I just installed 12.04 on my Dell Mini.  I have no sound and it is driving me crazy.  I am new to this so please explain as if talking to a 3 year old.  I do know that I have Realtek ALC268. Thanks for your help.

I do have sound though my headphones.

deanette@deanette-Inspiron-910:~$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC268
deanette@deanette-Inspiron-910:~$ 



Your ALSA information is located at [http://www.alsa-project.org/db/?f=ddb0ef7b0f819ce6f052ecc69aa7c3f8862b0153](http://www.alsa-project.org/db/?f=ddb0ef7b0f819ce6f052ecc69aa7c3f8862b0153)

---

### Post by mscout2004 on 2012-07-28
have you installed the package "linux-backports-modules-alsa-percise-generic"?

---

### Post by mylolligirl on 2012-07-29
No, I did not install that package.  Please forgive me for asking but would I install that in a terminal?  I am very new to this.  Thank you for your help.

---

### Post by mylolligirl on 2012-07-29
I searched for that package in updates and my search returned no matches.

---

