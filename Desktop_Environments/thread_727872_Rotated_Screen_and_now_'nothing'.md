---
title: "Rotated Screen and now 'nothing'"
date: 2008-03-18
forum: Desktop Environments
---

### Post by stork123 on 2008-03-18
I work p to a pesky green line on my LCD screen and was playing with the appearance settings. In doing so, I thought I'd rotate the screen to ensure the monitor is the problem. Now I have a blank screen. I've opened the terminal but not sure what to do next?
 I've tried sudo dpkg-reconfigure -phigh xserver-xorg and nothing...

looking at editing the xorg.conf file but see nothing indicating rotation is set there?

any thoughts?
is there a way to restore a 'default' display setting setting?


THANKS!

 I know just enough to get me in trouble... but thats how you learn i guess.

---

### Post by erginemr on 2008-03-19
Hi,

What do you mean by *"I thought I'd rotate the screen to ensure the monitor is the problem"*. I cannot comprehend the meaning of *"rotation"* here...

---

### Post by Peter09 on 2008-03-19
Note that this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

should really be this

```
sudo dpkg-reconfigure xserver-xorg
```

to get a user interface (no phigh)

PC

---

### Post by dltccf on 2008-03-28
I get this problem also, On two different machines, One a Dell GX620 with dual monitors. I have them both in "portrait" mode so i need to rotate them left 90 degrees. As soon as I do that using the new Monitor resolution feature it crashes. I tried it on a Dell 4500S with a single monitor and got the same result. This is definitely a bug with this new feature.

---

### Post by theeldest on 2008-03-28
I've found that monitors can quite often act like an Etch-A-Sketch. If you just pick it up and give it a good shaking, it should help reset everything.

Give it a try and let me know how it works.

[/joke]

---

### Post by BOBSONATOR on 2008-03-28
^lol, good one.

As i was reading the orig post, i couldnt resist laughing, "give it a rotate" (funny enough i do that too)

try disabling compiz, and state what gfx card you have, and what driver you are using.

---

