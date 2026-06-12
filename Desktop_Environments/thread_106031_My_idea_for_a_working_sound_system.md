---
title: "My idea for a working sound system"
date: 2005-12-19
forum: Desktop Environments
---

### Post by ace2005 on 2005-12-19
I want to use something like arts to be /dev/dsp and the real soundcard to be on /dev/dsp1.

So all the programs like ET and VMWare will use /dev/dsp and that'll go to arts and all the other programs that can use arts will use it directly.

I've tried other ways to get many things to play sounds at the same time but some apps want to use the sound device directly so i thought what if the real sound device they wanted use was fake and was just something that relayed the sound to a mixer.

Is it possible???

---

### Post by holiday on 2005-12-19
Nobody's answering you so I'll take a shot. 

You could try working with symlinks. 

$ man ln

You may have already explored that route and excuse me if so, but I've solved some problems like the one you're talking about by creating links. symlinks are really very powerful.

---

### Post by ace2005 on 2005-12-21
um... what is a symlink :confused: 

if its like a shortcut then what does /dev/dsp have to be linked to, there is no /dev/artsdsp

---

### Post by holiday on 2005-12-21
In the sober morning light, I don't think this is going to work for you because /dev/dsp probably already exists in which case you can not use its name for another object. 

A linux link is like a windows shortcut in the way that a computer is like a typewriter. They're fun to just play with. Essentially a link is an named object that points to another object so that the new name is an additional name for the other object. But there are hard links and soft links -- read the man pages. 

In firefox, enter man:ln in the address field. 

I was thinking something like

sudo ln -s /dev/dsp /dev/dsp1 

But thinking about it I'm sure that  will fail.

---

