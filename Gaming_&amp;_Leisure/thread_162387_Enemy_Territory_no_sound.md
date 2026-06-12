---
title: "Enemy Territory no sound"
date: 2006-04-18
forum: Gaming &amp; Leisure
---

### Post by ice.man on 2006-04-18
i have tryed To resolve this issue I simply typed from root terminal the following:
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

but it says  

ubuntu:~/games$ sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: Permission denied

---

### Post by mrchrisblau on 2006-04-18
change the permissions of the file, perhaps?

chmod should do it...

---

### Post by ice.man on 2006-04-18
negitive or i did it wrong

---

