---
title: "Kde 4.0 Rc 1"
date: 2007-11-21
forum: Desktop Environments
---

### Post by rich.bradshaw on 2007-11-21
Has anyone else had a play with this yet?

I've stuck some screenshots up on my blog [here]("http://richbradshaw.wordpress.com/2007/11/21/kde-40-rc-1-running-on-kubuntu-710/") for the interested - has anyone got Konqueror and Dolphin to install correctly? The packages suggested on the Kubuntu page seem to be borked.

---

### Post by flying_icarus on 2007-11-21
I have had a play with packages from the kubuntu page. :) 

Konqueror was installed by default, and I think I had to apt-get install dolphin-kde4, but I'm not sure.

I have a different arrangement of thingys on the screen than what the screenshots in your blog show- my kmenu is in the bar on the bottom of the screen, but the system tray is in the middle, desktop effects don't work and so... it's still early it seems. :)

There are more kde4 packages available it seems, if you're up to playing with them, try aptitude search "\-kde4" for a list. That's packages ending with -kde4, those beginning with kde4 seem to be from a different release set.

---

### Post by hikaricore on 2007-11-21
Am I the only one who really hates that Dolphin does not have "mouse over" previews?

I may try out KDE4, but I'm sure as hell not using that worthless porpoise.

---

### Post by PeterJS on 2007-11-21
I installed it this morning and was really disappointed.I couldn't figure out how to customize Plasma at all, I could add more widgets, but I couldn't figure out how to configure the kicker replacement bar. The new menu is cool in theory, but I found it really cumbersome and unwieldy to use. My biggest complaint is that the move to konqueror as a web browser, that happens to have a dolphin plugin for browsing local files, has broken the features that I like and use most. The new tabbing model of having the tree view as part of the tab, meaning I have to re-open it for each tab, is a pain. Also I can't figure out where they hid all the file views, there are a couple in the tool bar, but there were more in 3.5, I can't believe that they would have removed them, so the must just be hidden somewhere

---

### Post by JetskiDude911 on 2007-11-21
I played with it a while ago (before RC 1 was released), and it seemed pretty cool. I'm gonna wait for the final release though.

---

### Post by LuisAugusto on 2007-11-22
> **hikaricore said:**
> Am I the only one who really hates that Dolphin does not have "mouse over" previews?

I may try out KDE4, but I'm sure as hell not using that worthless porpoise.

Pardon me? It does use mouse hover previews.

If you hover any file on dolphin, it will show a preview in the information panel (without clicking it).

---

### Post by hikaricore on 2007-11-22
> **LuisAugusto said:**
> Pardon me? It does use mouse hover previews.

If you hover any file on dolphin, it will show a preview in the information panel (without clicking it).

Eh, wasn't aware of that.  I've only tested Dolphin in kde3.

Sad that there has to be an information panel though, it's much more minimalistic to have the info and preview pop at the mouse location.  *shrug*

---

### Post by punky on 2007-11-22
I've been trying to install this, but getting some grief. I'm following the instructions [here.](http://kubuntu.org/announcements/kde4-rc1.php)

A little disclaimer though, i'm trying this on Ubuntu Gutsy, not Kubuntu. Does that matter? I'm downloading Kubuntu anyway in case.

When I try:

Xephyr :1 & export DISPLAY=:1; xterm

I get:

> xterm Xt error: Can't open display: :1
[3]   Exit 1                  Xephyr :1

so when I try:

export  DISPLAY=:1 
Xephyr :1

I get:

> Xephyr cannot open host display. Is DISPLAY set?

If I skip that and try and run it as a full session: I get:

> dpkg: error processing kdm-kde4 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kdm-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas guys? X isn't my forte. 

Many thanx in advance.

---

### Post by rich.bradshaw on 2007-11-22
I've added the steps I went through to install at the top of my blog post in my first post in this thread.

I'm doing it from Kubuntu - think that's probably important - not sure though!

---

### Post by lexxonnet on 2007-11-22
I installed it on Kubuntu yesterday, and it seems plasma is pretty broken in this release. I cant seem to move any of the widgets anywhere, and this seemed to be the case on the OpenSuse LiveCD of RC1 as well.

Interesting thing though, is that KDE identifies itself as beta4 rather than RC1.

---

### Post by rich.bradshaw on 2007-11-22
Yeah, it reports as KDE 3.96.00 (KDE 4.0 Beta4) doesn't it... maybe it's the same thing internally...

---

### Post by bmorency on 2007-11-22
3.96 is the RC. if you go to the [ kde ]("http://kde.org/info/3.96.php") website it says that.

but it says this under bugs:

"The version number within kdelibs has been incorrect for the released tarballs. The application version will probably default to "KDE 4.0 Beta4", which makes identifying your bugreports against this new version difficult. Please apply the patch to fix the version number."

---

### Post by mivo on 2007-11-22
> **hikaricore said:**
> Am I the only one who really hates that Dolphin does not have "mouse over" previews?

Yes. ;) I always turn that off in Konqueror. (But choice is a Good Thing.)

