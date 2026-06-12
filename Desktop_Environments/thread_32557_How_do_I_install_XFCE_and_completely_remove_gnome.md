---
title: "How do I install XFCE and completely remove gnome"
date: 2005-05-08
forum: Desktop Environments
---

### Post by DaturaX on 2005-05-08
Hi,

I am running gnome on this system of mine and its getting a little slow for my liking. My question is, how do i remove gnome and install XFCE?

Can someone guide me along?

Thanks

---

### Post by cdhotfire on 2005-05-08
easiest way is, insert cd, and type in server
after install is finished login, and then do
```

$ sudo pico /etc/apt/sources.list

```

then uncomment the all the "deb"  sources.
should be like:
# deb ......
delete the #.

the
```

$ sudo apt-get update
$ sudo apt-get install xterm x-window-system-core gdm xfce4 abiword mozilla-firefox menu

```

and enjoy.:)

---

### Post by Gentist on 2005-05-08
I was given [this link](http://ubuntuforums.org/showthread.php?t=24403&highlight=debfoster), which explains how to use "Debfoster", when I asked a similar question. Though be careful, it's quite powerful in the sense that a wrong configuration could mess up your system.

Here's a few steps you can follow if you want, but make sure you know what you're doing, as I'm a newbie to this packaging system myself. In other words, I won't guarantee that this works.

1. Follow the guide in that thread, and make sure you keep the critical packages mentioned there.
2. After you've created the keepers file, remove everything that isn't needed from it (make sure you keep the gnome stuff, like ubuntu-desktop, for now).
3. Add the appropriate package for XFCE (dependencies should follow, if not, add them too).
4. Run "debfoster -f"
5. Switch over to XFCE and make sure that *nothing* Gnome related is running (if you want to keep the gdm, make sure you add it to the keepers file).
6. Remove the Gnome packages you don't want from the keepers file.
7. Run "debfoster -f" again.
8. Pray that you didn't miss anything.
9. Add other programs you'd want installed.
10. Run "debfoster -f" everytime you want to clean your system according to the keepers list.

---

### Post by DaturaX on 2005-05-08
I used this link.
[http://www.ubuntuforums.org/showthread.php?t=24403&highlight=debfoster](http://www.ubuntuforums.org/showthread.php?t=24403&highlight=debfoster)

Am running XFCE now. Loads faster on this server. Works like a charm and it only takes like 4 secs to load.

Thanks guys!

---

### Post by derrick1985 on 2005-05-08
[QUOTE=cdhotfire]easiest way is, insert cd, and type in server
after install is finished login, and then do
```

$ sudo pico /etc/apt/sources.list

```

then uncomment the all the "deb"  sources.
should be like:
# deb ......
delete the #.

the
```

$ sudo apt-get update
$ sudo apt-get install xterm x-window-system-core gdm xfce4 abiword mozilla-firefox menu

```
[/QUOTE]
That's the method I used personally. Google up ubuntu mini ram, read the howto and just replace XFCE with xfce4 and enjoy.

and enjoy.:)

---

