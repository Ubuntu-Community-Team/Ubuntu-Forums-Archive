---
title: "Disappearing Browser Titlebars"
date: 2007-10-31
forum: Desktop Environments
---

### Post by Bionic Apple on 2007-10-31
I have a very strange problem.  The title bar on top of Firefox and Opera (the part controlled by Linux where it says "Ubuntu Forums - Mozilla Firefox") blanks out and becomes totally white with no text.  Plus, the three window control buttons in the top right also get sort of messed up.  This seems to happen only when I load a new page, but other than that it is pretty random.  I reinstalled Opera, Firefox and all the Compiz and Gnome theme packages I could find.  However, this doesn't seem to happen when I don't have advanced desktop effects on.  I don't know what is wrong with Compiz and I also don't know if it happens in non-browser programs.  Any help?  I think it might be the Compiz theme decorator or wobbly effect.  I don't know though.  That is why I am asking you guys!

---

### Post by Bionic Apple on 2007-11-01
Nobody knows an answer?!  Well if somebody does, please respond.  I don't want to be bumping this for eternity.

---

### Post by Dingbats on 2007-11-13
I have exactly the same problem.  It only happens with Firefox when the window is maximized.  Hovering with the mouse pointer over the top left Firefox icon or the top right buttons returns it back to normal.  It seems to happen often, but not always, when I load a new page or a new tab.  All desktop effects (well, at least those I have applied) work normally.

EDIT: Hovering the mouse pointer over the Firefox icon or the buttons in the title bar also can also make it go blank, like half of the times.  That also applies to other maximized windows than Firefox, so I guess the problem isn't specific with Firefox, which makes sense.  Ubuntu 7.10.

---

### Post by Dingbats on 2007-11-15
Bump... there must be someone else who has this problem..?

---

### Post by garren on 2007-11-15
This problem only happens to you on your browsers, not other programs?  Very odd.  

It seems to me that a problem appearing in both Opera and FF is not likely caused by either of those programs, given how very different the two are on a programing language level.  

Accordingly, it seems to me that it would have to be a compiz-fusion problem, since that is drawing your window decorations (assuming your using Gutsy).  Try switching to metacity for window decorations and see if the problem persists, or try turning off window decorations in the compiz settings (actually, do both, but only one at a time so you can find where the problem is).  My guess is that the problem will go away, in which case there is a Compiz-fusion conflict someplace for you.  If the problem persists, then I'm stumped.  

As for a solution if this is a compiz problem--it sounds like a bug to me.  Maybe see what programs you have installed that most others don't, perhaps the problem lies there...  Who knows.

---

### Post by ingvildr on 2007-11-15
Yea i have been getting it too, mine seems to be pretty random though and will sometimes return to normal by itself. To solve it for me i have to unmaximize and maximize the window. Out of interest what themes are you guys using, because i had this same issue on a fedora 8 box and it was solved by changing the window decorators back from clearlooks to the fedora 8 default theme, so it may be theme (gtk-window-decorator) related.

---

### Post by Dingbats on 2007-11-15
Actually it applies to all maximized windows for me, as I pointed out in my edit in my first post.  I don't know which takes lesser effort though, installing Metacity and fiddling around with settings or growing used to it until the bug is fixed in Compiz...:neutral:

EDIT:  Before I come off as too much of a noob, I just realised I of course already have Metacity installed.  Nevermind.

---

### Post by dmgthe2nd on 2007-11-18
I have the same problem. As soon as I enable either the normal or advanced desktop effects, I lose the titlebar.  I just decided to use basic (no effects).  I have no idea which window decorator program i'm using.  I've been try to get clearlooks for a peticular theme I want.

---

### Post by tombeharrell on 2007-11-19
This happens for me too, Ubuntu 7.10 with Compiz Fusion, Nvidia graphics. 

When I have any window maximised, if I roll over the buttons on the title bar, every 4th or 5th time the titlebar background colour disappears until I roll over again. This randomly happens during browsing, I guess every nth time the page title changes in Firefox.

Interestingly this effect occurs to different extents depending on the Window Border selected in Appearance.

This doesn't happen with Aging Gorilla, Atlanta, Bright, Crux, Esco, Glider, Metabox, Mist or Simple.

It happens with Clearlooks, ClearlooksClassic, Glossy and Human.

Is this a case of GTK 1 vs 2? Just a stab in the dark.

---

### Post by Maverick1712 on 2007-11-26
I was getting this same issue. 

Changing window borders to Metabox seems to have fixed the issue.

---

### Post by lee555J5 on 2007-12-31
New install of Gutsy with nVidia card

I have the same issue: complete loss of title bar and borders on all windows. My terminal is just a white box. The only way to kill an app in the gui is to File, Exit or Ctrl-W. No title bar = no buttons. Hovering doesn't help. I can hold Alt and move a window, but I can't resize, maximize, or minimize. I can go to System, Preferences, Appearance, Visual Effects and choose 'None' and get my title bar, buttons, and borders back. They are gone if I choose 'Normal' or 'Extra'.

I saw a suggestion to run either 'compiz --replace' or 'metacity --replace'. How do I know which I am currently running. Synaptec says both are already installed.

Lee

---

### Post by lee555J5 on 2007-12-31
After further research, I found this thread: [http://ubuntuforums.org/showthread.php?t=652286]("http://ubuntuforums.org/showthread.php?t=652286")

Once I added

Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"

to my /etc/X11/xorg.conf under my nVidia device section, everything appears to work correctly so far.

My terminal window was white, so I could not start gedit from there. Go back to the Visual Effects tab from my previous post and change to 'None'. Now you can use the terminal, use gedit to edit your xorg.conf, and restart your session with Ctrl-Alt-Backspace.

Everything seems to be working. Thanks to overdrank.

Lee

---

### Post by prasannaraja on 2008-01-04
for me it just worked when i did this

rm -rf .g*  :guitar:

---

### Post by lajevardi on 2008-03-02
Hi Lee,
I have these options True valued in xorg.conf under nvidia, but there's still the problem..

---

### Post by thebrandon on 2008-03-07
I have the same problem and this seems to have fixed the problem :

Under System > Preferences > Advanced Desktop Effects Settings which opens the CompizConfig Settings Manager.  Scroll down to Workarounds and click on in.  In that menu uncheck Firefox Menu Fix.  Restart firefox.

Hope this helps!

---

### Post by enchantedsky on 2008-04-19
> **thebrandon said:**
> I have the same problem and this seems to have fixed the problem :

Under System > Preferences > Advanced Desktop Effects Settings which opens the CompizConfig Settings Manager.  Scroll down to Workarounds and click on in.  In that menu uncheck Firefox Menu Fix.  Restart firefox.

Hope this helps!

Thanks, this helped. Unfortunately, it fixed the menu problem in Firefox, but the same Window bar disappearing problem still occurs in Open Office. 

I get the impression this is due to the Nvidia driver being lousy.

---

### Post by thebrandon on 2008-05-01
I guess so, I still have titlebars disappear on me from time to time, usually a reboot or switching desktop effects off then back on again helps.

---

