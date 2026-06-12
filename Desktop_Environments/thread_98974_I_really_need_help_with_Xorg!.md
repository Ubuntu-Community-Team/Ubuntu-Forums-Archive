---
title: "I really need help with Xorg!"
date: 2005-12-04
forum: Desktop Environments
---

### Post by rozojc on 2005-12-04
Sorry if this count as reposting but I am really desperate and my other thread just vanished without recieving much help!

I am really desperate. I don't really know since when (I think since last kernel update) I've been having problems with Xorg. My laptop works fine and after a couple of hours suddenly processor use goes to 100% and it continues like that indefinitely. I end up having to kill the Xorg process, and everything then goes back to normal (at least for a couple of hours until it happens again)...

Can anyone help me out please? I have an Acer 3003LCi with a SIS M760GX graphics card. I already tried reconfiguring Xorg but it didn't help...

---

### Post by GreyFox503 on 2005-12-04
Try opening a terminal, then running "top".

Then just leave it running, and when your system starts this behavior, then check the window to see which process is misbehaving.

Also take note of any other programs you have running.  Hopefully its the result of an application rather than X itself.

---

### Post by rozojc on 2005-12-04
[QUOTE=GreyFox503]Try opening a terminal, then running "top".

Then just leave it running, and when your system starts this behavior, then check the window to see which process is misbehaving.

Also take note of any other programs you have running.  Hopefully its the result of an application rather than X itself.[/QUOTE]

I did that and the process that is taking 90 something percent of the processor is just Xorg!!!

---

### Post by art on 2005-12-05
Install treeps, and see what processes descend from xorg, when it goes crazy, maybe that will shed some  light...

---

