---
title: "Install on Inspiron 9200"
date: 2009-07-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 44robot on 2009-07-24
Can 9.04 ubuntu be installed on dell 9200 inspiron Intel M processor.ive burned .iso and tried install gets to the end and error pops says denied refer to log file wubi-9.04-128.log.using the snipping tool here is @ the error it highlighted.

---

### Post by s3MA00RRNY on 2009-07-24
Are you running the install from an admin account? That might work better.

---

### Post by dtrot55 on 2009-08-10
I am currently on a dell inspiron 9200 running 9.04 and the only issues i am having is that i cant really control volume and i get random cpu spikes that use 90-100% depending on what im doing...but 9.04 works fine when that doesnt happen

---

### Post by Sophont on 2009-08-11
> **dtrot55 said:**
> I am currently on a dell inspiron 9200 running 9.04 and the only issues i am having is that i cant really control volume and i get random cpu spikes that use 90-100% depending on what im doing...but 9.04 works fine when that doesnt happen

Do the spikes involve pulseaudio? And if so do you use Skype?
If the answer to both questions is yes you can fix that by getting the static-oss version of skype from the Medibuntu repo ([http://medibuntu.org/]("http://medibuntu.org/")) and put start skype with "padsp skype" instead of just "skype".

---

### Post by dtrot55 on 2009-08-11
No I don't use skype...but I was able to somewhat control the audio by using the PCM slider instead of the Master Volume Slider...so a temp fix for now...unfortunately the laptop control buttons dont control the volume though :(

---

