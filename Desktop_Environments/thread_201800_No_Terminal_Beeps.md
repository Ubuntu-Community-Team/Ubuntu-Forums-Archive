---
title: "No Terminal Beeps"
date: 2006-06-22
forum: Desktop Environments
---

### Post by etank on 2006-06-22
All of the sound on my system appears to be working except for beeps in the terminal. Even when I run: ```
echo -e '\a'
```I don't hear anything. I am running Ubuntu on a Dell Inspiron 5150. Any ideas what I could do to get the beeps to work?

Thanks.

---

### Post by rowanparker on 2006-06-22
Are they turned on?

---

### Post by etank on 2006-06-22
They are enabled in Sound Preferences. All other sound seems to be working fine though.

---

### Post by etank on 2006-06-23
I found a fix. I loaded the alsa drivers and utils and now all of the sound is working on my system.

---

### Post by rowanparker on 2006-06-23
[QUOTE=etank]I found a fix. I loaded the alsa drivers and utils and now all of the sound is working on my system.[/QUOTE] Good Good!

---

