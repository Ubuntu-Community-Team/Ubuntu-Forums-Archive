---
title: "boot screen"
date: 2013-02-15
forum: Desktop Environments
---

### Post by Puffin-ww on 2013-02-15
Hiya

When shutting down my Xubuntu 12.10 shows a IMO very nice screen:
blue background, "Xubuntu" in white, with a "progress bar".

When booting up, there is nothing at all. The screen is just black until the desktop is shown.

Is it possible to get a/the nice screen when booting up as well?

When I choose things in settings like "balou" or "mice", this has only an effect on the last second before the desktop appears.
But I would like to have something for the most part of the approx. 35 seconds boot time.

I also tried removing "quiet splash" in /etc/default/grub.
Again this only affected the last second before the desktop is shown, with the result that some text is shown then.

Many thanks.

Puffin-ww

---

### Post by sudodus on 2013-02-15
Try according to stinkeye's post in the following link

[[COLOR="Red"]http://ubuntuforums.org/archive/index.php/t-1701789.html[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-1701789.html")

---

### Post by Puffin-ww on 2013-02-15
sudodus, I did what you suggested.

The current design is the right one (as I said, I see it when it shuts down), and it's the only one (that my plymouth knows).

Creating /etc/initramfs-tools/conf.d/splash did show an effect:
For the second half of the booting time now the screen goes from "light-black" to "pitch-black". 

So we're getting closer. But why doesn't it show the xubuntu-logo ?

---

### Post by schragge on 2013-02-15
What's in your */etc/default/grub*? Please post the output of
```

grep '^[^#]' /etc/default/grub

```

---

### Post by Puffin-ww on 2013-02-15
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by schragge on 2013-02-15
Looks all right to me.

---

### Post by sudodus on 2013-02-16
> **Puffin-ww said:**
> sudodus, I did what you suggested.

The current design is the right one (as I said, I see it when it shuts down), and it's the only one (that my plymouth knows).

Creating /etc/initramfs-tools/conf.d/splash did show an effect:
For the second half of the booting time now the screen goes from "light-black" to "pitch-black". 

So we're getting closer. But why doesn't it show the xubuntu-logo ?

Stinkeye's tips in that link

[[COLOR="Red"]http://ubuntuforums.org/archive/index.php/t-1701789.html[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-1701789.html")

works for me with 12.04. I don't know, if something has changed in 12.10, so that it needs further tweaking. The only tip I have is that you try again, and do all the steps. Don't forget any step, for example to run ```
sudo update-grub
``` before reboot.

---

### Post by Puffin-ww on 2013-02-16
Thanks everyone.
It's working now.

It indeed also needed the GRUB_GFXPAYLOAD_LINUX setting in /etc/default/grub

See you

Puffin-ww

---

