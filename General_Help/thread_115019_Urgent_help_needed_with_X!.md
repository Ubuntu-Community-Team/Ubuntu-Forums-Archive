---
title: "Urgent help needed with X!"
date: 2006-01-09
forum: General Help
---

### Post by tappad on 2006-01-09
Ive been running ubuntu for a couple of months now but and been so very pleased!
Im sad to say that today my system crashed, and i dont know what to do.

I am now using the LIVE version, and really hopefull that some of you nice people out there can help me.

Here is what happens:

Everything boots fine, all the way till its time to start X (before login).
The system seems too freeze up and the upper half of the screen is filled with black (looks like its still in "console mode", or whatever) and the bottom half is filled with white colour. For about 5 seconds i can se the _ cursor (not the mousepointer but the inputcursor). Nothing really happens when i press any keys except, some flicker in the white regions when ALT + f1-f4 (maybe all the buttons, havent tried them all).
The first 2 times this happened i got an error message (blue screen, red box in the center) that X crashed and if i wanted to se errorlogs. Unfortunatly i belived that a reboot would take care of the problem.

The first time it happened was when i pressed CTRL+ ALT + Backspace to restart X, becouse the system got slower, and also VLC was hung up (Witch it does some times, usually no big prob.)

What ive been doing to, maybe, couse this error:

For the last couple of hours i was trying to get proftp up and running, tapering with accounts and such. 
I did do : 
mount -o bind /home/usr /home/usr2/usr 
Tamperd ALOT with users, adding, removing, changing homefolder, changing rights to folder.
also, as i said earlier, VLC crashed on me.. but everything was fine untill i pressed Ctrl + Alt + Backspace.

I really hope that someone could help me on this.

Best regards
David

---

### Post by naaman on 2006-01-09
Have you tried 'sudo dpkg-reconfigure xserver-xorg'?  This should rerun the debconf screens to automatically detect your video settings.

---

### Post by tappad on 2006-01-10
Thank you!

It worked, guess it was the graphics/screen then.

---

