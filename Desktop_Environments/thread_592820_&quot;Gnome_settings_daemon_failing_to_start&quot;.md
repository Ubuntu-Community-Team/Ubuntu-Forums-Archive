---
title: "&quot;Gnome settings daemon failing to start&quot;"
date: 2007-10-26
forum: Desktop Environments
---

### Post by raulih on 2007-10-26
I have this error quite often after login: "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Everything is usually ok after logout and re-login, but how to solve this permanently?

---

### Post by Caffeine_Junky on 2007-10-27
> **raulih said:**
> I have this error quite often after login: "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Everything is usually ok after logout and re-login, but how to solve this permanently?

Yes, I experience the exact same thing from time to time,  could this be a Bug?   

I would like too narrow this down so if needed a "bug report" can be submitted...

If anyone can help out in tracking down this problem, it would be much appreciated 

thanks

---

### Post by raulih on 2007-10-31
No one has anything to say? :(

---

### Post by Alligator on 2007-11-01
I'm having similar problems with the same error.  i.e. I changed the background, got the error and then it worked.  This is repeatable.  Also the "trash" does not work.  The trash window contains nothing even though I've selected it to be.:guitar:

---

### Post by raulih on 2007-11-02
I have no problem with Trash - only with background and font settings not loading when getting the error. Do you re-login to get background work? Is it same with trash or doesnt it work even after re-login?

---

### Post by bharani on 2007-11-02
Please look at this..after two restarts everything is fine...whole process repeats next day i log in to my comp..

---

### Post by raulih on 2007-11-02
This is not a full solution, but I found out that desktop settings can be run manually without a need to re-login. So after unsuccesful login press Alt+F2 and run command "gnome-settings-daemon" without quotes. First time testing it immediately loaded correct settings.

---

### Post by raulih on 2007-11-14
Running "gnome-settings-daemon" manually still seems always to load correct desktop settings. Still at least two things are not corrected when having the error message:* trash shows empty* while its not, and other *drives are not available in "File System"*. Does somebody know at least what service loads them? It would be handy to load them manually too if theres no other solution to the problem.

---

### Post by peter_k on 2007-12-19
I'm not sure if I'm getting the exact same error, but just wanted to check as it seems similar.  I run at 1280x1024; occasionally I get the error you guys have mentioned; the fonts aren't as sharp, and the resolution has switched to 1024x768.  Sometimes I get a black background (i.e. no wallpaper, but the menu bars are OK -- selcting Appearance fixes it immediately); something I thought I fixed, but which still occurs.  Finally, sometimes I just get a black screen (as if my monitor were off - but I confirmed it was on :) ); I can tell the system is still loading, because I can hear the startup sound.

I'm not sure if all of these are related, but it could be possible; sometimes I get a few boots in a row where all is well, and sometimes I get a bunch of boots where it goes wrong.  When I see the brown "splash" screen, and the mouse pointer changes to the right resolution (I believe my grub screen is  a resolution lower than 1280 -- it may even be 800x600). I know I'm in for a good login.  

Anyone else seeing this, and if so, have they fixed it (or is this a bug we have to wait for an update for)?

---

### Post by exploder on 2007-12-19
You can eliminate this problem by editing your /etc/hosts/ file. Put your computer name in the top line (leaving a space) and reboot. I saw this in a bug report, my system was constantly getting this error. The problem is completely resolved on my system now!

---

