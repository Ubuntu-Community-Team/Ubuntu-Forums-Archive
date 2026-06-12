---
title: "ATI - 3D acceleration issue"
date: 2006-09-05
forum: Desktop Environments
---

### Post by rlynch on 2006-09-05
So I want to use XGL(of course), yet I don't think I can, because ubuntu doesn't setup 3d acceleration out of box on my ati card.

I have a ATI Radeon Mobility 320M.

Does anyone else have this card, and was able to set this(xgl) up correctly? If so, what how-to did you use.

Or does anyone know how I can get Just 3d acceleration setup on this card.

When I go into system settings(kde) and click display, then change the video card driver to the proprietary driver, it hangs before showing the login screen. Just freezes at the splash screen before loading the login splash.


Thanks in advanced to anyone who can help with this issue.

---

### Post by x64Jimbo on 2006-09-05
XGL support for KDE is really shaky right now. If you can't wait for the eye candy, install the GNOME desktop and enjoy it right away. I'm still waiting for stability before I get it going on my KDE box. 
As for your video card, you should be ok -- check out EasyUbuntu for installation of your 3D driver as well as almost every piece of bonus software that you could ever want like DVD decryption, mp3 support, flash player, etc.

---

### Post by rlynch on 2006-09-05
I did use easy ubuntu, and installed the ATI 3d drivers, but again it does the freeze/hang thing.

I've done 4-5 format/reinstalls of ubuntu getting things from distorted video to the freezing at the splash screen.

---

### Post by x64Jimbo on 2006-09-05
Apologies! I didn't look up your video card model. From what I can tell, the entire Internet is clueless as to how to get that card working with 3D support. I saw some references that SUSE has a proprietary 3D driver for that card, and that it works, but it looks like you have to be running their kernel for it to work, and that doesn't help you out here much.

---

### Post by rlynch on 2006-09-05
Yea, I have been clueless on what to do as well.

I wanted to try the kororaa .2 xgl live cd as a final test, to see if the laptop could do it. Figured if the live cd didn't work, then I could abandon my quest.

I guess I'll do a duel boot on my desktop, and see if I can get it working on there(nvidia).

But yea, if anyone has any suggestions as to what I can do, thanks in advanced.

---

### Post by rlynch on 2006-09-07
Very Very Interesting.

I see that the Kororaa Xgl Live CD works on my laptop, with this ATI card.

Wobbly windows, cube desktop, it comes with an xgl shortcut file on the desktop that gives a list of commands zooming, transparency, etc. And it all works.

I dunno how to drag a window across screens on the cube, but if i do CTRL+ALT left/right.


So, how can this work on kororaa and not ubuntu. . .?

---

### Post by x64Jimbo on 2006-09-07
I am not sure. I have also played around with kororaa, but not on my ATI notebook. I might need to do so now. You might try looking at the config files that the LiveCD makes for itself to see if there's something they're doing differently.

---

### Post by rlynch on 2006-09-07
So after some more testing, I had it working on ubuntu last night around 1am - 2am.

The only thing that didnt work was the window borders were gone. After some searching here I read that if I typed in 'metacity' in a terminal after it boots, then they will appear.

Odd thing is I used the supposed 'out dated' how to, when trying the new one(installing csm, with lib packages, mesa, etc) then it broke it. So now tonight i'll have to do yet another format/reinstall. When it boots, it loads everything, goes black to fade to the splash/login screen, then shows just the kubuntu image, and hangs/freezes.

I thought the borderless windows was due to using kde, but when switching to gnome it did the same thing.


If anyone has any tips on how to fix this(even reverting back to default) without having to format the partitions, and reinstall everything from disc again, I would be very greatful.

---

