---
title: "Compiz Fusion and Video Playback"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by kodoku on 2007-07-19
Hello all,

Before someone shoots me, I've read all the threads I could about video playback with compiz-fusion, but I have yet to find a solution.

In compiz fusion, I've bent over backwards trying to find all the transparency/opacity settings I could.  But no matter how I tweak it, any kind of video playback in mplayer/smplayer will result in a transparent video (NOT fullscreen).  VERY transparent, as in video can barely be seen without a black background.  Alt-scroll will make the main window more or less transparent, but the video window itself never changes.

Could someone please help me? I've attacked ccsm > General Settings > Opacity to death, and I can't fix it.. Could it have something to do with my video playback using x11?

EDIT: Correction, this only occurs in SMplayer

---

### Post by Happy_Man on 2007-07-19
Then, perhaps it is an SMplayer setting. Have you rooted around in there?

---

### Post by dodgePT on 2007-07-19
I been having some issues with SMPlayer while running compiz-fusion.
The player acts funny while in fullscreen, the window itself magnifies, but the video stays the same size, on the top left corner. Other minor and random things happened, while compiz-fusion is updated everyday.
Maybe this is related?

---

### Post by kodoku on 2007-07-19
> **Happy_Man said:**
> Then, perhaps it is an SMplayer setting. Have you rooted around in there?

Oh yes, I have poked around A LOT in SMPlayer..  I guess I could live with it for now, but I do hope there is a fix soon.

Here are some screenshots, the first one is when it's not playing (notice, the video box is COMPLETELY transparent), the second one is when a video is playing.

[[IMG]http://img201.imageshack.us/img201/6464/86089534oo6.th.png[/IMG]](http://img201.imageshack.us/my.php?image=86089534oo6.png)   [[IMG]http://img508.imageshack.us/img508/1332/53381053ss5.th.png[/IMG]](http://img508.imageshack.us/my.php?image=53381053ss5.png)

---

### Post by rvm4000 on 2007-07-20
I've never used compiz-fusion, but by default SMPlayer doesn't update the video background to avoid some problems. Maybe that's causing your transparency problem. 

Try disabling the option "Don't repaint the background of the video window" in Preferences->Advanced.

---

### Post by kodoku on 2007-07-20
> **rvm4000 said:**
> 

Try disabling the option "Don't repaint the background of the video window" in Preferences->Advanced.

Wow, I swear I've enabled and disabled that option before.. But it worked this time.  I guess the default setup (with the option disabled) had the problem, and then enabling it didn't fix it.  But when I disabled it again, and I guess that fixed it.. Thanks for all the help guys.

---

