---
title: "Noticifaction area went bye-bye"
date: 2008-01-12
forum: Desktop Effects &amp; Customization
---

### Post by t3hi3x on 2008-01-12
Ok. So sometime back I was experimenting with dual x-screens and I got kinda mad at it          and it mixing with compiz...thats another story I couldn't resolve. But when I switched back to twinview I lost my main panel. No big deal, I'll just add another one. Well when I go to add the notification bar nothing is there even if something new is created. The daemon is running and the bar is there, but no icons.

Any clue?

---

### Post by tgalati4 on 2008-01-13
Dual screens, compiz, desktop settings makes for a challenge to set up.  Try running reconfigure on the setup that you are most interested in keeping.  

I have found that mixing dual screens, compiz, and changing desktop settings results in some breakage.  It's fine if you stay in one configuration and stick with it, but make a change and stuff starts to break.

You may have to delete some configuration files and start fresh.

---

### Post by t3hi3x on 2008-01-13
> **tgalati4 said:**
> Dual screens, compiz, desktop settings makes for a challenge to set up.

Indeed a challenge. The only issue I had was that the primary screen had issues creating new objects. Twinview is fine, so I'll survive.

I actually was able fix this problem. It is very very weird, but one of my panels had another one of my panels that went missing embedded into it. This is very odd. I drug it out and got the bright idea of killing that panel and putting the notification area somewhere else. And behold that worked.

I also tested it out and found that you can't use more than one notification area. This is defect in that part of gnome...kinda disappointing in my opinion.

Thanks alot for the help. Hope this helps someone.

---

### Post by tgalati4 on 2008-01-13
A defect or a feature!  So you want a notification area in both screens?  My guess is the Gnome environment is coded to support only one notification area per Gnome instance.  With some major effort, you could recode Gnome to support remote notification.  In KDE, the monitor application (it's name currently escapes me) is actually run as a server so you can set up multiple clients to get system information (temperature, loads, etc) on multiple machines, including remote machines.  Kind of neat.  I don't know if similar capability exists in Gnome.

---

### Post by t3hi3x on 2008-01-14
I sure don't consider it a feature. The problem is in situations like my own you get where you can't have a notification area. Yet when you have the option to add one....

I guess it's opinion thing but when there is an opinion there should be options :-).


Btw I believe gnome has a daemon but the settings aren't in the GUI part of the panel...

Oh well. Really isnt a big deal.

---

