---
title: "Shutdown splash/ activating Framebuffer"
date: 2005-10-22
forum: Desktop Environments
---

### Post by bonzodog on 2005-10-22
To save accusations of cross-posting etc, I'm posting this as my own question:

On the AMD64 section, someone has asked about shutdown Splash screens, instead  of the ugly text scrolling by. I thought I'd put this in the 32 bit forum as I think it's a good idea, and somebody in here might know about it. So, any ideas? Is there a way of getting ubuntu to display a 'shutting down' screen? (with an option to display the text)

Also, how do I get the console to use the framebuffer when not in X?

---

### Post by maxadamo on 2008-05-11
> **bonzodog said:**
> To save accusations of cross-posting etc, I'm posting this as my own question:

On the AMD64 section, someone has asked about shutdown Splash screens, instead  of the ugly text scrolling by. I thought I'd put this in the 32 bit forum as I think it's a good idea, and somebody in here might know about it. So, any ideas? Is there a way of getting ubuntu to display a 'shutting down' screen? (with an option to display the text)

Also, how do I get the console to use the framebuffer when not in X?

If you want to get usplash immediately running, when you perform shutdown/reboot, you have to edit: /etc/init.d/usplash

go to to "stop)" case (should be line 87), and modify as following:
  stop)
        pidof $NAME >/dev/null || $DAEMON -c &
        if grep -q splash /proc/cmdline; then
                usplash_write "TIMEOUT 25"
        fi
        ;;

If you want to enable framebuffer on consoles, you have to remove the framebuffer that you want to use from:
/etc/modprobe.d/blacklist-framebuffer
and then add it to initram ... probably need to personalize initramfs.

---

