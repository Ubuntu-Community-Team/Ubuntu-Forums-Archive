---
title: "How do I disable Emerald?"
date: 2007-12-05
forum: Desktop Effects &amp; Customization
---

### Post by Kaphix on 2007-12-05
I searched for this, and got [http://ubuntuforums.org/showthread.php?t=586754](http://ubuntuforums.org/showthread.php?t=586754)
The problem is, I uninstalled emerald and all of its components, but the theme remains. Its a bit uglier, but still glowing, transparent, and has shadows. This is the problem:

My computer runs smoothly with Emerald themes enabled and Compiz enabled, except my browser. I can scroll text documents and applications without lag, but for some reason in browsers it lags unless i disable GL desktop. Problem is, I find some of the compiz functions useful, and the rest fun. I can do without Emerald themes, but I'd like to keep compiz. 

I have another problem, and I think it has something to do with themes as well. I cannot play any music or movies in ANY media player. It loads it, then crashes. I disabled GL desktop, and it allowed me to play movies, but I still cannot play music.

---

### Post by firefeather on 2007-12-05
I don't know about the other stuff, but if you edit /usr/bin/compiz , there are a couple of options in there. If you disable Emerald it will fall back to gtk_window_decorator . It has slight transparency for unselected windows' title bars, but otherwise is just like metacity's normal way of handling window decorators.

You'll need to change the option in the /usr/bin/compiz script every time compiz updates.

(Now, I don't know a ton about Ubuntu; I've only been using it since April, but this is as far as I know!)

---

