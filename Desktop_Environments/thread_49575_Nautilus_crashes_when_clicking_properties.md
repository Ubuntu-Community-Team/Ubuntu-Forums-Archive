---
title: "Nautilus crashes when clicking properties"
date: 2005-07-16
forum: Desktop Environments
---

### Post by woedend on 2005-07-16
For some odd reason, nautilus crashes when right clicking a wav or wma file, then clicking properties.  It will run them with any app, do any thing else to them, just won't view the properties.  Just freezes until I close it.  All other files so far seem good(movie files and mp3 don't do this).  I'm thinking...then, that it is not nautilus but one of the libraries i've installed onto ubuntu, because it didn't happen initially.  Any way you guys can point me in the right direction here....it's a pain in the arse.

---

### Post by matthew on 2005-07-16
You know, mine started doing this last night with mp3's. I have no idea why. Today it works fine. Sorry I don't have a solution, just thought I would echo that you are not alone in experiencing this weirdness.

---

### Post by woedend on 2005-07-16
did you install any new codecs?  I'm thinking it's some kind of codec error maybe?  What do I know.  I reinstalled nautilus to no avail.  This did occur after I apt'd a couple million things(java,gstream,xine,xmms,w32) etc etc.  I removed w32...still no help.  It is very frustrating to me...I'm going to keep working on this.

---

### Post by matthew on 2005-07-16
I just looked at my logs to confirm as I tend to change stuff regularly on my machine... Nope, I didn't install anything new, but I did rip some of my cd's using goobox yesterday and I edited the tags of the mp3s with EasyTag. Only the new files were affected. Anyway, for me things cleared up after a reboot.

---

### Post by woedend on 2005-07-16
thanks for your help matthew.  I have actually narrowed it down...a LOT.  I renamed the wav file to .wv instead of .wav, then it let me view the properties(so, it's not the file but was the extension).  I then took association away from totem and put it to xmms.  After renaming it back to .wav, I could view properties normally.  So I would assume totem has some part to blame in this.  But, that's not all.  Totem is associated with all of my movie files, which displays properties normally.  So it has to be something in totem's audio/not video association causing this...because my WMA files were also associated with it.  Tricky indeed.  Any ideas now?  It happens on both totem-xine and totem-gstreamer so I'm not sure it's affected by those libs.  

Update yet again.  Actually this theory turns out to be false.  I renamed the wma file back to wma from wm, and now I can read its properties normally even though I did not change association.  Gotta love weird problems like this!  I'm starting to wonder if realplayer install had a little hand in this.

---

### Post by matthew on 2005-07-16
Hmm... The plot thickens. I wonder what would happen if you changed the filetypes' association from Totem (I have found Totem-xine to be more stable, btw) to another player like Beep or amaroK.

---

### Post by JGJones on 2005-07-18
I have this problem with any media files (avi, asf, mp3 et al) but a reboot fix it too.

Just wondering...do any of you have RealPlayer10 installed (I installed mine recently for the Live 8 streaming video from BBC and found RealPlayer to do a better job than Totem (Totem does work, but somehow it's just not...."smooth" while RealPlayer just get on with it. Strangly enough, RealPlayer will not work unless I have sound server off(!)

Anyway, I get this problem whatever file association you have it set to.

---

### Post by JGJones on 2005-07-18
Just checked it myself.

Booted system - look at properties - slight delay, but otherwise works fine.

Load RealPlayer10, play a music file, close it.

Look at system monitor or the command ps - A and verify that RealPlayer10 isn't loaded anywhere.

Look at propterties of music file - freeze up.

So is RealPlayer10 the problem somehow?

I have sound server switched off always (all media player don't use esd)

Applications that was running: Opera, Thunderbird, Gnome-terminal, GAIM (Yahoo conversation) - they was not touched at all during the test.

So I'll reboot and try it again but without opening any applications and see what happens if I load other media player etc.


EDITED for result below:

I rebooted the system and looked at properties - worked.
I opened the music file with beep media player and closed it and verified that it had completely exited

Look at properties - freeze up.

This is the same for all other media players but avi's are fine - it affect sound files (ie mp3, wav and some media files such as asf but rm files are ok).

All mediaa plyers are using the OSS sound driver - will retest using e-sound (esd)

---

### Post by Sephiriz on 2005-07-18
Hmmm... yesterday I installed Real Player and I believe that after that I tried looking up some information on some new MP3's I acquired, and I also experienced this freezing, something that never  happened to me before.  Reading all the previous posts could lead one to believe that Real Player is indeed the problem.

When I get back to my computer, I'll uninstall it and see if that will change anything to the better.

---

### Post by woedend on 2005-07-28
not to beat a dead horse...but realplayer does not seem to be the problem.  It seems like a hit miss install problem.  I've installed ubuntu probably a total of 5 times(don't ask), and 3 of those times it was perfect, the other 2 times I got this problem.  The last time realplayer was not installed.

---

### Post by henrrrik on 2005-08-16
I had this problem until today and it turns out totem-xine was causing this problem for me. Totem crashed on start and opening Properties on any file associated with Totem crashed Nautilus. Replacing totem-xine with totem-gstreamer solved the problem.

---

