---
title: "Wallpaper on dual monitors"
date: 2009-04-26
forum: Desktop Environments
---

### Post by doriard on 2009-04-26
How is wallpaper applied separately on dual monitors under Jaunty?  Current the wallpaper is showing up half on one screen and half of the other.  How do I get it to display on each monitor?  Even better, is there a way to have separate wallpaper on each monitor?

---

### Post by Rywern on 2009-04-26
Personally i use Nitrogen

```
sudo apt-get install nitrogen
```

then i repoint it to use a specified folder (since my collection of wallpapers is around 5000 it would be a pain to scroll through them)

```
nitrogen --sort=alpha /home/rywern/Nitrogen
```

all you have to do is start the program with that line and it will be a breeze.

Sometimes the comp loses the nitrogen wallpaper so instead of repointing it all the time i just take a screenshot of my desktop (Cleaned up with no icons ofc) and use that

NOTE: i use it on intrepid still but i have had good luck with it on jaunty when ive tried

---

### Post by doriard on 2009-04-26
Does Nitrogen automatically resize high resolution photos to fit the screen?  Also, I really prefer to manual select my own photos instead of random.  It sounds like that can be done in Nitrogren, but is there a previous window when selecting images?

---

