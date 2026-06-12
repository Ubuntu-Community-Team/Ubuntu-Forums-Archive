---
title: "How do i get (permanent) transparent windows with transset on Openbox?"
date: 2010-10-28
forum: Desktop Environments
---

### Post by Seeb on 2010-10-28
Hey there,

I want my Terminal to look transparent, just like this:
[http://box-look.org/CONTENT/content-pre2/81636-2.png](http://box-look.org/CONTENT/content-pre2/81636-2.png)

I tried to use xcompmgr with transset but 

1) after doing "transset 0.35" and clicking on the Terminal-window, it only stays transparent for as long as I don't close it or reboot => its not permanent. Next time it's non-transparent again

2) the WHOLE window is transparent, even the title- and menubar! But I just want to have the black textarea be transparent (like in the pasted screenshot)

But it somehow seems to be possible, since the screenshot is also taken from an openbox environment.

Any help?

Thank you! :)

---

### Post by mcduck on 2010-10-28
> **Seeb said:**
> Hey there,

I want my Terminal to look transparent, just like this:
[http://box-look.org/CONTENT/content-pre2/81636-2.png](http://box-look.org/CONTENT/content-pre2/81636-2.png)

I tried to use xcompmgr with transset but 

1) after doing "transset 0.35" and clicking on the Terminal-window, it only stays transparent for as long as I don't close it or reboot => its not permanent. Next time it's non-transparent again

2) the WHOLE window is transparent, even the title- and menubar! But I just want to have the black textarea be transparent (like in the pasted screenshot)

But it somehow seems to be possible, since the screenshot is also taken from an openbox environment.

Any help?

Thank you! :)

That's how transset works. There might be a way to write some script to automatically run transsset to set the trasnparencies for your programs, but transset alone will not do that.

And yes, transsset can only make the whole program transparent. It only sees a window, not what's inside it. It would be up to the program running inside the window to tell to draw some individual widget or area transparent, external applications can't do that.

edit: Sorry, but it doesn't look like there is any simple way to use transset automatically. Here's a guide for xterm, you might be able to use the same method to create launchers for other programs as well. [https://wiki.archlinux.org/index.php/Xterm_Automatic_Transparency]("https://wiki.archlinux.org/index.php/Xterm_Automatic_Transparency")

edit2: In the screenshot there are two programs that use transparency (xfce-terminal and tint2), and they both have built-in support for it which is why they have partial transparency.

---

### Post by Seeb on 2010-10-28
Hey there, thanks for coming back to me.

The strange thing is, that even though composite is enabled
("xdpyinfo|grep Composite" shows it) and xcompmgr is running, i just dont get ANY window to become transparent.

I did it exactly how they showed it in this short guide here:
[http://openbox.org/wiki/Help:FAQ#How_do_I_get_true_32-bit_transparent_windows.3F](http://openbox.org/wiki/Help:FAQ#How_do_I_get_true_32-bit_transparent_windows.3F)

I even tried it with the same app (urxvt) and it didnt work!

Btw: I'm using a fresh Lubuntu install.

I think Ill try to do an ubuntu server install and then install openbox over it, since I dont think that I am the reason for this isnt working ;)

---

### Post by gbestrada on 2010-10-28
Hello SEEB.

tha is easy.first open the terminal and on the menu bar click EDIT
 and select** profiles **.

In the new opened window select default and click **EDIT**.
then on the new opened window menu , click **BACKGROUND**
and look for where it says **transparent background** and select it.
and select the** opacity** you want .

And save/close the opened windows and you are done .

hope  it helps   :):):)

---

### Post by mcduck on 2010-10-29
> **Seeb said:**
> Hey there, thanks for coming back to me.

The strange thing is, that even though composite is enabled
("xdpyinfo|grep Composite" shows it) and xcompmgr is running, i just dont get ANY window to become transparent.

I did it exactly how they showed it in this short guide here:
[http://openbox.org/wiki/Help:FAQ#How_do_I_get_true_32-bit_transparent_windows.3F](http://openbox.org/wiki/Help:FAQ#How_do_I_get_true_32-bit_transparent_windows.3F)

I even tried it with the same app (urxvt) and it didnt work!

Btw: I'm using a fresh Lubuntu install.

I think Ill try to do an ubuntu server install and then install openbox over it, since I dont think that I am the reason for this isnt working ;)
I'm pretty sure you said in your first post that you can get them to become transparent, but they don't sty that way and the whole window becomes transparent.

That's what you get with transsset.

The programs that have built-in support for transparency don't need transset to do that. Just check each program's options and you'll find settings for transparency. (Can't say anything about URXVT, I've never used it myself.)

---

### Post by Seeb on 2010-10-29
@gebestrada
hey there,
i know how to set programs to be transparent, but the thing is, that they just dont become transparent when setting it ;)

@mcduck
yes, I get that with transset. But ONLY with transset!
Other programs I'm using that support transparency (Terminal, Tilda) just don't become transparent when i tell them to do so!

---

