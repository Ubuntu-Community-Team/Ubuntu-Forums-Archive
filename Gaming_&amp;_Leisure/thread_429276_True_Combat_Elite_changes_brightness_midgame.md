---
title: "True Combat Elite changes brightness midgame?"
date: 2007-05-01
forum: Gaming &amp; Leisure
---

### Post by SlackLagg on 2007-05-01
I'm having some trouble with True Combat Elite (TCE).  I haven't play much ET lately so I'm not sure if there is a problem with that as well.

My problem is after about 10-15 minutes of play, the game suddenly gets darker.  If I run 
/r_gamma it will show that the gamma setting has not changed.

if I manually retype in the r_gamma setting (IE   /r_gamma 1.5) it will reset.

The reason I posted this here and not on the TCE forums is because the game worked fine with 6.10 (Edgy)  **_BUT_** I was using Envy to fetch my Nvidia drivers. When I upgraded to 7.04 (Feisty) I decided to not mess with Envy and just use regular apt-get nvida-glx.  

What I have tried so far
[LIST]
[*]Deleting .etwolf dir
[*]Reinstalling ET
[*]Reinstalling TCE
[*]Reinstalling nvidia-glx
[*]Reinstalling restricted modules
[/LIST]

Any ideas on this ?

---

### Post by dekki on 2007-05-01
Had the same problem, for me it was the screensaver that started so it darkened the screen. I had to turn it off so it never started.

Another problem I still have is that some maps have worse fps then they had in Edgy, but that could be do to the new ATI drivers.

---

### Post by SlackLagg on 2007-05-01
Screensaver eh?

Humm I'll check that out.

EDIT:

So far that seems to have fixed it. I wonder what causes that? 

I wonder how I can keep from having to turn the screensaver on/off all the time. humm 

Well anyhow, thanks for the tip, it seems to have worked this time.

EDIT 2:

Yes after extensive testing *playing*  It would seem the screensaver was/is the problem.

---

### Post by cmat on 2007-05-02
ya it was caused by the screen saver. i quit the game as soon as it happened and was greeted by my screen saver.

---

### Post by MiKom on 2007-05-25
But is it possible to keep the screensaver and get rid of brightness changes?
Question is why in feisty the screensaver daemon doesn't recognize mouse moves and hitting the keyboard when ET is played? AFAIK ET engine doesn't take over mouse/keyboard input on so low level that other applications don't know what's going on.

---

### Post by Megatog615 on 2007-05-25
Hmm... It seems an older bug has come back in Feisty, as I also have this problem. In Tremulous it tends to flash the screen instead of cause the gamma bug. Since gamma is handled with SDL in Tremulous instead of direct OpenGL, it may have a different effect.

---

