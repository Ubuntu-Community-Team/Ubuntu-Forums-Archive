---
title: "[SOLVED] screensaver problem"
date: 2008-03-25
forum: Desktop Environments
---

### Post by darth.k on 2008-03-25
This is a small problem but is really annoying me.  My screen goes black after about 10 - 15 minutes of no activity on the computer, normally I wouldn't mind but it does it when i'm watching a movie or a dvd, it so annoying I have to move the mouse to bring it back on.

I have set all the power options to "never" but it's still doing it.  Any help?

---

### Post by finer recliner on 2008-03-25
do you have compiz effects enabled with an ATI graphics card? I had this problem too. some people offered solutions that worked for them, but none worked for me.

---

### Post by kellemes on 2008-03-25
> **darth.k said:**
> This is a small problem but is really annoying me.  My screen goes black after about 10 - 15 minutes of no activity on the computer, normally I wouldn't mind but it does it when i'm watching a movie or a dvd, it so annoying I have to move the mouse to bring it back on.

I have set all the power options to "never" but it's still doing it.  Any help?

What movieplayer are you using to view the movie or dvd?
It's up to the movieplayer to stop the screensaver from kicking in.

---

### Post by darth.k on 2008-03-25
yes i'm using compiz with an ati card.  I use vlc to watch viseos but the same was happening with movie player.

---

### Post by kellemes on 2008-03-25
Just to test..

Startup VLC.
Settings -> Preferences -> Advanced options (bottom right of dialog) -> Video -> Disable Screensaver (have it selected)
If it wasn't selected.. watch a video for some time and see if the screensaver kicks in, it shouldn't.

If it's already selected there is something else going on..
Maybe you can look in /var/log/messages for hints,  look at the file just after your screen goes blank.

---

### Post by darth.k on 2008-03-25
thanks for the reply, it was selected but the screen keeps going blank.  I looked in that file but don't really understand it.

---

### Post by finer recliner on 2008-03-25
here's a thread i had bookmarked from the time i spent researching the problem:

[http://ubuntuforums.org/showthread.php?t=584406](http://ubuntuforums.org/showthread.php?t=584406)

try some of their workarounds to see if you get anywhere

---

### Post by darth.k on 2008-03-25
Thanks for the input guys, I've tried one of the work arounds mentioned I'll report back with my findings.

---

### Post by darth.k on 2008-03-26
Thanks this worked a treat, seems to have disabled the screensaver but I'm not to fussed about that.

---

