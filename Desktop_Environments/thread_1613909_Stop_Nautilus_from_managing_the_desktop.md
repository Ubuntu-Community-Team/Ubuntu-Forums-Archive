---
title: "Stop Nautilus from managing the desktop?"
date: 2010-11-05
forum: Desktop Environments
---

### Post by FatalKeystroke on 2010-11-05
How does one go about stopping Nautilus from managing the desktop?
I want to use Conky, but every time I click on the desktop, it disappears. (Don't refer me to the supposed fixes by changing "own_window_type" because that's not what I want, it doesn't work)
I don't use my desktop for any icons and I have no wallpaper, it's just #131313.
Does anyone know how I can eliminate the file manager from managing the desktop so I may use Conky?
(I have had similar problems on different distros with different file managers controlling the desktop, so I assume stopping Nautilus from managing the desktop will solve it this time)

---

### Post by phredbull on 2010-11-05
If you disable Nautilus, then what will you use for a file manager?

I'm pretty sure the problem is with your Conky config. Make sure you have this included:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
```

---

### Post by mcduck on 2010-11-05
You'll have to open gconf-editor, and remove Nautilus from the required_components under the desktop/gnome section. I'd give the exact place if I had a Linux machine at hand at the moment, but I don't so you'll have to look around a bit.

After that you'll have to edit all your launchers to run "nautilus --no-desktop" instead of just "nautilus", to avoid Nautilus launching the desktop when you try to open a file manager window.

The Places-menu is probably going to cause you problems, and you'll also loose the right-click menu on the desktop.

If I were you I'd really just get the Conky configuration right instead. It *does* work.

---

### Post by FatalKeystroke on 2010-11-05
Well this makes me feel stupid.

My problem was that when I set own_window_type to desktop, it disappeared when I clicked on the desktop, much like everyone else. Then, when I set it to override, about 3-4 minutes after logging in, Conky would show up above all my other windows.
As with virtually everything though, Googling never gives you exectly what you need, just related items, so I never saw the line:
```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```Thank you phredbull, adding that line fixed the problem.

*sheepishly*
I guess it *was* a problem with my Conky configuration.

---

### Post by phredbull on 2010-11-05
Your welcome, enjoy!:popcorn:

---

### Post by madurax86 on 2011-01-03
I also noticed that there's a option called show_desktop in gconf-editor under apps>nautilus, just untick it :D

---

