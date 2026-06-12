---
title: "[SOLVED] Matchbox-session, something missing?"
date: 2008-06-18
forum: Desktop Environments
---

### Post by Xyem on 2008-06-18
I've done a minimal 8.04 install along with xorg, wdm and matchbox. I start matchbox using 'matchbox-session' which works fine but when I start an application, something seems to be missing.

In the top right corner, there is just a large black block. If I click in it, about 3/4 of the way across, it closes the window ( and therefore, application ) so I think something should be displayed there.. so my first question is, have I missed something, is is mis-configured or is that how it is supposed to be? I've attached a screenshot..

My second question is is there an easier way to change between running applications than Launcher -> Desktop -> Back -> Active tasks -> XYZ?

---

### Post by Xyem on 2008-06-24
It seems there is a package which isn't recommended or suggested by any other matchbox package: matchbox-themes-extra

I installed that and then started with
> matchbox-window-manager -theme [theme-name] and the full functionality of matchbox appeared. It's pretty cool :)

---

### Post by Xyem on 2008-09-01
Just a quick additional note:

You don't have to install that package, matchbox seems to come with the 'blondie' theme which you can use.

---

