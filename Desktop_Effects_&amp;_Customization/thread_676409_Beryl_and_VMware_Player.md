---
title: "Beryl and VMware Player"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by theforce117 on 2008-01-23
Hello all,

The first thing I want to mention is that I'm new to Ubuntu. I encountered a problem after I installed Beryl. I couldn't find any topic on this forum that related to this issue.

After I installed Beryl, I was able to see the Beryl-Manager and I had an icon from Beryl on my desktop. But I didn't saw any kind of animation.

I installed Ubuntu from VMware player. In the tutorial where I learned how to install Beryl they mentioned I had to install the latest nvidea drivers (9xxx). So I did that, logged out and in to make the changes take effect. Then my screenresolution and videocard wasn't detected anymore which resulted in a very small display. I looked in the settings and saw my videocard was a "vesa - Generic VESA". I have a nVidea 8600M GT 512mb. So I changed the videocard in the settings. Also I changed the resolution to Plug & Play 1440 * 900. I saved the changes, but now my whole ubuntu is not readable anymore. :(

[IMG]http://www.univertal.com/ubuntuproblem.JPG[/IMG]

:confused::confused:

If I look at the sessions I see only GNOME and something like X Viewer (next to the GNOME failsave and terminal). So I don't think I'v got XGL or anything installed.

As I'm new to Ubuntu, everything is getting to complex for me. So I have installed Ubuntu via VMware Player, installed Beryl but no XGL or something. Then I installed the newest nvidia drivers, my screentype/resolution and my videocard wasn't detected anymore. I tried to manually select the good ones, then my screen get's fuzzy. Is anyone able to help me? :confused::confused:

---

### Post by theforce117 on 2008-01-23
Some extra information you might need: I use Ubuntu 7.10.

And here's a screenshot of my sessions.

[IMG]http://www.univertal.com/ubuntuproblem2.JPG[/IMG]

Next to this: the loginscreen is bigger then my screensize, although I thought I set it to 1440*900 (my computers max. resolution). And when I logged in it's suddenly resizing to about half the size of my screen (as can be seen from the first screenshot). As you can see Ubunto is normal when it's in the login menu. But when I log in it get's fuzzy like in the first screenshot... So does anyone know how to let nVidea recognize my videocard etc. and how to make my screen back to normal? Thanks in advance

---

### Post by scxtt on 2008-01-23
if you have ubuntu as a VM running in Windows you _can't_ use 3D effect / compositing (i.e. Beryl) w/in the VM ...

---

### Post by theforce117 on 2008-01-23
Thanks for the quick answer!!

Why can't there be any 3d effects with VMware player? I thought VMware pretends like it's a computer so real that the OS thinks it's started on a real computer instead of an virtual one?

Next to that, do I have to install Ubuntu again in order to fix that weird screendisplay?

---

### Post by scxtt on 2008-01-23
the VM doesn't have direct access to your video card ... so the VM is basically using a virtual video card (VMware SVGA II) that isn't as powerful as your physical card ... i'm sure there'll be a day when it happens ...

you'll need to disable beryl to be able to use the VM again ... i would think that you should still get a login screen, maybe login to a different session ... maybe you have a ~/.beryl directory that could be removed so it doesn't start w/ your default session ...

looks like it might be in ~/.config/ and/or ~/.gconf/apps/compiz

---

### Post by theforce117 on 2008-01-23
Thanks for your help. The only session I can get into is the one with the terminal. But for some reason it uses a different keyboard layout, so I can't find the ~, the / and the y anymore :lolflag:. Because it's 1:48 AM now over here, I'll take a look at it tomorrow. I tried to find a folder named "Beryl", but yet without a result.

Thanks :)

---

### Post by theforce117 on 2008-01-24
Hey,

I used the terminal to try to find Beryl, but without any result. There wasn't a "compiz" folder in ~/.gconf/apps and there was no beryl map or something related in ~/.config.

I also had a look in other maps, but I wasn't able to find where Beryl is located.

---

