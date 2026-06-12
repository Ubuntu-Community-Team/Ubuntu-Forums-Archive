---
title: "Fedora help (thinkpad x200)?"
date: 2008-12-01
forum: Fedora/RedHat and derivatives
---

### Post by Ub1476 on 2008-12-01
Well, I posted this in the Fedora forums too, but I'll give a try here too. :)

So yesterday I installed Fedora 10 (gnome live x86_64), because Ubuntu wasn't working quite right with my Thinkpad X200. Well, Fedora works better, but I still need to tweak it a bit.

I'm looking at several guides from tuxmobil and thinkwiki, and to control the fan I need to install some [tpfand ]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_&_8.10_on_an_X200#Fan") packages. I can't find those in Fedora though.. Please help.

Also I try to get the middle mouse scrolling working. In Ubuntu, I could follow [this guide]("http://blog.aliencam.net/2008/11/tpmiddlemouse-ubuntu-810/"), but that doesn't work in Fedora.

I tried out Cheese too, but it doesn't show any recording from the integrated camera. Do I need gstreamer packages or something?

Also some function (FN) keys do not work, which did work in Ubuntu. Is there a certain driver I have to install, or configure something?

Also, I installed ccsm, but after enabling some plugin, the window-border vanished and now Compiz is totally broken.. I removed the package (ccsm + deps) and the compiz dirs in my home folder. Running Compiz returns a "texture from pixmap missing" error. Running integrated intel. Also does anyone know where the xorg.conf file is?

---

### Post by deadrabbit on 2008-12-15
I'm running Fedora 10 on my X200, and I've run in to many of the same issues.

-No luck with tpfand in Fedora, but I haven't tried very hard

-No luck with middle mouse scrolling. I imagine I've tried the same guides you have found. Mostly, I want middle mouse scrolling for Firefox, which does work if you turn on autoscrollCursor in about:config

-Cheese doesn't work, along with everything else that uses gstreamer for video. Skype does work, but who knows why, since it's closed source crap.

-Which function keys aren't working? I know sleep, battery, lock and brightness work for me. I think they work since I have the tpd package installed, but I can't remember

-The easiest way to get compiz going is to use compiz-fusion with fusion-icon. The xorg.conf file isn't used by default - it's generates those settings on the fly I think. Try the fusion-icon package though, it may solve your problems.

My biggest complaint is that undocking doesn't work with the ultrabase, leading to a lot of unnecessary restarting. It would also be nice to get audio to work with the ultrabase, and to get the fan speed under control.

---

