---
title: "Compiz Fusion on Kubuntu"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by cookieofdoom on 2007-08-14
Okay, so this could just be me doing something stupid, but I've had this problem for a while now and I can't seem to find a solution. I love the KDE interface, and really want to use it. I can't stand how laggy Compiz Fusion is with it, though. I've tried turning off all of the KDE desktop effects (you know the fancy tooltips and fake opacity stuff) and it is still really slow and choppy. Sometimes it just hangs for several seconds. The main problem seems to have to do with animations.

I switched to gnome for a while and everything seems a lot faster. It also doesn't crash nearly as much. Now, I've tried adjusting the backend to "KDE Configuration Backend" (had to install a lib from the repos to do it). It didn't seem to help at all, which was kind of disappointing cuz I had to change all me settings back after that.

Technical info:
I'm using Treviño’s repositories.
I'm using a 7900GS with the default Ubuntu Drivers.
I'm running  KDE 3.5.6
I can't think of anything else that might help but if you have any questions I'll do my best to answer.

If anyone else has this problem, please post here so I can know that I'm not alone. There was some mention of it in[ this thread](http://ubuntuforums.org/showthread.php?t=514291). It was related to Gutsy, though, and I'm not using Gutsy.

Thanks!

---

### Post by maestrobwh1 on 2007-08-14
Not that this is a huge help... but I have had a dual install of kubuntu Feisty, and when Gutsy 2 came out, I upgraded one of the installs.  I have compiz fusion on both, Feisty with a 3rd party repo, and Gusty has the packages in its own repo.  It runs much more smoothly on Gutsy than Feisty and both installs started off equally.  Go figure.

This post might help[URL="http://ubuntuforums.org/showthread.php?t=511389"]
http://ubuntuforums.org/showthread.php?t=511389[/URL], as creating a bash file called startcompiz and putting it in my /user/bin directory (I copied his script into kate, saved it in home, moved it to /usr/bin and made it executable) seemed to make it a bit less "sticky" but indeed, I have the same issue you have, especially when running firefox/swiftfox, just not very much crashing.  Amazingly, on Gutsy, there is none of this.  Same computer/same hardware.

I did not have luck with creating a file called /home/username/.profile like he did.  Emerald never launched and I had no keyboard.  Weird.

I modified my /home/username/.bashrc and put this at the bottom of that file

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
PATH=~/bin:"${PATH}"
fi
export KDEWM=startcompiz
(I think only the last line is important for this)

For Feisty, using kate, I created a desktop item like this, named "compiz"

[Desktop Entry]
Comment=
Comment[en_US]=
Encoding=UTF-8
Exec=startcompiz
GenericName=
GenericName[en_US]=
Icon=/home/bwh-feisty/.local/share/icons/compiz-logo.png
MimeType=
Name=Compiz
Name[en_US]=Compiz
Path=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=

Then I created one for kwin just like it, but changed Exec=startcompiz to **EXEC=kwin --replace** and obviously changed the name to kwin and gave it another icon.

I tried to put the desktop item for compiz in my /home/username/.kde/Autostart directly but emerald crashed and I had to hit the icon anyway to relaunch everything.

I toggle between them.  Sometimes the slowness gets to me when I am switching apps and such so I drop out of compiz.  

In Gutsy, I put the compiz desktop item in my /home/username/.kde/Autostart directly and it launches every time w/o crashing emerald.  I also kept that as a desktop item along with my kwin item, just to be able to nicely swap.

---

### Post by cookieofdoom on 2007-08-17
So it sounds like the issues will probably be fixed when Gutsy is released. I guess I'll stick with gnome until then. It's not that I don't like gnome, I just like KDE better. It kind of works out, though, because I never could sync my Pocket PC with Kontact.(segfault). When Gutsy comes out I'll probably go back to KDE.

Thanks.

---

