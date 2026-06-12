---
title: "Windows Vista has a better theme than I do!"
date: 2009-10-29
forum: Desktop Environments
---

### Post by armoftheland on 2009-10-29
Hi everyone, I've just installed 9.10 and finally have been able to play with my compiz and emerald themes (i've got one of THOSE graphics cards, apparently). I'm really set on an emerald theme, but even before I upgraded I always had this window popping up warning that my windows are not composited. I eventually installed the ccsm, and after installing emerald, dling my theme, highlighting that, clicking the desktop effects button, restarting about ten times, adjusting compiz settings etc. i'm still having problems activating the theme and wondering if the composited windows has anything to do with it? I've tried everything that the forums suggest, maybe I'm missing something.

When I type in emerald --replace the top parts of the windows change to the theme but everything else stays the same as my regular metacity "no desktop effects" theme. boooring. I want the neato semi translucent terminal screen and the colour theme. any suggestions? I'm kind of disappointed because I just deleted my vista system (not that that was a SUPER gem to begin with) in order to switch to Ubuntu...

---

### Post by Aemaeth on 2009-10-29
Well I cannot help with the theme but as for the terminal you can try edit > profiles and mod the terminal from there. however I prefer the quake style yakuake or guake. 

Don't worry... it will be pretty in no time...

---

### Post by Marrkk on 2009-10-31
i'm not a Gnome user really, but if i have to install or use Gnome, i Must  hve a few shadows and a bit of translucency..
so, before u give up totally with compiz.. and assuming your video card plays with xorg nicely, either installMac4Lin

[http://sourceforge.net/projects/mac4lin/](http://sourceforge.net/projects/mac4lin/)

extract, then run (in the terminal) mac4lin install.sh or whatever its called.. this will try to
 (if u answer yes to the question!)
enable Metacity compositing easily.

i cant say if it'll help with Compiz,
** BUT ** KDE (Kubuntu 9.10) for example does all this almost by default,
without Compiz etc. its part of KDE, not another 'layer' like in Gnome.
so if u come to blow your Linux install away, this may be another set of options.
hth

---

### Post by braete on 2009-10-31
> **armoftheland said:**
> Hi everyone, I've just installed 9.10 and finally have been able to play with my compiz and emerald themes (i've got one of THOSE graphics cards, apparently). I'm really set on an emerald theme, but even before I upgraded I always had this window popping up warning that my windows are not composited. I eventually installed the ccsm, and after installing emerald, dling my theme, highlighting that, clicking the desktop effects button, restarting about ten times, adjusting compiz settings etc. i'm still having problems activating the theme and wondering if the composited windows has anything to do with it? I've tried everything that the forums suggest, maybe I'm missing something.

When I type emerald --replace the top parts of the windows change to the theme but everything else stays the same as my regular metacity "no desktop effects" theme. boooring. I want the neato semi translucent terminal screen and the colour theme. any suggestions? I'm kind of disappointed because I just deleted my vista system (not that that was a SUPER gem to begin with) in order to switch to Ubuntu...

for composition and emerald i think you need xcompmgr (then add in the startup list "xcompmgr -c -f -n"), but dont quote me on that, i think i did this to fix cairo-dock + emerald some time ago ...

transparency for terminal: open a terminal and go to edit/profile preferences and under the background tab select transparent the set the slider to how you like it :)

---

