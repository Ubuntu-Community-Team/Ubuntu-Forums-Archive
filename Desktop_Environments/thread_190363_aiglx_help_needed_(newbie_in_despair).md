---
title: "aiglx help needed (newbie in despair)"
date: 2006-06-06
forum: Desktop Environments
---

### Post by jvdv360 on 2006-06-06
Hi,

I recently started to use linux and I was quite impressed with the userfriendliness of ubuntu.
I installed ubuntu on an old PIII Coppermine laptop with S3 Savage vidcard.
So far so good.
But when I tried to install aiglx using [gandalfn's howto guide]("http://ubuntuforums.org/showthread.php?t=145068&highlight=aiglx"), I stumbled across some problems:

I first tried the method he posted, and used the compiz-vanilla package. No errors whatsoever but when I restart gdm, the taskbars, icons etc all disappear. I can only see the desktop background. However, things should work because I can open windows and when hovering over those windows (which I can't see), the mouse cursor changes...
Second try was with the compiz-quinn package: I can see the taskbars and icons now, but I can't click on them.
If I disable the "extensions" section in xorg.conf however, these two methods work fine, only I don't have the eyecandy.
Finally I tried with the compiz-aiglx and compiz-aiglx-gnome package and after restarting gdm I can see the taskbar and icons, they work, only there are no window borders drawn.
Again disabling the "extensions" section worked to restore to normal (without the eyecandy).

Sorry for the elaborate post but I can't explain my linux problems very well :rolleyes: 

Can anybody help me out?

---

### Post by dentaku65 on 2006-06-06
mmm, it seems that in the session manager compiz starts twice; try to purge all and reinstall all:

sudo aptitude purge compiz-aiglx compiz-aiglx-gnome

sudo aptitude purge compiz-vanilla-aiglx compiz-vanilla compiz-vanilla-gnome

then if you want to use Vanilla (lets say light version of compiz):

sudo apt-get install compiz-vanilla-aiglx compiz-vanilla compiz-vanilla-gnome

of if you prefer Quinn (my fav, advanced compiz):

sudo apt-get install compiz-quinn-aiglx compiz compiz-gnome

;)

---

### Post by jvdv360 on 2006-06-06
I tried what you said, and now I do get a working taskbar with compiz-quinn, but still no luck with the window borders...
It's like the gnome-window-decorator thingy isn't running (but it is, I checked in the system monitor). Well, at least something's working now :-)
EDIT: when I click the "Switch to metacity" option at the compiz icon, window borders work. Don't know if that helps

---

### Post by jvdv360 on 2006-06-06
My quest for aiglx was unsuccesful but in the meantime I installed ubuntu on my main computer and it runs great with xgl. Since this is my normal working machine, I'm quite happy with the result!

---

### Post by dpm on 2006-11-12
> **jvdv360 said:**
> 
I installed ubuntu on an old PIII Coppermine laptop with S3 Savage vidcard.


Your problem was that **compiz/beryl** still does not work with the **savage** driver. I've also got similar hardware (PIII Coppermine + S3 Savage), and I got pretty frustrated by this.

Apparently the cause is a 3D feature not present in the hardware, which if I understood correctly could be emulated by software as a workaround, but is still not implemented. See the orignal bug report where I got this information from:

[https://bugs.freedesktop.org/show_bug.cgi?id=8758](https://bugs.freedesktop.org/show_bug.cgi?id=8758)

However, there seems to be hope. Compiz (gnome-window-decorator) does not seem to work with this card, but the next version of Metacity (2.18) apparently does. So my hope is that it is only a matter of time until we get an OpenGL desktop with this card:

[http://gentoo-wiki.com/Talk:HOWTO_AIGLX#AIGLX_on_savage_video_card](http://gentoo-wiki.com/Talk:HOWTO_AIGLX#AIGLX_on_savage_video_card)

Cheers.

---

