---
title: "byobu .. i get blank screen: inoperable"
date: 2012-07-24
forum: Desktop Environments
---

### Post by stabu on 2012-07-24
Hi,

I'm a screen user, but have heard enough about byobu that I decided to try it.

I installed via apt-get install and now I have quite a number of byobu executables, but I imagine that the simple "byobu" is the one to use.

In Gnome Terminal, when I do type "byobu", I get an amazing blank screen. The F-keys seem to be powerless. Even ctl+a, c (for example) gets nothing. It actually seems inoperable.

May be I am missing something, about the first time one uses byobu. I tried byobu-config which at least let me set things, but these had no effect.

screen itself works fine. my process list suggest that the following is being launched when I type "byobu".

screen -c /usr/share/byobu/profiles/byoburc -t shell motd+shell

This is just screen, and the rc file contains

source $HOME/.byobu/profile
source $HOME/.byobu/windows
source $HOME/.screenrc

the windows file itself is blank. I guess its the profile file, that its defaults are causing.

Unfortunately the blank screen inoperable state is a fairly nasty situation to be in. I'd much prefer a bailout error of some sort.

I'd don't know if other people have had this experience.

---

