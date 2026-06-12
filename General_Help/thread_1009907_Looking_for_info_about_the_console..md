---
title: "Looking for info about the console."
date: 2008-12-13
forum: General Help
---

### Post by asker on 2008-12-13
Hey there, Im a pretty long time user of Linux, and Ubuntu, and I can find my way around console commands pretty darn well. What I would like to know is, what IS the console? When I use the  Ctrl-Alt-F1 console, how does it communicate with the computer or the kernel? I read that it is just a emulator for the hardware console "VAX Station 100" or somthing like that. Why is it so different from an X session? They both display to the screen, so they should have more or less the same capabilities, right? I feel like I am really missing somthing. can anyone outline the difference? One more question, What is the difference between the term "console" and the term "terminal?" 

Thanks!

---

### Post by bluefrog on 2008-12-13
for the beginning I don't know.

a terminal is usually a program running in X session (so needing a window manager)
console is not running in X session

---

### Post by CatKiller on 2008-12-13
> **asker said:**
> Why is it so different from an X session? They both display to the screen, so they should have more or less the same capabilities, right? 

No. A virtual console (tty) doesn't have an X server running. So it can't do anything that requires X. Multiple windows, GLX acceleration, that kind of thing.

> One more question, What is the difference between the term "console" and the term "terminal?"

In general usage? Not much; they are often used synonymously. Normally *console* would refer to the "virtual console"; that is, one of the ttys. *Terminal* would refer to a command-line interface running in a Desktop Environment. This emulates the interface that you would get on the ttys, but since it's running on an X server, it is also able to spawn other windows or otherwise launch graphical applications.

Run **glxgears** in each to see the difference.

---

### Post by fguilhon on 2008-12-13
I really don't know all the details, but what I can say to you it that the console runs on a primitive video mode that defaults to 80x25 (that's lines x columns) video size. It is run by a primitive device driver.
Well, the console and terminal runs a program called the shell (usually the bash shell on Ubuntu). The shell have internal commands and envorinment variables but when you are issuing commans it is usually calling external programs, for example, ls is /bin/ls.... these progs communicate with the kernel using specific libs..
The X session uses a very different video mode run by more complex video drivers and so when you run a terminal it is really emulating console behaviour..
well, I hope it helped... I'm sure it's far from a complete explanation.

---

### Post by CatKiller on 2008-12-13
> **fguilhon said:**
> I can say to you it that the console runs on a primitive video mode that defaults to 80x25 (that's lines x columns) video size. It is run by a primitive device driver.

It doesn't have to, though. Mine's running at 1280×1024 (pixels). This is just a kernel option in GRUB. It can still display 32 (24) -bit colours, and can also display a nice logo in the background, if you like.

---

### Post by asker on 2008-12-13
Well thanks guys. Im gonna try to mess with the settings in GRUB (always a pain). Would there be a way to run both modes simultaniously on a single screen?

---

### Post by CatKiller on 2008-12-13
> **asker said:**
> Well thanks guys. Im gonna try to mess with the settings in GRUB (always a pain).

It's only a pain in that you need to reboot to test your settings. You can change the options from the GRUB menu, so you can test your settings with the minimum amount of reboot time and only change your menu.lst when you know that the mode you've picked will work. Changes in the GRUB menu are not persistent, so if it doesn't work you only need to reboot to get back to how you were.

You simply need to add a ```
vga=*VESAModeNumber*
``` argument to your kernel options to get a higher resolution. Tables of VESA mode numbers are freely available across the Internet. For example, I have vga=0x31B in my menu.lst.

You might find that, since the resolution of the framebuffer device is now higher than the default, the USplash splash screen looks peculiar. You can change the resolution of the splash screen by changing the *xres* and *yres* values in /etc/usplash.conf.

Setting prettification options (background graphics and such-like) for the virtual console used to be done by manipulating the **vesafb** kernel module. There might be newer modules in use these days - I haven't looked into it for quite some time. There's probably some useful information in the Customisation sub-forum.

> Would there be a way to run both modes simultaniously on a single screen?

I'm not entirely sure what you mean by this. The (realmode) setting that you put into your menu.lst will set the resolution for the whole of the boot process after the kernel has loaded, including starting the ttys. The X resolution for your Desktop Environment is entirely separate. The size of the Terminal window is 80 columns by 25 lines (but changes as you resize the window) and isn't affected by anything that you do to the ttys, since it's just an application that runs on X.

If you mean, "is it possible to have one resolution on tty1 and a different resolution on tty2?" I have no idea.

---

### Post by bodhi.zazen on 2008-12-13
Well, depending on how deep you want to delve ...

The console is managed by the kernel and dates back to a time before we had a graphical interface. These were sometimes termed "dumb terminals" and were those old green terminals + a keyboard.

You can increase the resolution and display graphics with framebuffer.

A terminal implies an X window system and is not managed by the kernel, but rather Xorg.

[http://znark.com/tech/serialconsole.html](http://znark.com/tech/serialconsole.html)

[http://www.vanemery.com/Linux/Serial/serial-console.html](http://www.vanemery.com/Linux/Serial/serial-console.html)

---

