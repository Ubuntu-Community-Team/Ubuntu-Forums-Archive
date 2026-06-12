---
title: "Tilda goes grey after I re-activate it in Gutsy (Gnome and XFCE)"
date: 2007-10-19
forum: Desktop Environments
---

### Post by FFighter on 2007-10-19
I've tested it both on Gnome and XFCE. When I first start Tilda, its terminal screen looks ok, when I hide it and try to show it again its rectangle is filled with a grey colour instead of the terminal window, trying to hide and show it again doesn't matter, it remains grey.

It used to work very well on Feisty. Does anyone know what could be happening?

Thanks in advance,

Marcelo.

---

### Post by Klargodut on 2007-10-20
Experiencing the same problem, currently under gnome. Anyone had any luck with it or has an alternative application to use?

---

### Post by wormie_dk on 2007-10-20
If you turn on animated pulldown and select animation orientation left or right it seems to work...

---

### Post by depi on 2007-10-20
Same here :( ( after installing 7.10)

---

### Post by Tundro Walker on 2007-10-20
Well, there's a [Launchpad bug]("https://bugs.launchpad.net/debian/+source/tilda/+bug/144175") submitted for it.

The work-around stated is...

1) Open Tilda Screen
2) Right-click on it & select **Preferences**
3) Click **Appearance** tab 
4) Select **Animated Pulldown** checkbox
5) set **Delay** = 1 usec (millisecond)
6) Select **Animation Orientation** Left or Right

Works for some folks.  Doesn't work for me.  Tilda used to have problems when the Compiz Desktop was active.  But this occurs even when Compiz is deactivated.

Sounds like (from the bug report) that a new version of Tilda has resolved this issue, but it'll take time for it to make it into the Package Manager system.

Could try Yakuake, I guess.  I tried it out when first checking out quake-style consoles, and I preferred Tilda.  But, since Tilda isn't working...  Man, get so used to hitting the tilde key to bring down my console...damn...it's like I lost a best friend...

---

### Post by gali98 on 2007-10-21
Thanks guys that worked for me. I was about to go crazy.
Kory

---

