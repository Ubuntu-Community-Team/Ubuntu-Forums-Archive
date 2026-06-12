---
title: "'Standard' keyboard shortcuts using xbindkeys"
date: 2009-11-30
forum: Desktop Environments
---

### Post by Gigi33 on 2009-11-30
Hi Ubuntu community,

I love keyboard shortcuts and use them all the time. Usually the first thing I do after installing Ubuntu is defining some shortcuts to launch my file manager, web browser, a terminal, etc.

Since I got tired of setting up the same shortcuts over and over I decided to write a little script which does that for me.

And now I feel like sharing: [http://github.com/Gigi33/gi-xbindkeys](http://github.com/Gigi33/gi-xbindkeys)

**Installation**
[LIST]
[*]Install git and xbindkeys
[*]Clone gi-xbindkeys from github
[*]Run the install script
[*]Install additional applications (optional) 
[/LIST]
For the lazy ones like me, copy and paste the following to a terminal
```
sudo apt-get install git-core xbindkeys
git clone git://github.com/Gigi33/gi-xbindkeys.git
cd gi-xbindkeys/
./install.sh
./install-applications.sh #optional

```

There are many ways to define keyboard shortcuts. One could use the System->Settings->Keyboard Shortcuts, another way would be using ccsm. I decided to use xbindkeys since it is very simple and easy to use for my purpose.

> Currently the following keyboard shortcuts are used:
 
<Super> + <T> opens your default terminal emulator.
<Super> + <W> starts your default web browser.
<Super> + <G> for the gedit text editor.
<Super> + <F> opens your files (home folder) in nautilus.
<Super> + <E> does the same as <Super> + <F>.
<Super> + <C> starts the gnome calculator.
<Super> + <R> starts dmenu_run, which kind of behaves like the windows run dialog.
<Alt> + <F3> starts dmenu, which can be used as a alternative to the <Alt> + <F2> run dialog.
<Ctrl> + <Alt> + <Del> opens the gnome system monitor.
<Ctrl> + <Alt> + <K> runs xkill which can come in handy if an application freezes.
 
The applications are only started if installed of course. To install dmenu, gmrun and vlc run 
$ ./install-applications.sh
All other applications should be included in a default ubuntu installation.
 
 
To change your default browser use the following command:
$ sudo update-alternatives --config x-www-browser
 
To change your default terminal emulator, use the following command:
$ sudo update-alternatives --config x-terminal-emulator
Some shortcuts come from the Windows world, some are inspired by [#!CrunchBang Linux]("http://crunchbanglinux.org/"), which supports many shortcuts by default.

Comments and critique are highly appreciated.

---

