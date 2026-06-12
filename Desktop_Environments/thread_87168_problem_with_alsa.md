---
title: "problem with alsa"
date: 2005-11-07
forum: Desktop Environments
---

### Post by suoko on 2005-11-07
Hi,

I have a strange problem with alsa.
When I select alsa from gstreamer-properties I get the choppy sound you can hear in the attachment.
If otherwise I select oss or esd it sounds ok (continuous sound).
What is the problem?
I have alsa and alsa-oss installed. I tried removing alsa-oss with no success.
I also removed all modutils and modprobe config files in /etc and I still get the problem. I guess the problem is in the /etc/init.d/alsa-utils file.
any hints?

---

### Post by manicka on 2005-11-07
Is this in amaroK?

---

### Post by suoko on 2005-11-07
It's strange since I have no problems with applications, only with the sample of gstreamer-properties

---

