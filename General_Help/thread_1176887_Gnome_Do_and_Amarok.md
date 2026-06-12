---
title: "Gnome Do and Amarok"
date: 2009-06-02
forum: General Help
---

### Post by kleinric on 2009-06-02
Howzit all, 

People who use Gnome-Do and would like to be able to control Amarok, will probably find that the Amarok plugin is dead. 

A nice way to control it while we wait for a revival is to look at the command line options for Amarok:

> 
amarok --help:

Options:
  -r, --previous            Skip backwards in playlist
  -p, --play                Start playing current playlist
  -t, --play-pause          Play if stopped, pause if playing
  --pause                   Pause playback
  -s, --stop                Stop playback
  -f, --next                Skip forwards in playlist
This is how i control it from various programs (gnome-do, easystroke etc...)
So just load the do menu and type 'amarok -t' to pause/play etc...

It doesnt have the full functionality that a plugin would probably have but at least its something...
Hope it helps,
ric

---

