---
title: "Mythtv+lirc, a 99% victory..."
date: 2006-10-07
forum: Desktop Environments
---

### Post by piksi on 2006-10-07
Hello,

I'm happy to report that i'm running Mythtv 0.20 with Nebula PCI DVB card on Dapper with Geforce 7600GS on dual setup (Surfing on display, mythtv running on tv).

Nearly everything is working perfectly, but there are two small annoying things that bother me for which i haven't found a solution to after a furious search:

1) I'm currently running ubuntu server with kdm login+blackbox and i'm really hesitant to install dozens of extra packages (*-desktop) because i already have a neat desktop system (this comp is meant to work 90% as a server). My dual displays are set in xorg.conf (nvtv refuses to identify my display card), so there's a bit of fighting going on about focus between the programs (mythfrontend and others). For example, i need to keep mythfrontend in focus to direct the lirc keypresses to it. How can i modify my display/lirc setup to be able to run mythfrontend separately on tv-out and direct only lirc output to it?

2) What extra commands or parameters do i need in my blackbox init file to be able to autostart the frontend into tv-out when i log in ?

I really hope someone knows the answer to at least question no.1 :-) In return i'll gladly assist anyone fighting with nebula cards and mythtv config!

---

### Post by superm1 on 2006-10-30
1) Unfortunately, there is no way to allow lirc to completely work unless mythfrontend has focus.  It will still be able to focus some menus if you use native lirc support instead of irxevent.  I've run into this same problem too.  I run metacity, with 2 seperate X displays.  When I move the mouse to the tv, it automatically focuses mythfrontend.  When I move it back to my display, it puts focus back on the app that i'm working with.  This works for the most part for me.

2) I've never used a blackbox init, but if its anything like fluxbox, there should be a startup file in (i think) ~/.blackbox/startup.

Look at this section of my myth howto.  It will detail a lot of apps that you can add to startup and their purposes.
[https://help.ubuntu.com/community/MythTV_Edgy_Frontend#head-f45e9d3b09cfac420cb45a5d87c5ad3228204366](https://help.ubuntu.com/community/MythTV_Edgy_Frontend#head-f45e9d3b09cfac420cb45a5d87c5ad3228204366)

---

### Post by frokki on 2007-10-24
> **superm1 said:**
> 1) Unfortunately, there is no way to allow lirc to completely work unless mythfrontend has focus.Forgive me if this is a stupid question, but is there no way to assign global shortcuts for MythTV Frontend? Like my keyboard multimedia buttons - they don't need any focuses to work.

---

### Post by frokki on 2007-12-27
Finally got my Nebula remote working without focus, by just following [this](http://ubuntuforums.org/showpost.php?p=3099393&postcount=3) post step by step. :)

---

### Post by superm1 on 2007-12-27
> **frokki said:**
> Forgive me if this is a stupid question, but is there no way to assign global shortcuts for MythTV Frontend? Like my keyboard multimedia buttons - they don't need any focuses to work.
Global shortcuts, well not that I can think of.

---

