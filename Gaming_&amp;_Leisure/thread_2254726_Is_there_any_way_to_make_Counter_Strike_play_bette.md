---
title: "Is there any way to make Counter Strike play better?"
date: 2014-11-29
forum: Gaming &amp; Leisure
---

### Post by philpope15 on 2014-11-29
I'll start with thanking anyone who has anything to add. I'm really surprised/satisfied with the amount of help these forums provide.

Anyways. I have a fresh install of Ubuntu 14.04 and installed steam and Counter Strike.
However, its slow. =(

I didnt install any other programs that might start when the computer starts up, I didn't think Ubuntu would come with an unnecessary start up programs like Windows does but I just don't know!

I did set the resolution to the lowest and details under the video settings to their lowest setting as well.

I am running an older laptop (the specs are above Counter Strike's "minimal requirements")
1.6 Dual Core intel Pentuim
1 gb Ram
'integrated' graphics.

It might just be too old and that's okay. I'm just wondering if there's any way to make it better. Thank you so much!

---

### Post by kostkon on 2014-11-29
It's probably graphics card related. I don't think you can do much about it.

But, what's your (I'm assuming) Intel graphics card anyway? To find out, give this in the terminal:
```
lspci | grep -i vga
```

It plays fine on my netbook with an GMA3150, even on the external monitor with 1600x900 res with the standard CS graphics settings.

---

### Post by philpope15 on 2014-11-29
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
phil@phil-Compaq-Presario-C700-Notebook-PC:~$

---

### Post by kostkon on 2014-11-29
> **philpope15 said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
phil@phil-Compaq-Presario-C700-Notebook-PC:~$
The card is pretty old (2006-7 vintage?) and you are already using a fairly recent version of the Intel driver so I don't believe [installing the latest]("http://www.omgubuntu.co.uk/2014/11/intel-linux-graphics-driver-installer-update") would make any noticeable difference.

You could also try installing a lightweight desktop environment (e.g. lubuntu-desktop) and running the game on that. It might improve the framerate a bit; again, that may not be enough to make the game playable.

I don't know what else to recommend.

---

### Post by Sef on 2014-11-30
moved to gaming and leisure

---

