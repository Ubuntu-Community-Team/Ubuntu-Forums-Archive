---
title: "gnome-terminal geometry"
date: 2018-04-23
forum: Desktop Environments
---

### Post by Skaperen on 2018-04-23
under Unity, i've been trying to get custom X terminals to be opened as desired (positioned as desired), but so far no success.  according to _man gnome-terminal_ it does have a _--geometry_ option that is described as _X geometry specification (see "X" man page)_.  the first oddity is that it uses a double-dash whereas X standard commands (see "man X") use a single-dash (e.g. _-geometry_).  just to be sure, i have used both, including both at the same time.  the double-dash form lets me set the window size but not the window position.  the window it opens always tries to "flow to the left" as far as it can without overlapping an adjacent window.  it never opens where i specify.  if i could get one to "flow to the right", this could accomplish what i want, which is to have 2 windows side-by-side with a gap between them in the center.

i also tried the classic "xterm" command.  it does open a window at the position i specify but so far i am unable to get it to use a font i specify (nothing documents where it looks for fonts).

does anyone know how to get _gnome-terminal_ to *obey* the position specified by _--geometry_ or some other option?  i am trying things by command line having not yet been able to get a .display file i create to show a button box that i can click on, on the launch bar.

---

### Post by kerry_s on 2018-04-23
your still at that?
what is the command your running?

gnome-terminal --geometry=?

so others can test the command.

---

### Post by Skaperen on 2018-04-24
i'm try to launch a terminal from a command line in another terminal.  it launches the size i ask for but not the position.

```
gnome-terminal --geometry=82x46+10+10
```

---

### Post by kerry_s on 2018-04-24
okay so on my screen 1366x768 it puts the terminal on the left side of the screen.
i can put higher numbers & it will move right.

as for the button:
```

gedit ~/.local/share/applications/terminal-1.desktop

put:
[Desktop Entry]
Type=Application
Name=Terminal-1
Comment=
Icon=terminal
Exec=gnome-terminal --geometry=82x46+10+10
Categories=System;


```

then it should show in you applications
[ATTACH=CONFIG]279429[/ATTACH]

---

### Post by Skaperen on 2018-04-24
this particular project involves starting the terminal via a command, so i am not concerned with .desktop files for this particular project.

it is the positioning of the window that was not working for me.  but i tried something odd: --geometry 82x46-0+0   ... that is, i specified a negative zero for the horizontal position, and the window opened in the far right, which is where i wanted it to open.  so i now have it working.  when my .bashrc script runs with the right conditions that exist when i open a terminal on the far left, it opens a 2nd terminal on the far right.  the button that opens the terminal on the far left was dragged in from the terminal applications listed by that ubuntu button at the top of the launch bar.  i sized that terminal using the terminal profile settings.  so now the effect is that button opens 2 terminals side-by-side ... the goal for this project.

the other project was to add a few buttons that would run my scripts to play music in the background, compatible with my music playing system.  no windows were to be opened in that other project.  i have not yet gotten any buttons to show up.  i may try to modify an existing one, next.

but today's project is now a success, despite some failure modes of --geometry, which i will disregard for now.

---

### Post by Skaperen on 2018-04-25
> **kerry_s said:**
> 
[ATTACH=CONFIG]279429[/ATTACH]

that screen looks nice, although i don't see anything i think you might be trying to show me.  also it does not appear to be Unity (bar is on top).  i am looking to switch to something else if anyone has a nice setup suggestion.  i will start another thread for it, sometime, with my requirements.

---

### Post by kerry_s on 2018-04-25
it shows the newly created terminal-1

that was pop!_os i was playing with. i've already blown that away & i'm using solus 3 budgie version. solus is the fastest distro i've come across, so i'n using for it's speed.

---

### Post by Skaperen on 2018-04-26
i see a couple term "buttons" if that's what you meant, assuming those are buttons.

speed is not by greatest concern once things are reasonably fast.  my greatest concern about most of my choices in life is to understand it.

---

### Post by kerry_s on 2018-04-26
yeap, just showing it did create the launcher.

yeah, been there, done that. when i click i want it to open, not take a microsecond to think about it. lol
i'm to old to be waiting, i tend to go with what just works & work around the stupid things.
like why would you have over amplification of sound, but the sound icon tops out at 100. ubuntu gets that right, they make the volume longer.
most other distro's don't. so i wrote a script for that.
then there's reboot/shutdown, why can't i have a icon, ubuntu mate get's that right. so i created my own & just adjust to what ever distro i'm using.
i use expose/overview a lot, why can't all distro's have that it's 2018. skippy-xd to the rescue for that.

put simple pick the closest that fills most of your needs, then bend it to your will till it does what you want.
[ATTACH=CONFIG]279445[/ATTACH]

elementary os was my favorite, so i go with that look, but i want more updated software. which is why i'm also using solus which is a rolling release.
there moto "install once update forever". we'll see how that turns out.

---

### Post by Skaperen on 2018-04-26
when you setup or try out or play with a new DE how do you isolate it?  do you just run it and let it replace the screen content?  do you run it under a different userid or directory?  do you run it in its own VM?

---

### Post by kerry_s on 2018-04-26
i usually play with it in vm to make sure it will do what i want. if it does good i then go ahead & just install it. i'll run it for awhile till i get bored or something better comes along.

---

### Post by Skaperen on 2018-04-26
i learned way back in my mainframe days (VM/CMS) that incremental upgrades can either lead to (often subtle) problems or leave them around. so with SunOS and 386BSD and Linux, i generally have isolated partitions or drives for the system (apart from user data) and do full re-installs to upgrade to a new version.  that experience and philosophy influences how i work with other things, too.  i installed Gnome over KDE, once, thinking that would make a clean switch.  nope.  funny how well it worked, though with strange confusion all over the place.

---

### Post by kerry_s on 2018-04-26
yeah, i never mix de's. i use 1 environment per install.
i try & keep it simple less things to get in the way.

---

### Post by Skaperen on 2018-04-28
i've been a Linux text console user ever since.  it was always faster than xterm under X on the same machine.  i got rather sophisticated at the text console setup.  i also did have X running for graphical needs like web browsing and photo processing.  now, hardware is fast enough that the higher speed of real text mode doesn't really help that much.  sometimes i can see the editor doing things that move stuff around, but that isn't an issue for me.

i still do editing in text mode in the terminal emulation i am running.  it is faster starting up that way, especially when editing remotely via an ssh session.

---

