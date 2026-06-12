---
title: "Vostro 1500 - Nvidia 8600M GT - Kernel Issues"
date: 2010-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dominicglenn on 2010-09-18
Hey Guys,

I recently switched to Ubuntu 10.04 and have set up Twinview using my laptop (vostro 1500 with 8600m gt graphics card) and everything runs fine.

The only issue is that every time I start up my Ubuntu I get a kernel error from the Nvidia drivers. It tells me that the configuration is wrong and that I need to change my x config.

I have installed the latest drivers from their website, and to remedy the situation I just quit to the command line, go to the setup file and start installing it.

Previously I would fully install it and then type 'sudo service gdm start' and this would let me login as usual and continue; but lately I didn't even let it install - I just boot into it and then quit when it tells me that my drivers are already up to date. If after doing this I type 'sudo service gdm start' it boots up fine, as if there was never anything wrong.

Do you have any idea how I could solve this issue for good?

Thanks

---

### Post by ptptaylor on 2010-09-19
I could be getting the wrong end of the stick, but i've had a few display issues before using the x server.
It was solved by editing my xorg.conf found in etc/X11 . 

In my xorg.conf, have a look what I used:

[http://ubuntuforums.org/showthread.php?t=1565046](http://ubuntuforums.org/showthread.php?t=1565046)

Note the resolutions you may need to edit so that it works for your setup.

I also tried to install the latest drivers (256?) and that didn't go to well. I installed it all fine, but had some compatibility issues so am using the (196?) driver.

---

