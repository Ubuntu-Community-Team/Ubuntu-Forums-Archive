---
title: "another problem with display"
date: 2021-06-12
forum: Desktop Environments
---

### Post by jgw on 2021-06-12
I now have a machine that boots to a 1024x768 on first boot in the morning.  To fix that I have to re-boot again and then it boots to 1920x1080 (the right one).  When it first boots I goto the setting and check the display and 1024x768 is the only resolution available. On second boot its got a lot of available settings. I am running with an nvidia display card. When I check for additional drivers there are none. I swear there used to be an additional driver being used! Anyway. I have no idea if this is even solvable.  I have tried to reset the resolution in the terminal but those won't work either (tried, amongst others, 
sudo xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
which failed

I figured it was time to stop messing around and try and get some help before I blew something up.

Thank you..............

---

### Post by MAFoElffen on 2021-06-14
xrandr changes only take affect for the current session. Once you shutdown, it goes away. To make that persistent, you would enter a working xrand set command into the user .bashrc file... [COLOR=#ff0000]**But do not do that!**[/COLOR] That is an outdated way of doing that by at least 10 years.

Off the top of my head, there are at least 10 ways to do what you want. AS long as we are talking about a real machine (not a VM), your video GPU and Display have the capabilities of doing it. You  didn't say what those were... Which the settings for the video driver beings used for that would also set that. You also didn't mention if you were using XServer or Wayland... 

I see in your Sig line that you Have NVidia NV*$, which uses the generic opensource nouveau driver... Which if you are using Xorg, then you could set that in an xorg.conf file... But there is something to try first, which is simpler.

If you change your grub default file, it will set the mode in grub to the resolution you want, inherit that change kernel KMS, then in the TTY session in the next layer. Then inherit into the Linux Graphics Layer (the upper layers of the stack). It's like a quick-start leg up... Look at post of one the Sticky in my signature line. Theres about 10 ways to make your resolution persistent for the Linux Graphics Layer where the Desktop lives.

The file is /etc/default/grub. Change the commented line that says
```
#GRUB_GFXMODE=680x480
```
And edit it with privilege's to say:
```
GRUB_GFXMODE=1920x1080
```
Then you have to update the grub menu so it picks up that change.
```
sudo update-grub
```
There are also about 3-4 kernel boot options to tell the kernel KMS to do that in that layer, if you want to do that there... I think it's better to do it in those layers, so you set those modes before the Plymouth boot screen.

There is a wealth of knowledge for just about anything you want to do with the Linux Graphics Layer and Xorg XServer in that Sticky... [

---

### Post by jgw on 2021-06-15
Thank you for the reply!

Today I started both machines.   Guess what?  They both booted properly!    The only thing I can think of is that I have, every day, been updating ubuntu because there is always something to update and most of the time its ubuntu itself that's updating.    Perhaps that one got fixed (its the only thing that's changed)

Anyway, I am going to set this as solved and save your reply if it should happen again.

---

### Post by MAFoElffen on 2021-06-15
Good to hear that! Good luck and enjoy.

---

