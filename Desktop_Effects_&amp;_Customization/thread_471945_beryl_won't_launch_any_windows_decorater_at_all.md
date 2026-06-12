---
title: "beryl won't launch any windows decorater at all"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by il-luzhin on 2007-06-12
any suggestions?

---

### Post by LollYouSuckZor on 2007-06-12
It depends on what you already have selected.  You have to go to, "Emerald theme manager", you then select a a new theme.  Then, Reload the window manager.  If that dosen't do the trick,  make sure you have Beryl, or MetaCity depending on what kind of theme you've installed.  


Hint: Remove the top bar, use only one bar, it reduced use of RAM.

---

### Post by il-luzhin on 2007-06-12
I've reloaded both the windows manager and the decorator a half dozen times, still no go.

---

### Post by LollYouSuckZor on 2007-06-12
Okay, Um,  I remember having this problem.. You're not using 6.10 are you?

---

### Post by il-luzhin on 2007-06-12
64 bit 7.04

---

### Post by LollYouSuckZor on 2007-06-12
Okay, how did you install it? 

Via Terminal? Or Synaptic?

---

### Post by il-luzhin on 2007-06-12
automatix2

---

### Post by LollYouSuckZor on 2007-06-12
BINGO!

```

sudo apt-get remove beryl beryl-core beryl-plugins beryl-manager

```

Install it with Synaptic.

---

### Post by il-luzhin on 2007-06-12
no change.

---

### Post by LollYouSuckZor on 2007-06-12
Nope, but did you try to select a different window manager?

---

### Post by il-luzhin on 2007-06-12
Originally Emerald wasn't installed so I was trying to figure out why metacity wouldn't launch.  After installing Emerald, I was fighting to get either of them working.

No success

---

### Post by LollYouSuckZor on 2007-06-12
That's your problem.  Install Emerald.


Remove Beryl once more.  
Install Emerald with this code, as well as beryl

```

Sudo apt-get install beryl beryl-plugins beryl-core beryl-manager emerald emerald-themes
```

Restart, and you should be good...

---

### Post by il-luzhin on 2007-06-12
Sorry my friend, I think I've given you a real challenge this time.  

Still the same.

---

### Post by dabl on 2007-06-12
Are you sure you have glx and compositing set up for your video driver?  If you run beryl-manager in a terminal window, does it scan your system and indicate it's good to go, or does it generate errors?  If you search this forum and Kubuntu forum on "missing window borders" you'll find about a zillion threads, most of which will lead you to the solution you need. ;)

---

### Post by il-luzhin on 2007-06-12
the folks on the beryl forum solved my prob

```

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

```

Thanks for the help LollYouSuckZor.  Much Appreciated

---

### Post by il-luzhin on 2007-06-12
More help please!
I can't get emerald themes working.  I chose a theme then hit the launcher that executes emerald -reload and nothing occurs.

```

luzhin@luzhin-desktop:~$ emerald -reload
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

```

---

### Post by il-luzhin on 2007-06-13
sorry folks the proper command was

emerald --replace

---

