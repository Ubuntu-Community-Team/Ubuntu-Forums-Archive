---
title: "No Splash on Boot - Splash on Shutdown"
date: 2012-07-03
forum: Desktop Environments
---

### Post by frogotronic on 2012-07-03
Hello,

  12.04 LTS with nVIDIA drivers.  No splash (plymouth) at boot, just a blank purple screen; but splash at shutdown, tried the 10.04 resolution fix for proprietary drivers - didn't work.

Any Ideas?

Thanks,
CH     :guitar:

---

### Post by msammels on 2012-07-03
Hello.

OK, well to be honest, now that I look at my machine, you're right :P have you tried reinstalling plymouth? I'm not sure if it maybe has something to do with the graphic boot drivers, not sure. But now I definitely notice it.

---

### Post by christiaan_ on 2012-10-18
It is all due to a little variable called **$vt_handoff** in the **/boot/grub/grub.cfg** file that blacklists graphic cards and decides wrongly that a graphical boot screen is not allowed. 

Simply edit the grub.cfg file and remove all $vt_handoff references in the code.

See : [http://www.thefanclub.co.za/how-to/how-fix-ubuntu-boot-splash-screen-after-grub-updates](http://www.thefanclub.co.za/how-to/how-fix-ubuntu-boot-splash-screen-after-grub-updates)

---

### Post by paviel on 2012-10-18
Another simple way is to edit /etc/default/grub and change the line GRUB_GFXPAYLOAD_LINUX

This solution works only when uvesafb is used.

sudo gedit /etc/default/grub
and change the line as follows
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-32,mtrr=3,scroll=ywrap  

after look at the line 
GRUB_GFXPAYLOAD_LINUX=1280x1024-32

and change
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=1280x1024-32

save the file
and
sudo update-grub

---

### Post by christiaan_ on 2012-10-18
Dear Paviel

The moment you update GRUB, it adds the $vt-handoff to the default you created. The line in **grub.cfg** then becomes :

quiet splash nomodeset video=uvesafb:mode_option=1280x1024-32,mtrr=3,scroll=ywrap **$vt_handoff**

In my case I have to remove this every time I update grub or the boot splash is missing as explained in my post #3.

---

### Post by paviel on 2012-10-18
Dear christiaan_

yes, grub.cfg contains $vt_handoff
but since the modifications I proposed before, I have plymouth working and never had to change anything else.

---

