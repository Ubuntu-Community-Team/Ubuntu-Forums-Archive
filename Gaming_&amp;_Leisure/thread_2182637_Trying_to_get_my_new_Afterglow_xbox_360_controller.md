---
title: "Trying to get my new Afterglow xbox 360 controller to work"
date: 2013-10-21
forum: Gaming &amp; Leisure
---

### Post by malenkylizards on 2013-10-21
Hello, all.  I recently bought an Afterglow xbox 360 controller.  I believe it's the same as this: http://www.bestbuy.com/site/pdp-afterglow-ax-1-controller-for-xbox-360/9888998.p?id=1218189805051&skuId=9888998&ref=06&loc=01&ci_src=14110944&ci_sku=9888998&extensionType={adtype}:{network}&s_kwcid=PTC!pla!{keyword}!{matchtype}!{adwords_producttargetid}!{network}!{ifmobile:M}!{creative}&kpid=9888998&k_clickid=6805ac44-f831-5089-d336-00002ee73581

I've had good luck with using it on the windows 8 side of my PC, however it hasn't been such easy sailing on the Ubuntu 13.10 side (surprise, surprise!).  I didn't try it OOB; first I followed the accepted answer here: [http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working](http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working)

If I followed it literally, it said to run the xboxdrv command BEFORE plugging in the controller, which doesn't work.  Once I did plug it in, the ring on the controller flashed steadily, which I took to mean it was getting power but unable to communicate with the computer.  I removed xpad from the blacklist, and restarted.  At this point, when starting up the computer and going into Steam Big Picture, it is responsive, but only partially.  The A button is unresponsive, for instance.  Pressing the left analog stick seems to do the same thing as the A button.  I've tried to modify it using jstest-gtk, but I get the following message when I try to run it: Error: /home/******/.config/jstest-gtk: File exists

I haven't been able to find anyone else with the same problem.  Any idea what's causing that particular error?

---

### Post by malenkylizards on 2013-10-21
OHHHHH!!!!!  "File exists" is kind of a silly way of saying permission denied.  I get the error with "jstest-gtk", but "sudo jstest-gtk" works.

---

