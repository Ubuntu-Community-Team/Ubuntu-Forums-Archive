---
title: "I would like a terminal embedded/integrated into my desktop/wallpaper"
date: 2007-04-08
forum: Desktop Environments
---

### Post by Crakie on 2007-04-08
I remember seeing this a long time ago in a screenshot: a terminal seemlessly blended in with the desktop, as if it was part of the wallpaper so to speak. Using the terminal increasingly often these days, it would be really functional for me. Not to mention how cool it might look with some transparency. Any ideas on how to get that to work?

I am running Kubuntu Feisty, by the way, so I guess we're talking about Konsole.

---

### Post by ComplexNumber on 2007-04-08
i'm not entirely sure what you mean, but you could install yakuake (its in the repos). that may be what you want.

---

### Post by capitalistpiglet on 2007-04-08
I used to use a embedded eterm terminal in the desktop, but since yakuake came along ive used that since its more convenient to use.
What you want can be done with something like this.
```

Eterm  --scrollbar off --borderless on --buttonbar off -O 

```
Cant remember how to run it so it runs below other windows which i guess is what you would want.

---

### Post by chavo on 2007-04-08
You can't really do it with konsole, because konsole has a little border around the edge. You can get rid of the window decorations, but there will always be that little border. Use another terminal, either eterm as capitalistpiglet said, or urxvt, aterm, etc.

---

### Post by Crakie on 2007-04-09
Yakuake is not what I was looking for, but interesting nonetheless. I guess a borderless/buttonless/etc eterm would be getting close to what I want, provided it can run underneath windows AND can be a permanent solution, that is, does not require any action on my part after KDE has started.

---

### Post by capitalistpiglet on 2007-04-09
To get it to run as kde starts you just need to put the command into a bash script and place it in the ~/.kde/Autostart/ directory. Its not ideal but you could just use alt+f3 then advanced> keep below others every time you start eterm. There is a way to start it below other windows but i cant remember what it is.

---

### Post by Crakie on 2007-04-09
I am using Yakuake right now, which is really good. I am also studying the eterm manpage, but with Yakuake's functionality, I might decide against it after all. It's a kind of keep-myself-busy-project I guess :) Thanks for the responses!

---

