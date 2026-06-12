---
title: "Mplayer full screen error - picture is still small."
date: 2005-03-20
forum: Desktop Environments
---

### Post by drasko on 2005-03-20
When I put a divx in mplayer, and push full screen button, screen becomes big, but the picture remains the same size (small), as it was before, and the black border is around it on the rest of the screen.

What's wrong?

What video drivers and codecs to use for divx. Currently I am using default mplayer driver and codec, I haven't touch preferences...

Thanks all,
Drasko

---

### Post by ups on 2005-03-21
Looks like MPlayer isnt using the correct video driver. Launch MPlayer, Right-click -> Preferences -> Video tab. Which driver is selected there?

For me, Full Screen works properly if I use xv. Try selecting that, and then restart MPlayer.

---

### Post by A-star on 2005-03-21
I had the same problems when I installed the ati-drivers that were in the repositories, I deinstalled them and with the driver that is included in xfree or xorg (depends on which verion of ubuntu you ar eusing) it worked without a problme.

I saw a solution somewhere on the boards, maybe this can help you, I didn't test it yet:
[http://www.ubuntuforums.org/showthread.php?t=3567](http://www.ubuntuforums.org/showthread.php?t=3567)

---

### Post by lorap on 2005-03-21
hi friend!
probably the codec you've downloaded just doesn't match the system or has a bug.haven't you tried run say "vlc" player?this player renders almost all filetypes known and needn't additional codecs been installed.if you're interested how to install it go to the Synaptic Package manager,after you've it open go to Settings-->Repositories.in the new window mark all options possible ignoring warnings.then press Ok button.then in the main window press Reload button.after the reload process completes press Search button and write in VLC.
change the search option to the "names and descriptions" and press Ok button.
once you've the player found mark it for install and press Apply button.
now you're done.
have a nice day!
pavel

---

### Post by kuleali on 2005-03-21
i had the same problem, get the mplayer with no gui, works for me!

---

### Post by Jonathan Drain on 2005-03-21
If you open the file via the command-line, use "mplayer -fs -zoom filename.avi" where filename.avi is your file. '-fs' opens it fullscreen and '-zoom' makes it actually resize to fit the whole screen.

---

### Post by gil-galad on 2005-03-21
You need to use the xv video driver instead of x11.

/etc/mplayer/mplayer.conf
vo=xv,

---

### Post by drasko on 2005-03-22
> You need to use the xv video driver instead of x11. 

Yes - that solved the problem. But I did not had to edit conf file, just to go to preferences, and switch to xv. Thanks a lot. Anyway, I dont know nothing about all those drivers and cocdesc - why X11 did not work, and xv is working? What codec to use (in the preferences pull-dovn meni there are a lot of them)? etc...

Drasko

---

### Post by LordCantenberry on 2005-03-22
Awesome, this fixed a problem I was having as well.  Thanks.

---

### Post by daschizoid on 2005-04-17
Its working as well with the GUI. Use "gmplayer -zoom" to start (or change it in the icon-properties), and suddenly its all good.

---

### Post by Snower on 2005-04-22
When I do xvinfo I see that my computer has XV support but when I try to open mplayer with the xv driver he doesn't find him and I can't pick him with the GUI version also can anybody help me how I can compile mplayer with the xv driver thank you

---

### Post by RaverDK on 2005-04-25
[QUOTE=gil-galad]You need to use the xv video driver instead of x11.

/etc/mplayer/mplayer.conf
vo=xv,[/QUOTE]
 Thanks for your help...

The part to correct my /etc/mplayer/mplayer.conf file helped me to beable to see video full screen.... 

Thumbs up guys!

---

### Post by logan2004 on 2005-04-28
cheers...

also make sure zoom=yes

---

