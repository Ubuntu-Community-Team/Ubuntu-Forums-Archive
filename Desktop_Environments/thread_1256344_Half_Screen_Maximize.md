---
title: "Half Screen Maximize"
date: 2009-09-02
forum: Desktop Environments
---

### Post by rabklyn on 2009-09-02
Anyone know how to make a window fill half of your screen like in windows 7?
I'd like to be able to display any 2 windows side by side on my wide screen monitor without having to manually adjust the bounds.

---

### Post by mimor on 2009-09-02
I think there's such an option in compiz-fusion.
But I'm not sure :s

---

### Post by ceti331 on 2009-09-02
been trying to hack similar things, e.g. bind a hotkey with "wmctrl -r :ACTIVE: -e 0,0,0,840,1050" etc, had that working in fluxbox

---

### Post by rabklyn on 2009-09-02
I've installed compiz-fusion and it's pretty great, but dont see how to make it work for half screen.  
Any Compiz-fusion experts out there?

---

### Post by bear24rw on 2009-09-02
Check out the compiz plugin Maximumize under Window Management

---

### Post by rabklyn on 2009-09-03
I've got  a solution:
I used the Grid plugin under Window Management in Compiz and set keystrokes for "Put Left" and "Put Right".

Thanks, everyone.

---

### Post by ddgromit on 2010-10-20
Installing the grid plugin worked for me on 10.10 Maverick.  It doesn't look like its in the package managers so I just followed the directions on the [main plugin site]("http://wiki.compiz.org/Plugins/Grid"), including the git-checkout part.  Then it just showed up in my compizconfig settings manager under Window Management.

> 
[SIZE="4"]Install[/SIZE]

Note that grid is now included in compiz so you're unlikely to need to fetch from git unless you've an old version of compiz.
On a fresh install of ubuntu 8.10 you will need to uncomment the "intrepid-backports main restricted universe multiverse" and "intrepid partner" repositories in your sources.list

* update your list of available packages
* install those necessary dependencies
* clone the git repository
* make, make install
* enable and configure "grid"

```
sudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install git-core libtool compiz-dev compiz-fusion-bcop compizconfig-settings-manager
mkdir tmp;cd tmp
git clone git://anongit.compiz-fusion.org/compiz/plugins/grid;cd grid
git-checkout 1281082ba678033e515a19419ca8ffe8641d744b
make
make install
ccsm (to enable and configure "grid")
```

---

