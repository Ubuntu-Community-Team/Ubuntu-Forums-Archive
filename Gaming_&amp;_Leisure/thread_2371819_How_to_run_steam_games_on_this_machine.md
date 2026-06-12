---
title: "How to run steam games on this machine?"
date: 2017-09-19
forum: Gaming &amp; Leisure
---

### Post by bobis on 2017-09-19
Hello , I currently own a headless pc desktop (only ethernet and power are  connected to its back) and I have installed the latest Ubuntu Server on it.

I also have installed a VNC server (NO gnome or any desktop GUI, only VNC , I mean,  when I connect a monitor to the pc , I just see the black screen of console , so I want to keep it minimal) on it in order to have simple GUI access from remote or lan location 

I also tried to install steam on this VNC session and tried to launch CSGO client (the game) but it fails. Especially , I see 2 error messages:

1) After launching steam : "OpenGL GLX context is not using direct rendering, which may cause performance problems. For more information visit https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457." but it seems to be ignored because steam launches ok , but with some minimal graphical problems.

2) After trying to launch CSGO: " Failed to create SDL window: Couldn't find matching GLX visual"

The reason that I want to launch CSGO behind a headless server is to help populating a server by idling.

Well, the pc-server has a graphic card ( a simple nvidia one) , but it seems that VNC sessions do not recognize it (hence these errors) so how to make it read my graphic card? I also tried to install some nvidia drivers but failed with a boot stuck , so how to install them safely.

Thank you!

---

### Post by oldrocker99 on 2017-09-20
You may need to install a desktop, which the errors seem to indicate.

---

### Post by efflandt on 2017-09-23
To be able to be fast enough, most games need to be able to work directly with graphics hardware ("direct rendering: Yes" in glxinfo from mesa-utils package) and that is not mirrored externally through VNC or even ForwardX11 in ssh. I don't actually see why Steam itself would necessarily need that, but any Steam games would, so it would be good to know if GLX is not working before trying to download/install any Steam games.

it appears that you are looking for something like Steam Link or Nvidia Shield and I don't really know if those work on a Linux host yet, much less on a host computer with no working graphics.

---

