---
title: "Only command line after using Xorg/Xserver!"
date: 2006-04-12
forum: Desktop Environments
---

### Post by greenbmw530i on 2006-04-12
I got EasyUbuntu and got that set up, then I got a X server set up window thing...and I made sure I read the "help" for each option before hitting "forward" and I thought I was making the correct selection for each option (mainly the default, or auto-detected choice for each option)....

So, I restarted and got this big error that X server wasn't set up properly, so it made me view the configuration and it was all greek to me; however, one thing stood out to me:

Toward the end of the Xorg configuration list, it showed me a fatal error something about a framebuffer. Then if prompted me to go to the command line (i had no other option  :(), and that's all greek to me aswell. I'm pretty sure its related to my ATI video card.How can I fix this framebuffer option in X server in the command line to make Ubuntu all good and well again?

Please help me, my Ubuntu is unuseable to me as of now!
-Thanks a lot in advance,
Mike.

---

### Post by hater2win on 2006-04-12
A linux box without X is hardly unusable :P. You can browse the internet with a text based browser (w3m, lynx, links2). Any everything else you can do via commandline. you can switch to a command line with ctrl + alt + f1, f2, f3, etc (hold ctrl+alt for them all). 

as far as your problem goes, try running the configuration again, use this command:

```
sudo dpkg-reconfigure xserver-xorg
```


PS: ctrl + alt + F7 is the default one for X server, just so you know.

---

### Post by greenbmw530i on 2006-04-12
[QUOTE=hater2win]A linux box without X is hardly unusable :P. You can browse 
```
sudo dpkg-reconfigure xserver-xorg
```

That worked great, i was able to mess around with it and i rebooted and viola!

Thank you very much!
-Mike

---

