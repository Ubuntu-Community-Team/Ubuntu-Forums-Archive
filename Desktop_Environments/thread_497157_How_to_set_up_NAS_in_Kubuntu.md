---
title: "How to set up NAS in Kubuntu"
date: 2007-07-09
forum: Desktop Environments
---

### Post by glennr on 2007-07-09
I use a KDE desktop (Kubuntu Fiesty) via VNC from a Windows PC and I would like for sound to also be exported to the Windows PC.

I notice that KDE has the option to output sound using NAS but I cannot find any instructions on how to configure it. I gather that I'll need nasd running on the Windows PC, but am unsure how to tell KDE to direct the sound to this nas server.

I have "nasd -aa" running on the Windows PC and "auplay -audio tcp/otherpc:8000 somesound.au" correctly plays on the Windows PC. 

In Settings/Sound & Multimedia/Sound System/Hardware there is an option under output devices for Network Audio System, I have selected that and put "-audio tcp/otherpc:8000" in "the use other custom options" box but that doesn't work.

Does anyone know how to make this work?

---