### Post by rlynch on 2006-09-07
So the re-install is complete, working off a fresh install now(haven't even done easyubuntu or automatix yet).



[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

that is the how-to used that get's it to work in both kde and gnome, for my ati card, except for the window borders.

Later tonight, or most likely tomorrow I'll do this again, but this time see if the 'metacity' command fixes the borders.

---

### Post by rlynch on 2006-09-08
Holy guacamole Batman!

My geek level went up by 2! this morning around 4am. Using three different how-to's, I have finally got xgl/compiz running on my laptop. With CSM, csm themes, etc.

Window borders were fixed by installing csm, and csm themes. Then instead of loading gnome-window-decorator, i loaded csm.

(the metacity thing I read did not work)

So I do a glxgears in terminal, to test my fps, and this is my output, is this good?

```
rlynch@rlynch-laptop:~$ glxgears
392 frames in 6.1 seconds = 63.889 FPS
480 frames in 6.2 seconds = 77.749 FPS
480 frames in 6.7 seconds = 71.848 FPS
474 frames in 5.8 seconds = 81.980 FPS
684 frames in 6.0 seconds = 113.934 FPS
704 frames in 5.4 seconds = 129.784 FPS
570 frames in 5.1 seconds = 112.425 FPS
348 frames in 5.9 seconds = 58.942 FPS
480 frames in 6.2 seconds = 76.862 FPS
480 frames in 6.3 seconds = 76.190 FPS
479 frames in 5.8 seconds = 82.853 FPS
360 frames in 5.9 seconds = 60.557 FPS
360 frames in 5.9 seconds = 61.175 FPS

```

Any time xgl does something, like making a window wobbly, maximizing, even the wobbly tooltips, make the system usage go to 50%-80%. Also when playing a video in vlc, it doesn't visually lag, but I can just tell it's having *some* issues while playing it. I can rotate the cuble while it's playing, full screen, and it doesn't pause, lag, or anything, but like I said, I can just tell it's not playing at 100% ability/speed.

Should the fps be higher in my glxgears. The spike up to 100 fps is from me rotating my cube. When coming back to the side(of the cube) with the image of the gears running, it drops back down to 50.

---

### Post by Anthem on 2006-09-10
> **rlynch said:**
> Holy guacamole Batman!

My geek level went up by 2! this morning around 4am. Using three different how-to's, I have finally got xgl/compiz running on my laptop.
Can you post links to these how-tos?  I don't especially care about Compiz effects, but I'd love to have the GPU take over all of the 2D stuff.  Right now the graphics feel sluggish.

I'm impressed that you did all of this on a 320m.

---

### Post by rlynch on 2006-09-12
I would suggest only using this how-to if you own a HP Pavillion ze4805us Laptop, or have the ATI Radeon Mobility 320m Video card.

The first thing I did was do this walk through.
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

In my Xsession file I can switch this to gnome or kde, and both work(as much as they work at this point). My friend tried this how-to using the nvidia/gnome settings, and it broke his install(like so many other how-to's did for me).

At this point I would suggest restarting into your 'default' session at the splash login menu, to see if you get what I get.

For me this how-to gets the effects of xgl/compiz working, but the gnome-window-decorator themes that is loaded in Xsession file doesn't work with compiz/xgl. This means the 'window borders' do not show up, so no minimize, maximize, close, file, edit, view, etc, or status area. To fix this you have to install the cgwd and cgwd-themes by doing.

sudo apt-get install cgwd cgwd-themes

Then logout of your session, and log back into your default session, and it should work(or at least did for me).

---

### Post by Anthem on 2006-09-12
> **rlynch said:**
> I would suggest only using this how-to if you own a HP Pavillion ze4805us Laptop, or have the ATI Radeon Mobility 320m Video card.

The first thing I did was do this walk through.
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)
Wait, what?  All that walkthrough does is install XGL.  How did you get the 320m to use full acceleration when the open-source driver doesn't work and the closed-source driver doesn't work either?

---

### Post by rlynch on 2006-09-12
I didn't. lol

I got xgl/compiz working without 3d acceleration. When all other how-to's tell you that you have to have 3d acceleration working before xgl/compiz works.

Talk about miscommunication. Sorry man.

---

### Post by Anthem on 2006-09-17
> **rlynch said:**
> I didn't. lol

I got xgl/compiz working without 3d acceleration. When all other how-to's tell you that you have to have 3d acceleration working before xgl/compiz works.

Talk about miscommunication. Sorry man.
Oh, I get it.

Bummer.

---

