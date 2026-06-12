---
title: "different default ServerLayouts for different logins - possible?"
date: 2008-02-04
forum: Desktop Environments
---

### Post by Redsandro on 2008-02-04
Hi,

I've been looking here and there for a while now but cannot seem to find the - if any - solution.

(Ubuntu 7.04 / Gnome)

There's a ServerLayout for office work, one for media work and one for MythTV (which I only want on TV). No problems, but the switching is lame. Office is default, and in order to switch, I type
```
startx -- :1 -layout "tv"
```or```
startx -- :1 -layout "tv-clone"
```depending on what I want and it works like a charm. I can ctrl+alt+F# to switch back. However, MythTV is broken when running as a secondary session, and I want to use autologin for Myth, which also works perfectly but then it takes the default ServerLayout which is for office work.

Using this article, I got me some options to switch layout PRIOR to logging in, which is somewhat neat:
[http://nat.truemesh.com/archives/000706.html](http://nat.truemesh.com/archives/000706.html)

But if TV is not plugged into the computer anymore after MythTV (for reasons) and I want to do office work, I have to plug in the tv in order to see where to click to set de ServerLayout back. Hassle.

Can't the default ServerLayout be dependant on what login I use?
Office: Monitors
MythTV: TV
Media: TV-Clone?

I believe MythTV uses a different desktop manager from GNOME, so maybe I can use that in my advantage. That would at least make this work for 2 out of 3 options.

---

