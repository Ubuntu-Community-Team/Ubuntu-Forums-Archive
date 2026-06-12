---
title: "Help with fonts"
date: 2009-08-21
forum: Desktop Environments
---

### Post by jonnan on 2009-08-21
I appear to have goofed up ubuntu in entirely surprising ways by uninstalling what appeared from context to be entirely foreign language fonts.

I have recovered the mess enough by manually reselecting fonts in Ubuntu and firefox that I'm back on the web; but would very much like to know how to

A) reset the fonts back to the original installs

B) reset the various font/appearance settings back to their original installs, and

C) what are the best font's and configurations for ubuntu 9.04 and an LCD monitor, if anyone has an opinion.

D) ask if anyone knows exactly what fonts are required in the default installation, because I'm entirely confused as to how uninstalling a group of oriental and other foreign language fonts could reduce my machine to doing things like showing [0020] in little squares on every space between words - but still show words?!?! Or show blank spaces on google, but words when highlighted? and so on . . .

Thank you in advance - Jonnan

---

### Post by oldfred on 2009-08-21
You could try reinstalling ubuntu desktop. This will add if anything is missing:
sudo apt-get install gdm ubuntu-desktop  
or reinstall:
sudo apt-get install --reinstall gdm, nautlius, ubuntu-desktop, x-gnome-session, xserver-xorg

That should reset everything.

Also info on pixel smoothing:
Pixel smoothing for fonts
[http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/](http://hawn.be/tag/ubuntu-fonts-msttcorefonts-microsoft-fonts-tahoma-arial-times-new-roman/)

Also System, preferences, appearance, fonts    - for settings.

---

### Post by macunixfan on 2009-08-21
> **jonnan said:**
> C) what are the best font's and configurations for ubuntu 9.04 and an LCD monitor, if anyone has an opinion.


To get the fonts to look like how they look in my OSX I went on this guide:

[http://neologe.com/articles/improving-linux-fonts/](http://neologe.com/articles/improving-linux-fonts/)

Don't know if it will help you or not but I'm using 9.04 and thats what I did.

---

### Post by jonnan on 2009-08-24
Thanks - I'll try that - Jonnan

---

