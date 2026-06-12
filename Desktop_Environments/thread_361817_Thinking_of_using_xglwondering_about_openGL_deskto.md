---
title: "Thinking of using xgl/wondering about openGL desktop acceleration on a Pentium 2"
date: 2007-02-14
forum: Desktop Environments
---

### Post by jordoex on 2007-02-14
So... the title says it all.

The computer has a Geforce2 and Ubuntu edgy.  I want to use it for mostly programming.

If i used Compiz or Beryl I'd have all of the bells and whistles off, obviously, or maybe Metisse would work. Or is there a way to pipe xserver instructions to xgl or aiglx instead of sofrtware rendering to take the load of the cpu using a normal window manager (KDE, Xfce or IceWM would be my choice, I simply dislike Gnome for some reason)

Thanks!

---

### Post by Paerez on 2007-02-14
Well you can run normal Xorg with direct rendering. This will use your geforce to render the screen, without using beryl.

If your resolution is low and you turn most of beryl's stuff off, I think you should be ok.

If you had 800x600 rez you would be fine. 1024x768 probably. More than that will be tough.

Experiment!

---

### Post by jordoex on 2007-02-15
Yeah, i don't have a working monitor at the moment (I'm gonna borrow my uncle's old one, my cousin's that he doesn't need(setting up a server) or get one from eBay or Craigslist).
So results will take a while to post.

And about direct rendering, do i use my current **xorg** and modify config, or do I install **xgl**? I have the nvidia proprietary drivers installed already.

All of the info on this is very fuzzy.  Someone should write a wiki page.

---

### Post by jordoex on 2007-02-15
*found the wiki page. It's under composite manager. I might make an autoforwarding wiki page.  It includes instrudtions for setting up xgl/gnome, xgl/kde and xgl/xfce, without beryl or compiz, which is really nice.

---

