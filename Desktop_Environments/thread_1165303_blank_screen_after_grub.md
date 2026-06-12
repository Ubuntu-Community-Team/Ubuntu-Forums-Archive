---
title: "blank screen after grub"
date: 2009-05-20
forum: Desktop Environments
---

### Post by se_landy on 2009-05-20
Today I uninstalled fgrlx driver that I was using to try new ATI driver... First I uninstalled old driver, than restarted my computer, than installed ATI 9.5 driver. There were no improvements. It was even worse... so I decided to uninstall it and install my old driver. I uninstalled it, restarted my computer and installed my old driver... Then I pressed reset button again so my old driver could start working. But my computer wont't start... Grub shows up, but after grub there is just blank screen. First there was a message saying Xsomething can't start and "No device found" but now there is just blank screen...
What can I do???? I don't want to reinstall ubuntu if I don't have to, I spent too much time adjusting it... :(
It's ubuntu 9.04

Could it be some error in ATI drivers I'm using??? This is what I get when I try "startx"

[SCREENSHOT]("http://www.imagesforme.com/out.php/i501826_SPA0691.jpg")

Can anyone tell me how to stop using ATI driver and to go back to default driver??? PLEEEEEEAAASEEEEE!!!

---

### Post by se_landy on 2009-05-20
ANYONE??? I can't look at my computer anymore, I don't have desktop for too long now...:(

---

### Post by zika on 2009-05-21
let's start:
when You boot can You select (recovery mode) option for Your kernel in Grub menu?
if You can choose that option and after that if You get next menu select option with command prompt and networking ...
log-in with Yourname and password
after that, once You are in command line (i.e. terminal) do:[FONT=monospace]
[/FONT]sudo aticonfig --force --initial
logout and reboot (sudo reboot now) and let's see what happens.

You are missing defaults in ATI database that is supposed to replace (and already did) depreciated xorg.conf ...

good luck and, please, check with manuals and on the net before using my suggestions ... do not believe me, this is just an educated guess ... I was just looking at Your screen shot ...

---

