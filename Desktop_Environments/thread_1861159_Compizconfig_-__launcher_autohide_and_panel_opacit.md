---
title: "Compizconfig -  launcher autohide and panel opacity functions not working  in 11.10"
date: 2011-10-15
forum: Desktop Environments
---

### Post by jammaj on 2011-10-15
I have just upgraded to 11.10. I like a really minimal, 'clean' desktop. In 11.04, under the Ubuntu Unity Plugin in Compizconfig, you could change the opacity of the panel and launcher, as well as making the launcher autohide by default - which meant that the desktop environment could look minimal. Both these functions do not seem to be working in 11.10. Any idea how I can get them to work?

---

### Post by Krytarik on 2011-10-15
It seems like you are being logged in to Unity 2D as per fallback to the regular Unity. You can easily check that via "System Monitor"; if you find a bunch of processes with names starting with "unity-2d", it is.

As it seems you had the regular Unity running in Natty 11.04, check if you can install a better video driver, in "Additional Drivers", if you have an Nvidia or a non-legacy AMD/ATI card/chip. See this guide how to check if your current setup is capable to run the regular Unity, and if needed, how to force it:

[http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

However, if you can't get the regular Unity to run, see this guide how to configure Unity 2D, even though it doesn't offer as many options as the regular one:

[http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html](http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html)

Hope that helps!

---

### Post by Scott Deagan on 2011-10-15
I have a problem with the launcher set to 'auto-hide'. Sometimes when I start up 11.10 and then move the mouse pointer to the very left of the screen, the launcher just doesn't appear.

Although annoying, I found that going into CCSM -> Ubuntu Unity Plugin and then setting "Hide Launcher" from "Autohide" to "Never" and then back to "Autohider" fixes the problem.

---

### Post by jammaj on 2011-10-16
> **Krytarik said:**
> It seems like you are being logged in to Unity 2D as per fallback to the regular Unity. You can easily check that via "System Monitor"; if you find a bunch of processes with names starting with "unity-2d", it is.

As it seems you had the regular Unity running in Natty 11.04, check if you can install a better video driver, in "Additional Drivers", if you have an Nvidia or a non-legacy AMD/ATI card/chip. See this guide how to check if your current setup is capable to run the regular Unity, and if needed, how to force it:

[http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

However, if you can't get the regular Unity to run, see this guide how to configure Unity 2D, even though it doesn't offer as many options as the regular one:

[http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html](http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html)

Hope that helps!

Yep, that did help - thanks very much! It is all working now. 

I feel like a bit of an idiot for not checking that out. I have got an ATI/AMD that needed an additional driver. It was the same in 10.10 and 11.04. I just didn't think of it. #-o

---

### Post by Krytarik on 2011-10-16
> **jammaj said:**
> I feel like a bit of an idiot for not checking that out. I have got an ATI/AMD that needed an additional driver. It was the same in 10.10 and 11.04. I just didn't think of it. #-o
Actually, the Jockey should have popped up automatically upon the first login, as it's used to do. So, I wasn't sure if you have a video card/chip for which 'additional drivers' can be installed, or whatever else reason might have led to those dialog not popping up automatically, or if you just missed it. ;-)

---

