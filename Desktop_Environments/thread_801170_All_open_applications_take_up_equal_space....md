---
title: "All open applications take up equal space..."
date: 2008-05-20
forum: Desktop Environments
---

### Post by sohaibma on 2008-05-20
I am looking for an application (or a built in feature in hardy) which allows me to organize and manage all my open windows, eg. resize, make all the windows spread out equally on the desktop, etc.

Something similar to this program for windows: [http://www.winsplit-revolution.com/](http://www.winsplit-revolution.com/)

Do you know any such software for hardy.

---

### Post by Ace2016 on 2008-05-20
Yes you can do it with compiz fusion and the tile plugin

// Ace2016 //

---

### Post by sohaibma on 2008-05-20
sorry, I have via unichrome pro igp graphics card, so compiz doesn't run. Any other options?

---

### Post by Crick on 2008-10-18
Sorry I can't help those without compiz, but I thought I'd stick a little howto in here as the other threads I see here are read-only.

Some searching brings up these threads:
[http://ubuntuforums.org/showthread.php?t=609155&highlight=winsplit](http://ubuntuforums.org/showthread.php?t=609155&highlight=winsplit)
[http://ubuntuforums.org/showthread.php?t=601186&highlight=winsplit](http://ubuntuforums.org/showthread.php?t=601186&highlight=winsplit)

I thought I'd write a quick guide/howto as to how to get this working in Hardy (8.04). If you are looking to do what splitview apparently does, or ultramon does on two monitors, read on if you are trying to make more productive use of your widescreen monitor's real estate.

steve9000 has made a plugin for compiz that does the same thing, and is controlled via keyboard to make things easier and quicker. If you are reading this Steve, thanks very much for writing this! I hope this gets included in the next Ubuntu version, or compiz, or whatever.

1. ```
sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
```

2. ```
mkdir ~/compiz
```

3. ```
cd ~/compiz
```

4. ```
git clone git://anongit.compiz-fusion.org/users/stevek/grid
```

5. ```
cd grid
```

6. ```
make
```

7. ```
make install
```

7.1 You may need to enable "Normal" or "Extra" under desktop effects in System->Preferences->Appearance first. (You may also need to chown -R user:user ~/compiz in order to get things to compile.)

8. ```
ccsm
```

9. Check "grid" under "Window Management". Note you can actually click on the icon and "grid" to bring up keyboard shortcuts for placing the windows where you want them. Do not expect to have new icons come up at the top of the windows (next to minimize/maximize/close), this won't happen. However, <ctrl><alt><kp 6> is quicker anyway.

10. Play around with what the different control-alt-numeric keypad combos do to get an idea of how to use this. It's pretty intuitive.

Let me know if I have left anything out.

---