### Post by Klargodut on 2007-10-22
Works some of the time, but not always :( switching to YaKuake for now, until this bug is fixed.

---

### Post by germania on 2007-10-22
Wow... this bug hurts a lot.  I love tilda 

:(

---

### Post by radovan01 on 2007-10-22
Happy not to be the only one with this bug. Animation delay works for me, but the animation really sucks. Looking forward for tilda update. I have tried yakuake that I am running on debian testing + kde but it wasn't 100% rendered so I am staying with animated tilda right now.

---

### Post by germania on 2007-10-22
I decided I couldn't live without it.  I built a .deb on gutsy for the CVS as of today (October 22), and while it doesn't have the dependencies etc. set up, it does appear to fix the bug without enabling that awful animation.  For anybody interested, it's at 

[http://benclarke.ca/tilda_0.9.5pre-1_i386.deb](http://benclarke.ca/tilda_0.9.5pre-1_i386.deb)

enjoy!

---

### Post by Klargodut on 2007-10-23
Thank you! Actually works :) Yakuake is out!

---

### Post by ktulu1115 on 2007-10-23
My tilda works except for one small bug - when I restore it, does not maintain "on top" status - as in, it scrolls onto the screen but not on top).  Using desktop effects on new Gusty install, worked fine on Feisty w/o compiz.

---

### Post by radovan01 on 2007-10-23
> **germania said:**
> I decided I couldn't live without it.  I built a .deb on gutsy for the CVS as of today (October 22), and while it doesn't have the dependencies etc. set up, it does appear to fix the bug without enabling that awful animation.  For anybody interested, it's at 

[http://benclarke.ca/tilda_0.9.5pre-1_i386.deb](http://benclarke.ca/tilda_0.9.5pre-1_i386.deb)

enjoy!

thanks germania!

---

### Post by javier.der on 2007-10-24
> **germania said:**
> I decided I couldn't live without it.  I built a .deb on gutsy for the CVS as of today (October 22), and while it doesn't have the dependencies etc. set up, it does appear to fix the bug without enabling that awful animation.  For anybody interested, it's at 

[http://benclarke.ca/tilda_0.9.5pre-1_i386.deb](http://benclarke.ca/tilda_0.9.5pre-1_i386.deb)

enjoy!



oh, i love you sooo much!!! thank you, i'm way too lazy and didn't want to fix it myself...
:)

---

### Post by mcpish on 2007-10-25
Thank you so much for creating this package.  I love Tilda (but I turn off the animation) and noticed this bug right away after installing Gutsy.  This new deb fixes that problem but it creates a completely new different problem.  Try typing "exit" from the tilda command line, it doesn't quit.  Also everytime I start the programme it always brings up the preferences window everytime.

---

### Post by Rog on 2007-10-25
I have a similar exit problem, press Ctrl-D (exit), and it freezes up.

- Roger

---

### Post by smack on 2007-10-26
> **germania said:**
> I decided I couldn't live without it.  I built a .deb on gutsy for the CVS as of today (October 22), and while it doesn't have the dependencies etc. set up, it does appear to fix the bug without enabling that awful animation.  For anybody interested, it's at 

[http://benclarke.ca/tilda_0.9.5pre-1_i386.deb](http://benclarke.ca/tilda_0.9.5pre-1_i386.deb)

enjoy!

Many thanks bro! \\:D/

---

### Post by geist27 on 2007-10-28
> **germania said:**
> I decided I couldn't live without it.  I built a .deb on gutsy for the CVS as of today (October 22), and while it doesn't have the dependencies etc. set up, it does appear to fix the bug without enabling that awful animation.  For anybody interested, it's at 

[http://benclarke.ca/tilda_0.9.5pre-1_i386.deb](http://benclarke.ca/tilda_0.9.5pre-1_i386.deb)

enjoy!

Total lifesaver!!

You never know how much you love something till its gone, I shall never take you for granted again Tilda!

---

### Post by gsiliceo on 2007-10-29
> **germania said:**
> I decided I couldn't live without it.  I built a .deb on gutsy for the CVS as of today (October 22), and while it doesn't have the dependencies etc. set up, it does appear to fix the bug without enabling that awful animation.  For anybody interested, it's at 

[http://benclarke.ca/tilda_0.9.5pre-1_i386.deb](http://benclarke.ca/tilda_0.9.5pre-1_i386.deb)

enjoy!

Awesome man! thx

I just had to install libconfuse0 for it to work :)

---

### Post by zero456 on 2007-10-31
Thanks a lot germania, you're a life saver! :guitar:

I've added a comment to the bug about the package which is [here]("https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/144175/comments/44").

---

### Post by mcpish on 2007-11-03
> **Rog said:**
> I have a similar exit problem, press Ctrl-D (exit), and it freezes up.

- Roger

I figured it out.  Bring up the preferences, (right click on the Tilda window), and go to the "Title and Command" tab.  Go to the "When Command Exits" dropdown and select "Exit the terminal".  This will fix it.

---

### Post by kungfooguru on 2007-11-14
These problems are fixed in the cvs version of Tilda. You can find instructions on downloading this here: [http://sourceforge.net/cvs/?group_id=126081](http://sourceforge.net/cvs/?group_id=126081). Sorry for the delays in getting a new release out, I don't have much time to spend on Tilda. The cvs version is stable and very close to release. Just one or two more features to add. Sorry for the slow releases and breakage. Let me know if anyone has more troubles.

Tristan

---

### Post by zero456 on 2007-11-16
Thanks for the update kungfooguru.  I'm not sure if this is fixed in the latest version (Since October 22) but occasionally, tilda will start rather lopsided, with about an inch of screen space above, and about 1/8 of an inch to the left of it (It is set to 100% width 25% height).

---

### Post by dustigroove on 2007-12-03
> **kungfooguru said:**
> These problems are fixed in the cvs version of Tilda. You can find instructions on downloading this here: [http://sourceforge.net/cvs/?group_id=126081](http://sourceforge.net/cvs/?group_id=126081). Sorry for the delays in getting a new release out, I don't have much time to spend on Tilda. The cvs version is stable and very close to release. Just one or two more features to add. Sorry for the slow releases and breakage. Let me know if anyone has more troubles.

Tristan
[COLOR=Black]
Hi Tristan, thanks for the update and information on downloading from cvs. I have checked out the src and attempted to build using the included autogen script however I am getting the following:
```
./autogen.sh: 33: autopoint: not found
```I'm assuming that I am missing some dependency, but based upon the README it appears I have everything. Any advice?[/COLOR]

---

