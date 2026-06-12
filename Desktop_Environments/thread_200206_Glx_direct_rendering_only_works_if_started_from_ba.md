---
title: "Glx direct rendering only works if started from bash"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Trab on 2006-06-19
I have a pecular problem, ive posted it a few times, but gotten very unhelpful/no response for all of them.
so i'm posting again, hoping i will be able to better explain it and get help this time.

when i start my machine from full shutdown (or reboot) and it starts X server (and auto-logs into gnome) it doesnt have direct rendering enabled.
if i then move my xorg.conf file to xorg.con and restart x it will obviously crash. if i copy the xorg.con back to xorg.conf and startx it works fine.

this is very annoying :-/
the only think I know that might have effected this is i started tweaking around with compiz/Xgl and then changed my mind (only partially fixing it...) i think something might be messed up in my gnome-startup but im not sure.
as i said, the same xorg.conf produces 2 different results.

as another note, if i do sudo startx instead direct rendering also works (so its not a 1 user vs another thing)

any help would be aprecated, its not enjoyable to have to restart X just to get this working.
thanks
Trab

---

### Post by leech on 2006-06-19
That is pretty annoying.  It could be in part due to 'thefuture' script that most of the Compiz/XGL Howtos explain to create is being loaded and crashes because Xgl is not there.

I'm not entirely sure what steps you took to remove Xgl, but the way I do it is to modify /etc/gdm/gdm.conf-custom so that there are # in front of all the Xgl stuff that you added at the end of the file.  Do this while still running Xgl if you can.  (otherwise copy that custom gdm back over, get into Gnome and then modify it) and also make sure before you log out to remove /usr/bin/thefuture from your Gnome-Sessions.  

Oops, I just reread your post.  Doesn't sound quite like you're having the problem that I was, but try all of this to fully 'uninstall' Xgl (it doesn't really uninstall it, just makes it not load).  

This is from memory, since I'm in Windows right now.  But hopefully this will help.

Leech

---

### Post by RAOF on 2006-06-19
It sounds like you're still using the XGL X-server.  Which you could without knowing it, because it looks just the same as the normal Xorg server, but direct rendering doesn't work ;)

Perhaps try **sudo aptitude remove xserver-xgl**?  If, after doing that, it doesn't start X from a reboot, then you know what was wrong (and you'll need to edit /etc/gdm/gdm.conf-custom) ;)

---

### Post by mzembe on 2006-06-20
I had a problem like that. I could get direct rendering to work but not Xgl, but if I stopped gdm (run /etc/init.d/gdm for instructions - it's easier than renaming your xorg.conf everytime.) and started X as root I could Xgl would work with the freaky jello windows. I double checked my xorg.conf to make sure the dri mode was set and tried editing the gdm.conf & gdm.conf-custom with different standard displays to see if I could get it to run on display :1 and all that.
Finally, I got tired of messing with it. The 9800pro and X700 turn my pc into an oven. I just put a nvidia quadro2 in, it's passively cooled, doesn't require a heatsink, etc. It even plays counterstrike allright in windows. I think I'm gonna wait another 6 months or so before screwing with it again. Maybe rasterman will whip us up a 3d enlightenment. lol.

Oh yeah, I was getting Xgl to work as root because I had a custom .xsession file to start compiz - but it wouldn't work with a user defined .xsession and gdm. I wanted to have Xgl on a per user basis for experimenting. 
At some point I had limited Xgl/compiz through editing the global gdm.conf-custom session but had to change whatever that standard display variable in the plain gdm.conf because the DRI (fglrx -display :1) was only functioning on :1.
I noticed on the last few dapper updates that the drm libs, mesa libs, and Xgl server have changed a couple of times. Maybe it has been fixed.

---

