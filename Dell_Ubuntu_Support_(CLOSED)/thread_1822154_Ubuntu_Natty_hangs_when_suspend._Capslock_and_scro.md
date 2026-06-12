---
title: "Ubuntu Natty hangs when suspend. Capslock and scroll lock blink continuously."
date: 2011-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kranthi.doss on 2011-08-10
Hi, i am running Ubuntu 11.04 on Dell inspiron 1520. My present kernel 2.6.38-10 hangs after i hit suspend and the caps lock and scroll lock LEDs blink continuously until the battery drains out. The same is not the case with kernel 2.6.38-9, suspend and resume work perfect.

I tried to use the no_console_suspend option and pm-suspend to see if i can find something, but that didn't go well becoz the terminal too hung up.

PLZ HELP ME !

---

### Post by Toz on 2011-08-10
The flashing LEDs is in an indication that your computer has suffered a kernel panic. 

I too had issues with 2.6.38-10 and quickly uninstalled it and went back to 2.6.38-8 which works flawlessly for me. Unless you have some pressing need for new functionality or bug fixes in the -10 kernel, you do not need to install/run it.

Hold down the Shift key while you are booting to display the grub screen. IIRC, the new kernel restructures grub so that you now have a section called something like "Previous kernels". Go into that section and you should see the -8 kernel listed, click on it and you will boot with it to get access to your system again.

---

### Post by kranthi.doss on 2011-08-10
thanQ TOZ. I'll do it. I hope that is the solution for now.

---

### Post by kaoul on 2011-09-03
I had the same problem with my toshiba. I created this file as a solution :

```
root@tshb:/usr/lib/pm-utils/sleep.d# cat 54virtualhook 
#!/bin/sh
# Unload vboxdrv for a bug workaround on suspend on ubuntu 11.04

. "${PM_FUNCTIONS}"

suspend_vb()
{
    service vboxdrv stop
}

resume_vb()
{
    service vboxdrv start
}

case "$1" in
    hibernate|suspend)
        suspend_vb
        ;;
    thaw|resume)
        resume_vb
        ;;
    *) exit $NA
        ;;
esac

```

After a chmod +x on this file, when I suspend from the menu it works.

---

### Post by thilina on 2011-09-04
I too had the same problem with Ubuntu 10.04 and 10.10 . But all got solved when I switched to 11.04. (My laptop is Inspiron 1464)

---

### Post by venro on 2011-09-10
Many thanks. 

I've tried lot of solutions on web, but only 54virtualhook script helped me. I'm on Ubuntu 11.04 x86 with Thinkpad T61.

I had no idea that the cause was VirtualBox (I needed it from the moment I installed Ubuntu).

---

