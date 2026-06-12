---
title: "Swisswatch on all desktops"
date: 2013-12-09
forum: Desktop Environments
---

### Post by Azyx on 2013-12-09
Hey.
I have installed swisswatch on my computer and have added it in Startup Application with 1 seconds tick

```
swisswatch -tick 1
```

What I don't have found is how I get it to show on every workspace. There is a man-page, but I'm are bad to under stand it:

[http://pwet.fr/man/linux/commandes/swisswatch](http://pwet.fr/man/linux/commandes/swisswatch)

I suspect it may be to use OPTION [COLOR=#a52a2a]-display[/COLOR], but in the help it say look at: X(1), but I don't get anywhere...

Someone who are more familiar with man-pages terminology or understand how I let the clock be visiable on all workspace? If I right-click on the clock-menu and chose "Always on Visible Workspace" it work, but I wan't it happen autamatically on startups ( manage to add the OPTION -tick, 1 second ;) )

/Cheers

PS:  -help get this...

Azyx@Computer:~$ swisswatch --help
usage: swisswatch [toolkitoptions ...]

---

### Post by tgalati4 on 2013-12-09
If you right-click the clock, do you see any options?  Perhaps "Always on Visible Workspace"?

---

### Post by Azyx on 2013-12-09
Yes: as I said : " If I right-click on the clock-menu and chose "Always on Visible  Workspace" it work, but I wan't it happen autamatically on startups (  manage to add the OPTION -tick, 1 second :wink: )"

---

### Post by stinkeye on 2013-12-09
Don't know if it's possible through swisswatch options.
You could set to to be sticky using **compizconfig-settings-manager**(ccsm) though.
Could also remove decoration also using ccsm.

---

