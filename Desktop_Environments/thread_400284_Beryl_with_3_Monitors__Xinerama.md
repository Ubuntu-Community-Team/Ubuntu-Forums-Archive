---
title: "Beryl with 3 Monitors / Xinerama"
date: 2007-04-03
forum: Desktop Environments
---

### Post by freerick on 2007-04-03
[SIZE="4"]Has anyone had any success with **setting up Beryl on a system with three monitors**?[/SIZE]

I have two NVidia 6200 cards and I'm using Xinerama to emulate one large desktop spanning all three screens, but with different resolutions and boundaries on each screen. It works like a charm, but I can't get Beryl or Compiz to work because appaprently Beryl requires the RandR extensions to be present. It is present, but it's disabled by Xinerama, since it's theoretically not needed when there is more than one monitor. If I only use two screens and switch to TwinView, thereby circumventing Xinerama, Beryl works, further corroborating the theory that the lack of the RandR extension with Xinerama is the likely cause for the problem; this has also been brought to the attention of th Beryl dev team and they said they "might offer a fix" in one of their "future releases". 

I've read reports that people have successfully set up **three screens with Beryl**. If anyone has any information on how to patch the code or other techniques I could employ to make this happen, it would be greatly appreciated.
Regards,

---

### Post by palermi on 2007-04-29
i have same configuration, (22'' DVI , 17'' VGA, TV TV-Out).

 My conf work well with 22 and 17 on xinerama but dont work with 22''+17''+TV on Xinerama.

Beryl dont work, i dont know.

Please, post your xorg.conf

Thanks

---

