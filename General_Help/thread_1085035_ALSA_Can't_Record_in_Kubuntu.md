---
title: "ALSA Can't Record in Kubuntu"
date: 2009-03-02
forum: General Help
---

### Post by Unanimated on 2009-03-02
EDIT: I need to record something in about a week, so this is rather urgent!
EDIT2: No replies yet, just my own bumps. -_-

In Ubuntu 8.10, recording worked perfectly using ALSA. Now that I've switched to Kubuntu 8.10, I can't record using my mic or direct input from my keyboard anymore. I downloaded a recording suite from the repos, and when I pick the engine to be ALSA, it says that it can't open ALSA or something like that. I downloaded a simple recorder from GNOME, and it gave the same result. What's the issue here?

---

### Post by Unanimated on 2009-03-02
bump

---

### Post by Unanimated on 2009-03-03
bump

---

### Post by Unanimated on 2009-03-03
bump

---

### Post by Unanimated on 2009-03-04
bump

---

### Post by Unanimated on 2009-03-04
bump

---

### Post by Unanimated on 2009-03-05
Oh, come on. Three days and no replies?

---

### Post by Unanimated on 2009-03-06
You can't be serious.

---

### Post by martrn on 2009-03-06
Type:  ```
alsamixer
``` into a terminal (or shell).

Are any of them muted ?

The default sound trouble shooting guide is at:
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

Make sure your sound card is supported by ALSA kernel modules and is properly installed.

I have to (or have had to) rebuild by ALSA drivers on every kernel update, because the stock ALSA kernel modules do not want to work.

---

### Post by Unanimated on 2009-03-11
Traverso says that it can't set the audio device thread to realtime priority. That might be the case. I set the audio device thread to ALSA.

---

### Post by Doncr on 2009-06-26
Well, I have just wasted most of today trying to get sound to work properly in Kubuntu 9.04.

I've been using Linux for ten years, and sound has always been a pain in the ****. Basically dosen't work. I give up on it.

---

