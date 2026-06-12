---
title: "where do i get the latest compiz fusion plugins?"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by StevenEpic on 2007-08-20
ive been looking for oveer an hour and i cant find a tutorial :/

---

### Post by StevenEpic on 2007-08-20
anyone?

---

### Post by macaholic on 2007-08-20
What repository if any are you using?

---

### Post by st33med on 2007-08-20
If you compiled it by hand (or script), then you might want to [look here]("http://smspillaz.wordpress.com/2007/07/25/") for the screensaver, shift plugin, etc.

If you installed a .deb (meaning you used a repository), then Trevino's is most up to date currently, however, the Compizconfig manager doesn't work well. Amaranth's repo is going to have a shift plugin in a few hours (as I have been told), and as well as a few others (I think).

---

### Post by Rupertronco on 2007-08-21
Vorian's repo is my personal favorite. It's got the shift switcher :D among most of the other unofficial plug-ins and ccsm works beautifully.

---

### Post by StevenEpic on 2007-08-21
i got alot of the plugins already that came with compiz fusion
but i want to install these,
i already got the .tar.gz files but i dont know how to install them from source.
[IMG]http://compiz.org/images/thumb/b/be/3DPlugin.jpg/300px-3DPlugin.jpg[/IMG]
[IMG]http://compiz.org/images/thumb/a/aa/XglsnowPlugin.jpg/300px-XglsnowPlugin.jpg[/IMG]
and i want to get the latest plugins too :]

---

### Post by Rupertronco on 2007-08-21
The 3-d windows and snow are both available in Vorian's repo. well I'm sure the 3-d windows is, I think the snow plug-in is beyond obnoxious, so I haven't even bothered to look if it's there. You can find Vorian's repository a few threads up, if you're not used to installing software from source, I'd recommend aptitude or synaptic methods of install.

---

### Post by Inxsible on 2007-08-21
Vorian's repo ? Are you talking about this [thread]("http://ubuntuforums.org/showthread.php?t=481314&highlight=adding+new+users"), where he uses Amaranth's repos?

He used Trevinos repos previously and he has changed it now.

If Vorian has his own repos, could someone provide a link?

I had Trevino's and his latest update messed up with my window borders and so I installed amaranth's but it doesnt have all the plugins that trevino had.

My window borders is still unresolved however !!!! :(

---

### Post by Rupertronco on 2007-08-21
Vorian has his own repo:

deb [http://debs.vorian.org/](http://debs.vorian.org/) feisty extras
deb-src [http://debs.vorian.org/](http://debs.vorian.org/) feisty extras
GPG key: 22130E65

---

### Post by Inxsible on 2007-08-22
Thanks...

will try that and see how it works...but I am starting to think that my windows borders problem is not related to compiz fusion....if that is the case...i'd have to re-trace all my steps.

Trouble is ....i didnt do much except create a new user :(

---

### Post by steveneddy on 2007-08-22
@  Inxsible....

What happens when you

```
compiz --indirect-rendering --replace -c emerald
```

---

