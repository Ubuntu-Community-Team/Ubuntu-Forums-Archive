---
title: "Nexuiz - Won't Run Fullscreen"
date: 2008-06-02
forum: Gaming &amp; Leisure
---

### Post by RobbieB on 2008-06-02
Gday,
     Installing Nexuiz from the repositories I've had a few issues.
The game starts up and loads the menu fine, but for some reason it just won't run full screen or capture my mouse movements properly. (included a screenshot)

I've set a custom resolution in the config file to 1280x800 to match my laptop screen, but the problem existed before I changed it as well. I've made sure that the value for running fullscreen in the config file is true too...

Any suggestions?

[IMG]http://i28.tinypic.com/25ibuwl.png[/IMG]

---

### Post by Perfect Storm on 2008-06-02
Disable compiz;
```
metacity --replace
```

Run the game.
When done playing.

```
compiz --replace
```

Or install fusion-icon for point'n'click.

---

### Post by RobbieB on 2008-06-02
Worked perfectly, thanks alot! :)

---

### Post by F-3000 on 2010-08-25
> **RobbieB said:**
> Worked perfectly, thanks alot! :)

I second that, with Ubuntu 8.04.

---

