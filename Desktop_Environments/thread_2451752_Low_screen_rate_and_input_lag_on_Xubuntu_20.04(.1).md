---
title: "Low screen rate and input lag on Xubuntu 20.04(.1)"
date: 2020-10-10
forum: Desktop Environments
---

### Post by ioni14 on 2020-10-10
Hello,

I usually don't post my issues but after a lot of research, I don't find a solution to this one at all.

I've installed the new Xubuntu LTS  (20.04) and I was on 18.04 that works very well (the both are in dualboot for the moment).

And when I've used the 20.04, my middle screen has a frequency rate lower than my 2 other screens, despite that it has a higher rate. (When I move quickly my cursor on the middle screen, it has fewer "traces" than others).

Here my config on the both versions (18.04 and 20.04) :
Display: [Ecran 1 : 144Hz] - [Ecran 2 165Hz] - [Ecran 3 144Hz]
Graphic Card : Nvidia RTX 2080 Ti (the 3 screens are all plugged with DisplayPort).
I'm using a nvidia driver (not X) on the both versions (nvidia-410 on 18.04 and I've tested many versions on 20.04).

And, when I write on some applications (e.g., Slack, Joplin, Discord...) I have a big input lag (~1FPS) that displays the text only after some time.

It seems that if I disable hardware acceleration on Slack and Discord, this removes the input lag. There are no issues at all on 18.04.

I hope you can help me because it's very annoying.

Thank you.

---

