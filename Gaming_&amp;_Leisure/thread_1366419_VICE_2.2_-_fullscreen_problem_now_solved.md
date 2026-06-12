---
title: "VICE 2.2 - fullscreen problem now solved"
date: 2009-12-28
forum: Gaming &amp; Leisure
---

### Post by jamyskis on 2009-12-28
Many of you will probably already be aware, but VICE 2.2 was released on 22 December. For many people this may be fairly uninteresting, but given the problems that VICE has had with fullscreen in the past few years, there is one major change that many of you will more than likely greet with open arms - VICE now sports a SDL-based UI.

Now, it's not the most comfortable to use, but it is in keeping with the general C64-ish feel of the program and it does offer a couple of blinding advantages. One is that fullscreen works absolutely blindingly well with the SDL UI. Another is that there is an option to have the window scale perfectly to the resolution that you select using OpenGL.

For the time being, you will have to compile yourselves - when you do, remember to tell configure that you want the SDL interface using:

./configure --sdlui

Then, when you start x64, you can press F12 to call up the menu and select video options to enjoy your C64 nostalgia FINALLY in fullscreen glory!

---

### Post by farrell2k on 2009-12-30
Nice.  I can't wait to play Legacy of the Ancients.  The DOS port is too ugly.

EDIT:  I don't see 2.2 at viceteam.org.  Where id you get it?

---

### Post by Marller on 2009-12-30
[http://vice-emu.sourceforge.net/]("http://vice-emu.sourceforge.net/")
They moved everything to sourceforge a while ago. It's written at the bottom of your link.
viceteam.org seems to get updates at a slower pace.

---

### Post by LeFish on 2010-01-02
Hi!

I'm trying for hours now to get VICE 2.2 on my Ubuntu 9.10 to work in Fullscreen mode by typing in --fullscreen-enable as a ./configure option.

Now that I stumbled across your thread and tried your option "--sdlui", yet it did not work... - considering I'm pretty much a newbie to compiling my own programs. (But wanting to use VICE you seemingly dont get around it...)

Would you be o kind and explain to me how to get this option to work?
Will --enable-gnomeui still work?
Which packages do I have to have installed?

Thanks for your effort!

LeFish

---

### Post by jamyskis on 2010-01-08
Can you post the error messages that come up on the console?

---

### Post by Jammet2 on 2010-04-23
configure: error: unrecognized option: --sdlui
Try `./configure --help' for more information.

This sdlui ... mysteriously, configure doesn't know about it. At all.

Until you try 

./configure --enable-sdlui

Remember, it's always the little things.
Enjoy the little things.

---

