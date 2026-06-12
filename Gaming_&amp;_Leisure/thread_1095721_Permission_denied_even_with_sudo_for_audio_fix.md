---
title: "Permission denied even with sudo for audio fix"
date: 2009-03-14
forum: Gaming &amp; Leisure
---

### Post by Azure.Rise on 2009-03-14
Usually for Wolfenstein Enemy Territory I could use 

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

to fix the audio at least for the current session when I was getting no sound. Now when I try it I get permission denied even when using sudo. I've never tried install ET on Ubuntu 8.10, but I'm pretty sure this worked in 8.04.

---

### Post by sahabcse on 2009-03-14
paste the command o/p 

ls -al /proc/asound/card0/pcm0p/oss

---

### Post by Azure.Rise on 2009-03-14
-rw-r--r-- 1 root root 0 2009-03-13 23:31 /proc/asound/card0/pcm0p/oss

---

### Post by sahabcse on 2009-03-14
hi

Login to the root user

#sudo bash

Then enter

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

### Post by Azure.Rise on 2009-03-14
Thanks, that worked! Also it looks like this is permanent and not just for the session right?

---

### Post by sahabcse on 2009-03-14
Yes it is permanent:D

---

### Post by Azure.Rise on 2009-03-14
Well, I logged out and back in and the audio still worked. But I turned my computer back on this morning and the audio is gone. Running the command again makes the audio work though. How do I make it permanent?

---

