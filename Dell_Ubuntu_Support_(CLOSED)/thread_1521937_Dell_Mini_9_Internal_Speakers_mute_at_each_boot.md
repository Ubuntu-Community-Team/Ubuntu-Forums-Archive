---
title: "Dell Mini 9 Internal Speakers mute at each boot"
date: 2010-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by malegria on 2010-07-01
Hello. I have had a Dell Mini 9 for almost a year now with no problems. As of a week ago the sound from the internal speakers have been self-muting. I am not able to un-mute them with the sound preferences but with using **alsamixer** in a terminal. (Attached is an image of this screen).

I can unmute through there just fine but the problem is that I have to do this every time I reboot the netbook. Any advice on how to make this setting persistent?

Many thanks

Julio

---

### Post by snowpine on 2010-07-01
The following code should store your current alsamixer settings for future sessions:

```
sudo alsactl store
```

---

### Post by malegria on 2010-07-01
I used this command after I raised the volume, but upon reboot it did not set it as I wanted it. Do I do this before, after, or in conjunction with **alsamixer**?

---

### Post by snowpine on 2010-07-01
1. Set desired volume with alsamixer.
2. Save settings with 'sudo alsactl store'.

---

