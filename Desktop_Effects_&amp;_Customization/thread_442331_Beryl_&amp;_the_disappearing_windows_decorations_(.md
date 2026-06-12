---
title: "Beryl &amp; the disappearing windows decorations (Feisty) ....solved"
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by meanmrmustard on 2007-05-13
After hours of googling and finding the problem not only with Ubuntu but Gentoo, Arch and others - and following recommendations on each page that didn't resolve the issue, I stumbled on this page:

[http://forum.beryl-project.org/viewtopic.php?f=47&t=6088](http://forum.beryl-project.org/viewtopic.php?f=47&t=6088)

It's in German and it's a different problem, but Andreas posted his config file....

I added  this to the top of the  Section "Screen" 
in /etc/X11/xorg.conf:

        Option "AllowGLXWithComposite" "True"
        Option "RenderAccel" "True"
        Option "AddARGBGLXVisuals" "True"
        Option "AddARGBGLXRootClipping" "True"

 ....and viola!

My windows decorations are back :biggrin: 

I suspect that the "Option AddARGB...." line is what did the trick - it was suggested in another thread to add that line to another section of xorg.conf but the problem still persisted.

Hope this helps you too.

---

### Post by Ateo on 2007-05-13
[QUOTE=meanmrmustard]I added  this to the top of the  Section "Screen" 
in /etc/X11/xorg.conf:

        Option "AllowGLXWithComposite" "True"
        Option "RenderAccel" "True"
        Option "AddARGBGLXVisuals" "True"
        Option "AddARGBGLXRootClipping" "True"[/QUOTE]

Truely amazed you're not having issues as the first 2 options belong in your "Device" section (where you define your video driver).

The thread is in german so I don't understand what they are saying.. but it's the first time I've ever seen that configuration and.... it's wrong...

---

### Post by meanmrmustard on 2007-05-13
> **Ateo said:**
> Truely amazed you're not having issues as the first 2 options belong in your "Device" section (where you define your video driver).

The thread is in german so I don't understand what they are saying.. but it's the first time I've ever seen that configuration and.... it's wrong...

The only issue I seem to be having is that emerald themes aren't working.
I don't understand German either but  no suggestions seemed to resolve the issue for me and several others so I took a shot.

I've moved the first two options to "Device" and everything has remained the same.

---

### Post by Ateo on 2007-05-13
Well, I suppose I shouldn't have used the word issues now that I think of it. Either way, you won't 'see' a difference by putting those 2 options in your "Device" section since they are just ignored when you put them in the "Screen" section. Granted, sometimes, you can have the oddest lines in xorg.conf and you can still boot. But that doesn't mean it's correct and logs will show it. The 2 options are very specific to your video driver.

The goal when configuring X is to have no errors in the X log file. =)

I may be totally wrong but I suspect I'm not. But I'm biased. hehe...

---

### Post by lammer on 2007-05-13
Just posting to say HUGE THAAANKS!!!!! that strange configuration worked for me too!!!

Hey thanks for sharing!

:guitar:

---

### Post by Vladtux on 2007-08-03
Dammit!!! :lolflag:


Work perfect for me!!! Thanks!!! Dude

Viele Danke!!!


:D

---

### Post by sicknor on 2007-12-07
Very good , thanks a lot dude.
Worked perfect on my debian sid :)

---

