---
title: "usb-creator, live CD and restart"
date: 2009-06-02
forum: General Help
---

### Post by sirdan on 2009-06-02
I've created a bootable USB drive with the Live CD image using usb-creator with Jaunty. It works great, but when I choose restart from the menu or hit the reset button, the computer doesn't boot; saying there is no bootable device. It always works from power on though.

I've initiated a conversation with Intel about this, thinking maybe it's a BIOS problem. However, I don't encounter the same problem with a DOS bootable USB drive. It always finds a boot device when I hit reset.

Anyone else encounter this?

thanks,
dan

---

### Post by munky99999 on 2009-06-02
So bios normally sees usb drives but not when the wizard does it?

Have you tried alternatives like unetbootin?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by sirdan on 2009-06-03
Thanks  munky99999 for the suggestion. I just tried unetbootin, but it doesn't boot at all in that case. Simply giving "Boot error" for the message when it tries to boot.

I wouldn't be surprised if the creators of LiveCD didn't consider there might be a situation where users did want to restart without removing the LiveCD. I guess the more normal usage might be boot once, try it and install. But my scenario is different. I want to restart from the bootable USB "LiveCD" all the time. As a side note, I want to eliminate the prompt asking me to remove the CD and press Enter.

Anyone out there who can help me solve this problem? Is this the approriate forum for LiveCD questions or is there a better place?

thanks,
dan

---

### Post by sirdan on 2009-06-03
To answer my own question..

For Ubuntu 9.04, follow the instructions to create a LiveCD, [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

You'll need to rebuild initrd.gz according to the instructions after you modify edit/etc/init.d/casper. Just comment out the lines that eject the CD and prompt to remove the disc.

---

