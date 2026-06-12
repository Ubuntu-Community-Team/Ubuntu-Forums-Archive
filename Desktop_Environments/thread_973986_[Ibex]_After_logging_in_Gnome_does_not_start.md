---
title: "[Ibex] After logging in Gnome does not start"
date: 2008-11-07
forum: Desktop Environments
---

### Post by whtvr on 2008-11-07
Hi,

I have just installed the Ubuntu 8.10 desktop (stable release) on my Thinkpad X30 and I have a problem with it. Installation goes fine and systems starts ok but when I put my username and password on the login screen Gnome seems to be loading for couple of seconds, I can see and move the mouse cursor and than the whole thing just stops. I can only see black backgroud and no panels/icons/etc. There's no disk activity and I cannot use Ctrl + Alt + Backspace or Ctrl + Alt + Fx although I can move the cursor. The only option is to hard reset the computer.

I had exactly the same issue with the last beta and RC of Ibex but couldn't find a working solution so far ([http://ubuntuforums.org/showthread.php?p=6041597](http://ubuntuforums.org/showthread.php?p=6041597)) even though I've found couple of threads describing similar problems.

This is very frustrating and effectively prevents me from upgrading to the newest version of Ubuntu. Any help will be much apreciated.

Thanks

---

### Post by jerrylamos on 2008-11-07
Those look like the symptoms I get with my IBM Thinkpad R31 with Intel video graphics.

8.10 Intrepid has by default "eye candy" "animation" code called compiz. For many many users 8.04 Hardy worked fine.

In 8.10 compiz uses a video graphics code path not used by any other code. This path does not work as compiz expected for many Intel graphics resulting in a black or tan screen with cursor when the desktop should have loaded.

A workaround for this:

Boot in rescue mode. That's the second line on the screen.
At the menu, select:
root shell prompt
At the command line type:
sudo apt-get remove compiz compiz-core
Answer Y when asked
exit
resume

This works for many people. Depending on what hardware you have, there are some other things to try. 

A more complete explanation of the compiz situation is in Launchpad Bug #259385.  The bug was originally reported on August 19 however it wasn't until after 8.10 was released that they found the cause.  There still isn't a fix to enable the compiz to work; there is an update which just disables compiz for the affected hardware.

Good luck. Jerry

---

### Post by whtvr on 2008-11-07
Awwwwright! (-:

Thanks Jerry, that did the trick. Additionally I reclaimed 20MB of my hard disk space (-;

Thanks again

---

