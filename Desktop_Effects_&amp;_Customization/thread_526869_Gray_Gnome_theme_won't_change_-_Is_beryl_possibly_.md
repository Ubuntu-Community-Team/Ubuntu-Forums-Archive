---
title: "Gray Gnome theme won't change - Is beryl possibly affecting it?"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by sergiothatguy on 2007-08-16
Hey everyone, before you read any further I'd like to point out that I'm a linux newbie whose knowledge is basically limited to these forums and ubuntu wiki guides I've found via google. That being said, I already 'broke', if you will, my gnome theme and was wondering if anyone knows how I should go about fixing it (note: I did run a search beforehand and was not able to find a similar situation).

So anyway,  I am using Ubuntu 7.04 with Beryl and I just recently edited my **startxgl.sh** file to fix the shutdown/restart issues listed here

[http://ubuntuforums.org/showthread.php?t=458505](http://ubuntuforums.org/showthread.php?t=458505)

I also have KDE installed, but I only got that to get the programs that come with the package. Anyway, I log out and then log back in with Run Xclient script (just cause I was curious to see the different login settings). I wasn't really liking the interface so I log back out, and log back in with my default **Gnome with XGL** setting and I get a very dull gray theme (reminiscent of the Windows "classic" start menu.. oh and the fonts were huge too, I don't know if that helps any but I figure I should mention it) that refuses to change from **System -> Preferences -> Theme**. To add insult to injury, I keep getting logged out as I attempt to type this message (thank god for firefox session manager). So I'm not really sure what to do, I mean I can login just fine with other **session** settings like KDE, and regular gnome without XGL, but, correct me if I'm wrong, I am pretty sure that I need to run Gnome w/ XGL for Beryl to run correctly.

I would've taken a screenshot if the session would let me stay logged in for more than 30 seconds, but of course I can't even do that. I was able to save a bug report that was generated when I got logged out the first time around though. So I hope that helps a little, if at all.

---

### Post by BucKao on 2007-08-16
I am having the same problem.  Everything looks normal when I'm logged-in under the regular Gnome session, but windows look flat and gray when logged in under the Gnome-XGL session.  When running the XGL session, I cannot change the theme with the Gnome Theme manager.  The window borders DO change when using Emerald, though.  

I am using the proprietary ATI driver from the Ubuntu Feisty repositories.  I wonder if a newer driver version would fix this?

---

### Post by sergiothatguy on 2007-08-16
I managed to get a screenshot of what my desktop looks like now and note that my screen resolution is 1920x1200 on a 15.4" widescreen laptop, so the application fonts are much larger than they should be.

---

### Post by realvz on 2007-08-16
i have the same issue..i have compiz fusion and i use AIGLX...thats the default one for NVIDIA card...

everything runs fine...i get gnome theme nice and good....but the moment i do sudo *something* that application will now open with a theme similar to window classic...

---

### Post by BucKao on 2007-08-16
I did some searches on the Compiz Fusion forums, and found a couple that might be relevant.  I'm pretty new to Ubuntu, so I don't know if any of this will help or not, but I will try some of this out tonight or tomorrow and see if it works.

[http://forum.compiz-fusion.org/showthread.php?t=2956&highlight=theme](http://forum.compiz-fusion.org/showthread.php?t=2956&highlight=theme)

[http://forum.compiz-fusion.org/showthread.php?t=376](http://forum.compiz-fusion.org/showthread.php?t=376)

---

### Post by BucKao on 2007-08-16
OK, after more searching, it looks like the problem is that in an XGL session, gnome-settings-daemon doesn't start automatically, and needs to be added to the start-up programs in System->Preferences->Sessions.  I found someone on the Launchpad talking about it.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/75280](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/75280)

---

### Post by sergiothatguy on 2007-08-16
Nice finds BucKao. I'll go ahead and check this out as soon as I reinstall XGL lol. I was going to see if that would do the trick, but I have a feeling it might not.

---

### Post by BucKao on 2007-08-16
OK, it worked.

I added a startup command in System-->Preferences-->Sessions named simply "Gnome Daemon", and for the command, put "gnome-settings-daemon", then I did ctrl-alt-backspace to restart the GUI, and everything worked!  No more Win95 appearance!  I can now change icons and colors with System-->Preferences-->Themes.

Ubuntu is beautiful now, with new icons, colors, Compiz-Fusion effects, and Avant Window Navigator all running flawlessly (knock on wood).    

I hope this works for everyone else having this problem, too.

---