---

### Post by rich.bradshaw on 2007-11-22
Does anyone know of any newer packages - some screens on other sites show the panel at the bottom working properly with the plasmoids properly docked on it...

---

### Post by punky on 2007-11-22
OK, i've tried again on Kubuntu. Still got the same error, but i ignored it, and it worked :)

Looks great, although the UI runs like a dog on my friend's box (P4 1.8, 256meg RAM, riva tnt 32mb) 

He's going to try and install more RAM and a better gfx card, but its a start :)

---

### Post by rich.bradshaw on 2007-11-23
Yeah - I've not seen any of the compositing stuff in Kwin yet - not sure if it's in this version, but you probably need a half decent graphics card for that as well.

---

### Post by lexxonnet on 2007-11-23
hmm... I've got an ati 9600 using the DRI drivers and it seems to work fine with compiz. I cant for the life of me get kwin-composite working though.

---

### Post by LuisAugusto on 2007-11-23
> **hikaricore said:**
> Eh, wasn't aware of that.  I've only tested Dolphin in kde3.

Sad that there has to be an information panel though, it's much more minimalistic to have the info and preview pop at the mouse location.  *shrug*

Weird, I remember that Dolphin in KDE 3 does have this feature :/
I haven't test D3lphin, maybe they changed that there.

> **lexxonnet said:**
> hmm... I've got an ati 9600 using the DRI drivers and it seems to work fine with compiz. I cant for the life of me get kwin-composite working though.

I made it work, but it works slower than Compiz. I couldn't ever make it work whit XGL, but whit the latest drivers, I used aiglx, if you want to run it, I can tell you how :)

See you.

---

### Post by lexxonnet on 2007-12-06
> **LuisAugusto said:**
> 
I made it work, but it works slower than Compiz. I couldn't ever make it work whit XGL, but whit the latest drivers, I used aiglx, if you want to run it, I can tell you how :)

See you.
Hehe... sure, I wouldn't mind dabbling with it again :)

---

### Post by LuisAugusto on 2007-12-06
> **lexxonnet said:**
> Hehe... sure, I wouldn't mind dabbling with it again :)

Once you installed the last 7.11 (or 8.43)

Add the following lines to your xorg.conf:

Under Section &#8220;ServerFlags&#8221; add:

```
Option &#8220;IgnoreABI&#8221; &#8220;on&#8221;
Option &#8220;AIGLX&#8221; &#8220;true&#8221;
```

Under the section extensions:

```
Option &#8220;DAMAGE&#8221; &#8220;true&#8221;
Option &#8220;RENDER&#8221; &#8220;true&#8221;
Option &#8220;Composite&#8221; &#8220;true&#8221;
```

And, finally, under section device, make sure that none of those appears twice, you may have one of those already, I can't remember clearly XD:

```
Identifier &#8220;aticonfig-Device[0]&#8221;
Driver &#8220;fglrx&#8221;
Option &#8220;Capabilities&#8221; &#8220;0×00000000&#8243;
Option &#8220;VideoOverlay&#8221; &#8220;on&#8221;
Option &#8220;OpenGLOverlay&#8221; &#8220;off&#8221;
Option &#8220;XAANoOffscreenPixmaps&#8221; &#8220;true&#8221;
Option &#8220;AllowGLXWithComposite&#8221; &#8220;true&#8221;
Option &#8220;RenderAccel&#8221; &#8220;true&#8221;
```

As a side note, it doesn't work usably fast with OpenGL, I use Xrender. 
To change that, you have to right click the window border, select configure window behavior, desktop effects, advance options, Xrender.

I hope it helps you :)

---

