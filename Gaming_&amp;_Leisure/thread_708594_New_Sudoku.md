---
title: "New Sudoku?"
date: 2008-02-26
forum: Gaming &amp; Leisure
---

### Post by dandydan on 2008-02-26
I have been enjoying Sudoko under Feisty Fawn and it had an option for entering custom games.  Now since I upgraded to Gutsy Gibbon that option seems to have disappeared.  Can I get the old version back somehow?  I somehow got this posted on absolute begginers instead of gaming. is it possible to move?

---

### Post by erginemr on 2008-02-26
You can try the following:

1. From this site:
[http://packages.ubuntu.com/feisty/gnome-games](http://packages.ubuntu.com/feisty/gnome-games)
download "gnome-games" & "gnome-games-data". They are for Feisty and their version is "1:2.18.1-0ubuntu1".

2. From Synaptic, uninstall "gnome-games" & "gnome-games-data". Their version is "1:2.20.3-0ubuntu1".

3. Double click on the Debian packages you have downloaded and install them.

4. If all games (and Gnome-Sudoku) work as you expect, then to prevent synaptic from bothering you with an update for "gnome-games", edit the file:
```
gksudo gedit /var/lib/dpkg/status
```

5. Find the line:
```
Package: gnome-games
```
and change the version number to:
```
Version: 1:2.[COLOR="Red"]21[/COLOR].3-0ubuntu1
```
Again find the line:
```
Package: gnome-games-data
```
and change the version number to:
```
Version: 1:2.[COLOR="Red"]21[/COLOR].3-0ubuntu1
```

Save and exit. And that's it.

---

