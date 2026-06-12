---
title: "beta nvidia settings not detecting second monitor"
date: 2006-10-07
forum: Desktop Environments
---

### Post by themoebius on 2006-10-07
I'm using the beta drivers I'm using I have a setup with a GeForce FX 5900XT as my primary, AGP vid card and I have two identical EN9110 screens plugged in one in the digital port and the other in the VGA port. The second video card is a Geforce 6200 and has a Dell P780.

nvidia-settings detects the digital EN9110 and the Dell and it detects that there is something connected to the VGA port on the 5900, but I can't get anything above 800x600 on it. I've tried going in to xorg.conf myself and entering the correct HorizSync and VertRefresh rates and metamodes myself, but it didn't help.

I'm thinking I'll have to configure xorg.conf myself since nvidia-settings is insufficient but convincing it to to a three-headed, two-vid-card display with xinerama extensions AND hardware acceleration is very difficult. I did it once for a short time but I've since reinstalled that system and forgot to back up the xorg.conf. I have attached my current xorg.conf.

---

