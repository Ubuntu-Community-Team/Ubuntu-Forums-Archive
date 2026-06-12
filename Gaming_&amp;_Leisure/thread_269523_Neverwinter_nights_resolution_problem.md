---
title: "Neverwinter nights resolution problem"
date: 2006-10-01
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2006-10-01
I can start up and play nwn, however, if I try to change the resolution, the game crashes.  If I try to manually change the resolution in the nwn.ini file, the game does not start up.  In addition, if I run the game in fullscreen mode, the game goes off the edge of my monitor, but if I run it in windowed mode, it takes up the full screen, but is offcentered.  I currently running the game at 800x600, and my display is set to 1024x768.  Any help?

---

### Post by VDM on 2006-10-02
Can you save the game?
Make sure the files are writable to the game.

---

### Post by Naegling23 on 2006-10-02
yea, I can save the game.  Playing it is not the issue, it runs fine.  I just have to run it at 800x600, and the screen is not centered at all.  In fact, part of it runs off of my monitor.

---

### Post by leech on 2006-10-02
How about some info?  What video hardware are you using, and driver?  Do you have any other special video settings (like water effects, etc.)  

Leech

---

### Post by Naegling23 on 2006-10-02
I'll try my best to give you all the info I can (I'm at work, so I dont have my computer in front of me).

I have an nvidea 6800gt graphics card, with the nvidea drivers installed.  Doom3 runs without a problem, at the second to highest graphics level.  I have tried enabling all the graphics settings, and boosting everything up to max in nwn, and I have also tried to uncheck all the graphics settings, and set everything to minimal.  Either way, it wont run at anything other than 800x600.  When I run 800x600, the image is not centered on the screen.  Like I stated before, my desktop resolution is set to 1024x768, so its not like my display cannot handle it.  If I try to change the settings in game, it crashes to the desktop, and if I try to change them manually, it doesnt start.  I also do not notice any difference between running in windowed mode and fullscreen mode.  

Is there any more specifics you would like me to try to provide?

---

### Post by Naegling23 on 2006-10-02
alright, here is a little more info.  I changed the nwn.ini file to a resolution of 1024x768, then tried to launch using konsole, here is what I got

naegling23@naegling23-kubuntu:/usr/local/games/nwn$ ./nwn
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x138
  Serial number of failed request:  106
  Current serial number in output stream:  108


I have no idea what this means

---

### Post by Perfect Storm on 2006-10-03
Have you pathed NWN?

Is your xorg setup to use the res. you want in NWN?

---

### Post by Naegling23 on 2006-10-03
I run doom3 at 1024x768, and that is my desktop resolution, so I dont think its a problem with xorg....I guess it could still be, but that would be really odd.

Im not sure what you mean by pathed to nwn.  I created a launcher in my kmenu which launches the game fine...provided that I run it at 800x600 (althouth the image is not centered on the screen).  If it was a pathing problem, it wouldnt run at all correct?

---

### Post by Perfect Storm on 2006-10-03
sorry, I mean patch.

---

### Post by Naegling23 on 2006-10-03
yes, I followed the instructions in leech's forum post
[http://www.ubuntuforums.org/showthread.php?t=113259](http://www.ubuntuforums.org/showthread.php?t=113259)

the game was patched to 1.67, I can try to reapply the patch, maybe something went wrong?

---

### Post by Perfect Storm on 2006-10-03
Try patch it to 1.68 and see if it makes any diffrences.

---

### Post by Naegling23 on 2006-10-03
alright, will do, is there a patch available on the bioware website?  If so, do I just download and run it?  I installed everything from leech's script, I think it only covers up to 1.67.  How do I install 1.68?

---

### Post by Perfect Storm on 2006-10-03
unpack the patch and copy/move the files and folder to where nwn is installed.

---

### Post by Naegling23 on 2006-10-03
copied the files to the /nwn directory.  Overwrote when prompted, did not solve the problem.

---

### Post by Naegling23 on 2006-10-03
so heres another wrench to throw into the equation.  Under xgl, with the game set to 1024x768...the game loads up.  The screen is centered.  So it runs fine in xgl/compiz, but not regular old kde.  The only problem running under xgl is that the extra graphics load causes the system to run choppy.  

Just thought I'd throw this out there, maybe it can help someone trouble shoot this a little better.

---

### Post by podfish on 2007-02-02
It's not just nwn.  Try switching resolutions in something like ppracer or neverball or any other fullscreen opengl app.  It's gotta be X, when not in composite mode.

---

