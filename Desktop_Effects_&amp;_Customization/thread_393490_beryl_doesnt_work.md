---
title: "beryl doesnt work"
date: 2007-03-25
forum: Desktop Effects &amp; Customization
---

### Post by ThumbBumpkins on 2007-03-25
i just installed beryl, but nothing has happened. the emerald icon is present and beryl seems to be running, but all my windows look exactly the same and none of the effects are working. i have reinstalled my nvidia drivers with no apparent problem, and I have restarted my desktop multiple times, but no matter what i do it still seems to not be working. any ideas what the problem is?

edit: i just restarted my computer one last time, and now X doesn't work at all. when i manually reinstall my nvidia drivers again it does work, but still no beryl.

---

### Post by daynah on 2007-03-25
The icon that needs to be in your menu bar needs to be the beryl icon, not the emerald icon (red like a ruby, not the green emerald). Emerald is the name for kinda like the theme pack. If you could go to terminal and type in "beryl-manager" it should open it up.

When it's open up, right click and go to "Select Window Manager" and see if it's on "Beryl" or "Metacity." If it's anything like my Beryl, it sometimes just stays on Metacity. Remember, Beryl is in version 0.2. Talk about a beta!

That's just one way it may be messing up, but I wanna make sure you have -beryl- open, when you describe a "emerald icon" present, it makes me wonder if you actually have it running.

---

### Post by esodin on 2007-03-25
Did you right-click on the beryl icon and select beryl as your desktop manager? It should be the second or third option from the top.

---

### Post by ThumbBumpkins on 2007-03-25
sorry, i did mean the beryl icon. it is a red icon, and when i right click on it, it does in fact say that beryl is my default window manager, but it still looks like metacity is running.

---

### Post by Ash1984 on 2007-05-13
I have the exact same problem. Also when I enable emerald themes, all title bars just become invisible.

---

### Post by dr.silly on 2007-05-13
how recently did you install beryl? this sounds like what's happening to me. I just upgraded and beryl isn't working.

---

### Post by dr.silly on 2007-05-13
right click on the beryl icon and Beryl Settings Manager Up at the top you're supposed to see more than just General Options but that's all mine says after the upgrade.

---

### Post by Kalior on 2007-07-19
same problem as ash, will someone please help the noobz

---

### Post by tyreck on 2007-07-24
Similar problem as I've read in countless threads, one of them matched really nice but now I can't find it again.

So. as is a common started, "I'm new!" (6 hours, give or take {and that is to Linux, not just Ubuntu)

I've seen a few people mention "Feisty", I don't know what that is.

I JUST installed the Ubuntu 7.04 disk, and loaded Beryl and Emerald, Beryl is running (separate issue; I can't get it to start up automaticly after following the instructions someone posted to add it to the startup in sessions)

> tyreck@tl:~$ glxinfo |grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: MOBILITY RADEON 9600

When I try to select Beryl as the Window Manager everything flashes and then it's still on Metacity when I look again. Emerald is selected as the Decorator, but since Beryl isn't actually active neither is it.

I've installed using the Add/Remove Programs, from the Terminal and with Synaptic Package Manager (like Synaptic the best so far I think) in that order. I then removed everything and started over using only Synaptic. Same thing.

If I deselect "Launch fall back window manager if Beryl crashes" and then select Beryl it will stay on Beryl, but still nothing works.

I'm no genius but I think I've deduced that it's crashing (duh right?)

So!, anyone have anything else I could try? I would be eternally in your debt.

---

### Post by Runamok on 2007-07-24
Good luck to those new Ubuntu and Beryl, 

Unfortunately, Getting 3D applications to run nicely with Ubuntu is not so much plug and play.  It takes some experimentation, and some free time.  Don't give up! THIS  is what trying out a new  OS is all about.  If you have a will , and the eye-candy is worth it, you can get beryl to work!  If anything, check the sticky's at the top of the forum, then Google is your friend!  

First, [Do you have the right Graphics card for Beryl?]("http://www.phoronix.com/scan.php?page=article&item=730&num=1")

The brand (Ati or Nvidia) of graphics card is important.  If you have an Ati card, then you'll have to remove the pre-installed drivers and replace them.  You'll also have to make some changes to a file called xorg.conf (be careful!) I can confidently suggest the following tutorial. [ Installing Beryl on An Ubuntu Feisty Fawn with an Ati Radeon Graphics Card]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

If you have an Nvidia card, it seems easier, but I don't have any experience with that.

Good luck!

---

