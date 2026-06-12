---
title: "Problem with beryl"
date: 2007-06-07
forum: Desktop Effects &amp; Customization
---

### Post by Flikoman on 2007-06-07
I'm new here as you can see and I installed Linux Ubuntu 7.04 Feisty Fawn yesterday! Everything was fine, even beryl, until Exaile! program freezed and I used xkill command and by mistake I clicked on the panel at the bottom of the screen. Then everything dissapeared and I have restarted my computer and since then beryl doesn't work. I tried to reinstall it and everything, but simply it won't work! Any ideas??

---

### Post by Soybean on 2007-06-07
Well... killing the panel shouldn't have broken Beryl. At least not permanently. ;) Was this the first time you rebooted after installing Beryl? 

If the red jewel is there, right-click on it, go to "Select Window Manager" and pick "Beryl". If it's not there, try typing "beryl-manager" in a terminal, and see what happens. 

If neither of those suggestions help, can you be more specific about how it "doesn't work"? Mainly, is the jewel there, and are there any error messages?

---

### Post by Flikoman on 2007-06-08
No, it wasn't the first time I rebooted my computer! I've tried everything and beryl still doesn't work! When I try to select BERYL in section SELECT WINDOW MANAGER in the red jewel it automaticaly returns to METACITY. I have discovered why beryl doesn't work, and the thing is that when I type beryl in terminal, this error appers: CHECKING FOR XComposite Extension: failed, no composite extensions. Any ideas how to fix that? Thanks in advance...

P.S. My graphic card is Geforce FX 5900!

---

### Post by Soybean on 2007-06-08
Ah, there we go. The Composite extension is almost certainly the problem. I can think of two main ways it could be broken.

First, the easier one: perhaps your restricted nvidia driver somehow got disabled. Go to System->Administration->Restriced Drivers Manager and enter your password. Make sure the "enabled" checkbox is checked beside your NVIDIA accelerated graphics driver.

It may want you to restart X or reboot... actually, even if it doesn't, I'd reboot anyway, just to be sure.

If that doesn't work, you may need to fiddle with your xorg.conf a bit. You can either try fixing it yourself (just look for references to "Composite"), or post it on here and someone should be able to look at it and give you some advice. :) The file is at /etc/X11/xorg.conf in case you're not familiar with it. And it's pretty important, so make sure you make a backup copy of the working one before changing it!

---

### Post by EricWiz on 2007-06-08
I had this happen, or at least something like it. What I did was disable the restricted driver for my Nvidia card, restart X (ctrl-alt-backspace) then go in and enable the restircted driver again. 

That had worked for me. I hope that helps!

---

### Post by Flikoman on 2007-06-11
I've made it....THANK YOU GUYS..you've been very helpfull!

I've got one more question...see the "X" button on the upper right side of the window...it's messed up! Any ideas how to fix that?

[IMG]http://img114.imageshack.us/img114/9963/screenshot1xj9.png[/IMG]

P.S. Sorry for my english...

---

### Post by Soybean on 2007-06-11
I find that sometimes my buttons get messed up when I'm changing themes in emerald. Some things that sometimes help:
1) Change the theme and then change it back (Right click on the beryl icon, then go to the "emerald theme manager" to change themes).
2) Reload the window manager (right click on the beryl icon, pick "Reload Window Manager").
3) Restarting X (make sure you save anything you have open, then press ctrl-alt-backspace).

On the other hand, your problem looks a little different from what I've experienced, so if none of those things help, hopefully someone else will have an idea.

---

### Post by Flikoman on 2007-06-11
Thank you anyway, but that didn't help...any more ideas?

---

### Post by Soybean on 2007-06-12
Hmm. Maybe more information would help. Were you able to change the theme with Emerald? If so, are other themes also missing buttons?

---

### Post by Flikoman on 2007-06-13
I think i solved the problem. In emerald there is a BUTTON section and I've selected back_close.png and now it works fine. THANKS AGAIN

---

