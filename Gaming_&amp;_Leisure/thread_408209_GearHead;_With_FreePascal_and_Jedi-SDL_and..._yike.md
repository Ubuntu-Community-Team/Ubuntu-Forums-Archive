---
title: "GearHead; With FreePascal and Jedi-SDL and... yikes. (Edgy)"
date: 2007-04-13
forum: Gaming &amp; Leisure
---

### Post by Keiseth on 2007-04-13
Hello! I'm pretty new to Ubuntu and Linux in general, having it for about a week or so now? It's a very enjoyable experience, learning how to use a new operating system; and I plan to stick with it primarily. Right now I'm using Kubuntu 6.10 with the gnome-desktop installed, so I can use either as the situation demands it. Handy.

Anyway, to cut to the chase, on a windows machine I was playing a Roguelike called GearHead...
[http://gearhead.roguelikedevelopment.org/](http://gearhead.roguelikedevelopment.org/)

...And I enjoyed it a bit. I tried installing it with the synaptic package manager (I may of been using Ubuntu 6.06 then) - And it seemed to install but as I started it up, it panned across a field (normal) but there were no mechas, no options in the menu to choose and any click or press would close the program! Not to mention it was an outdated version and I imagine the game is pretty buggy...

I tried compiling it myself but I'm pretty confused. The readme in the source says I need FreePascal and Jedi-SDL. I thought I had set up FreePascal but the supplied command didn't work. It also suggested I get Jedi-SDL out of CVS and I had never, ever done that before in Linux... but I think I managed to do it. I still had little idea how to USE it.

After all that madness I couldn't get it to work. I was going to ask if anyone can walk me through it a little, or give me some advice? I've googled and searched these forums but I haven't found anything at all. It doesn't seem to be a super well-known game.

I apologize in advance if I'm either asking something idiotic. I'm still settling into everything! I'd like to figure this out so I can compile any future versions of it, as well.

---

### Post by Keiseth on 2007-04-14
Yikes. I think I might of compiled it. I have FreePascal set up, I imagine, perfectly. I've gotten the latest Jedi-SDL out of CVS (Specifically, I chose the module "JEDI-SDL"- there was also a lower case version and Jedi-SDL1.0 or some such.)

In the console I went to the GearHead folder (fully unpacked, of course) and typed "ppc386 arena -Fu"<<Path to JEDI-SDL>>""

It seemed to compile, but the resulting executable (arena) doesn't do anything. Does anybody have any tips? Yes, I downloaded the Image files and unpacked "Images" into the "GearHead" folder. Still, the "arena" executable does nothing...

I notice I've gotten a few games from the package manager before, and their executables failed to do anything as well. I can't recall offhand which, however, so I'm of little use. XD

Edit: Sorry for double-post. I'm tired and idiotic and I didn't see the edit button...

---

### Post by macksting on 2007-12-02
It's been months with no reply. I'm starting to worry, too, seeing as how I'm trying to install the same game.
I'll check in later.

---

### Post by macksting on 2007-12-06
So the only way to get a Jedi-SDL for a Debian make, as opposed to .rpm files, is CVS?

---

### Post by macksting on 2008-01-05
Does the silence imply that CVS won't have it for Ubuntu, either?

---

### Post by Belliinator on 2008-01-31
This is an old thread, I know, but I have figured out how to run the game the 'cheat way.

If you download it from the repo's, as far as I know, you have the console version of gearhead. Go to the terminal, and rezize the window to 80*25 (by clicking and dragging a corner of the window) and type gearhead to run the game.

Or, get the precompiled binaris from:
[http://michalis.ii.uni.wroc.pl/~michalis/gearhead_unix/]("http://michalis.ii.uni.wroc.pl/%7Emichalis/gearhead_unix/And")
or
[http://camelot.homedns.org/~michalis/gearhead_unix/]("http://camelot.homedns.org/%7Emichalis/gearhead_unix/")

double click arena after extraction
make sure you have the requires sdl libraries. Jedi-Sdl doesn't seem to be required in the pre-compiled edition. Im not sure about freepascal Read the read me

I hope this helps someone

---

