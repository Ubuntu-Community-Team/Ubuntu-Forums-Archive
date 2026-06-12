---
title: "Skype settings at boot"
date: 2005-03-16
forum: Desktop Environments
---

### Post by matgorb on 2005-03-16
How can I put this two command at startup, without being ask for a password?

sudo echo "skype 256 65535 block" > /proc/asound/card0/pcm0p/oss
sudo echo "skype 256 65535 block" > /proc/asound/card0/pcm0c/oss

---

