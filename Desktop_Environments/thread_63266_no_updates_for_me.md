---
title: "no updates for me??"
date: 2005-09-07
forum: Desktop Environments
---

### Post by X5-655 on 2005-09-07
I installed Ubuntu on both my Dell Latitude CSx laptop, and a mini PC which is made for Linux (it has a sticker on the back stating no Windows support, only *nix allowed), and it says I have no updates available.

However, when my father installed Ubuntu on his PC (his first Linux), it says he has 50 updates available and has a red icon up in the top right corner of the screen next to the clock.

How come I'm not getting these updates?

---

### Post by Steve1961 on 2005-09-07
Once you're online check that you have all the repositories you need by following the instructions in this guide:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Then open a terminal and run the following two commands:

sudo apt-get update
sudo apt-get upgrade

---

### Post by X5-655 on 2005-09-07
[QUOTE=Steve1961]Once you're online check that you have all the repositories you need by following the instructions in this guide:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Then open a terminal and run the following two commands:

sudo apt-get update
sudo apt-get upgrade[/QUOTE]

thanks, it updated...   :)

one question though, how come on my fathers PC, it asked him what resolutions he wanted to use on his monitor, while my PC (the mini *nix only one), did not ask?  It only gave me up to 832x624, and I can't access 1024x768 on mine..

also, since my father messed up on his selection, and only selected 800x600, is there a way to re-select and chose 1280x1024?  he's stuck with a small resolution and can't get much done, and he doesn't want to have to reinstall to get that screen up again..

---

### Post by Stormy Eyes on 2005-09-07
[QUOTE=X5-655]one question though, how come on my fathers PC, it asked him what resolutions he wanted to use on his monitor, while my PC (the mini *nix only one), did not ask?  It only gave me up to 832x624, and I can't access 1024x768 on mine..

also, since my father messed up on his selection, and only selected 800x600, is there a way to re-select and chose 1280x1024?  he's stuck with a small resolution and can't get much done, and he doesn't want to have to reinstall to get that screen up again..[/QUOTE]

try running **sudo dpkg -reconfigure xserver-xorg** from a terminal on each machine, and then reboot.

---

### Post by fimbulvetr on 2005-09-07
[QUOTE=X5-655]thanks, it updated...   :)

one question though, how come on my fathers PC, it asked him what resolutions he wanted to use on his monitor, while my PC (the mini *nix only one), did not ask?  It only gave me up to 832x624, and I can't access 1024x768 on mine..

also, since my father messed up on his selection, and only selected 800x600, is there a way to re-select and chose 1280x1024?  he's stuck with a small resolution and can't get much done, and he doesn't want to have to reinstall to get that screen up again..[/QUOTE]


System->Preferences->Screen Resolution

---

### Post by X5-655 on 2005-09-07
[QUOTE=Stormy Eyes]try running **sudo dpkg -reconfigure xserver-xorg** from a terminal on each machine, and then reboot.[/QUOTE]
my PC gave me this:

dpkg: conflicting actions --control and --remove

Type dpkg --help for help about installing and deinstalling packages [*];
Use dselect for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
------------------------------------------------

i won't be able to try it on my fathers PC, his is passworded and he's at work..

---

### Post by X5-655 on 2005-09-07
[QUOTE=fimbulvetr]System->Preferences->Screen Resolution[/QUOTE]

on my PC, i am only seeing 832x624 as the highest resoluion, where in Windows I could do 1024x768...

I remember trying that on my fathers PC, and it listed 800x600 at 60 Hz as the highest..

---

