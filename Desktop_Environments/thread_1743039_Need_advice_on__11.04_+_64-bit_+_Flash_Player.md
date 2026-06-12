---
title: "Need advice on : 11.04 + 64-bit + Flash Player"
date: 2011-04-29
forum: Desktop Environments
---

### Post by Guillaumeb on 2011-04-29
Hello

I installed Ubuntu 11.04 and use the GNOME environement instead of Unity on a Dell Latitude E4300 which has a 64-bit architecture.


I'd like to run GTalk in my Firefox sidebar with their [web messenger]("http://talkgadget.google.com/talkgadget/popout"). Yet the service requires flash.

I tried installing Flash from the Ubuntu software center and also tried to install the 64-bit version by doing : 
sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer

from [this tutorial]("http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal") 

Now on the same machine the Google website used to run perfectly with ubuntu 10.10, though I can't remember which version of Flash I used.

Would anyone be kind enough to post a tip for me and explain how they got it to work.


Thank you very much

---

### Post by zain.dain on 2011-04-30
Hi 
relay now i installed Adobe Flash Player on my new Ubuntu 11.04
what you have to do 
[INDENT]1. Download [Adobe Flash Player 10]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz")
 2. Untar it : *tar zxvf flashplayer10_2_p3_64bit_linux_111710.tar.gz*
 3. Copy *libflashplugin.so* to firefox plugins directory and make a symlink for addons directory
 *   sudo  cp libflashplugin.so /usr/lib/firefox/plugins*
 *    cd /usr/lib/firefox-addons/plugins*
 *    ln -s /usr/lib/firefox/plugins/libflashplayer.so libflashplayer.so*
 4. Restart Firefox
[LEFT]

I think you got it 

Have a Nice Day:popcorn:
[/LEFT]


[/INDENT]

---

### Post by zero-g on 2011-06-20
Thx zain.dain worked like a sharm :)

---

### Post by fballem on 2011-06-20
Another option that I have found to be very reliable is to use the flash-aid add-on in Firefox.

To obtain this, open FireFox then the Add-ons from the Tools menu. If you search for, and install, Flash-Aid, it will guide you through the rest of the way.

I don't use Google Chrome, so not sure how flas works there.

Hope this helps,

---

### Post by ovidiu_b13 on 2011-07-24
> Another option that I have found to be very reliable is to use the flash-aid add-on in Firefox.

To obtain this, open FireFox then the Add-ons from the Tools menu. If you search for, and install, Flash-Aid, it will guide you through the rest of the way.

I don't use Google Chrome, so not sure how flas works there.

Hope this helps,

Works like a charm on Chrome. Ubuntu 11.04 x64.

Thank you for your help.:)

---

### Post by ovidiu_b13 on 2011-08-22
The instalation and update works with Flash-Aid from firefox, but on chrome flash videos don't play normaly: most of the times a black square apears in the place of the video  and the audio works, but there is no video. If I refresh the page a fiew times, only then the video works. 

Any Ideas on how to fix this?

---

