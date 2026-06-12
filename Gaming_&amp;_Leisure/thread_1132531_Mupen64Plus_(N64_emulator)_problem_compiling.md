---
title: "Mupen64Plus (N64 emulator) problem compiling"
date: 2009-04-22
forum: Gaming &amp; Leisure
---

### Post by Mr. Hibba on 2009-04-22
I tried the pre-built package of Mupen64Pus, but I couldn't open the controller configure window. So, I grabbed the source code from [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/) and tried to compile it to see if it would work better.

Following the included instructions, I typed "make all" in the terminal and ran it. I got an error message which, according to my Google search had something to do with graphics files/drivers. It read as "/usr/bin/ld: cannot find -lGL". However, I installed/uninstalled packages and am now not getting that particular error.

Now, I am currently getting the following error message: /usr/bin/ld: cannot find -lSDL_ttf. What do I need to do to fix it?

I'm not a very advanced user (Would almost say "newbie," except that I've used Linux off and on for a while. I guess I would be more of a "inexperienced user.") I would appreciate the answer having some extra explanations,as needed, to help to help along this inexperienced user. :)

---

### Post by wingnux on 2009-04-22
Run the pre-built package from the terminal, try to configure your controller and post the terminal output here.

---

### Post by Grishka on 2009-04-22
> **Mr. Hibba said:**
> I tried the pre-built package of Mupen64Pus, but I couldn't open the controller configure window. So, I grabbed the source code from [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/) and tried to compile it to see if it would work better.

Following the included instructions, I typed "make all" in the terminal and ran it. I got an error message which, according to my Google search had something to do with graphics files/drivers. It read as "/usr/bin/ld: cannot find -lGL". However, I installed/uninstalled packages and am now not getting that particular error.

Now, I am currently getting the following error message: /usr/bin/ld: cannot find -lSDL_ttf. What do I need to do to fix it?

I'm not a very advanced user (Would almost say "newbie," except that I've used Linux off and on for a while. I guess I would be more of a "inexperienced user.") I would appreciate the answer having some extra explanations,as needed, to help to help along this inexperienced user. :)

[apt://libsdl-ttf2.0-dev]("apt://libsdl-ttf2.0-dev"), [apt://libgl1-mesa-dev]("apt://libgl1-mesa-dev"), and make again.

---

### Post by Mr. Hibba on 2009-04-23
> **Grishka said:**
> [apt://libsdl-ttf2.0-dev]("apt://libsdl-ttf2.0-dev"), [apt://libgl1-mesa-dev]("apt://libgl1-mesa-dev"), and make again.

Thanks, looks like that did the trick!

Thanks wingnux, too!

Mr. Hibba.

---

