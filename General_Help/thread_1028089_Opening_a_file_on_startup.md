---
title: "Opening a file on startup"
date: 2009-01-02
forum: General Help
---

### Post by lkrubner on 2009-01-02
Macintosh computers used to have an easy to use Startup folder into which you could throw stuff if you wanted stuff to start every time you booted up. If I was working on some files for a long time, I'd drag an alias of the file to the Startup folder, so it would open I turned on the machine. I'd like to do that with my Ubuntu machine, too, though I get the sense that getting something to start on start up is surrounded with a bit more ceremony on a Ubuntu machine? Do I have to edit configuration files and such? Can someone tell me how I can get a text file to open, or a command to run, everytime the machine starts up?

---

### Post by cdtech on 2009-01-02
You can use the "System > Preferences > Sessions" to include startup programs.

---

### Post by the yawner on 2009-01-02
> **cdtech said:**
> You can use the "System > Preferences > Sessions" to include startup programs.

But you'll also need to know the options of a command for every program you'd want to start with your specified files. For example:

- To open a txt file
```
gedit filename
```
- To open a txt file on a certain directory
```
gedit /path/to/filename
```

---

### Post by Forlong on 2009-01-02
If I remember correctly, KDE has that exact same feature with that startup folder. Used to confuse me quite a bit. :D
So, you might want to give KDE/Kubuntu a try.

But generally, **the yawner**'s way is the way to do it on GNOME. :)

---

