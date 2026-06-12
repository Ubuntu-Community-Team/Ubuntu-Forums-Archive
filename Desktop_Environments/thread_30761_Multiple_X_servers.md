---
title: "Multiple X servers?"
date: 2005-04-30
forum: Desktop Environments
---

### Post by graigsmith on 2005-04-30
i would like to be able to play a game in one X session and have gnome on another.

or even have a gnome session set up so that someone else can switch to a new x session and log in.

thru various online things i figured out that ctrl-alt-f7 and f8 can switch to different x sessions.  i was able to start X on the second screen, the one you press ctl-alt-f8 to get to.  every game i tried to run on it failed though. 

how many x sessions can there be? 

is it possible to run a game on one x session, gnome on another? and mabey another gnome session all at the same time in ubuntu?

any good websites that talk about this?

---

### Post by jobezone on 2005-04-30
I'm not sure what would happen if you launched Gnome in two X sessions simultaneous using the same user. 
Even if this works fine, perhaps you may not want to use gnome in the session you'll be playing games, and instead use a light window manager. Like xfce or fluxbox or others (all in universe, and easiest is xfce):

If you use GDM and want to launch a new X session:

Switch to a Virtual Terminal 1 by pressing Ctrl+alt+F1, log in with your username and do:

startx -- :1

If you want to launch another X session, you would switch to VT2, doing ctrl+alt+F2, and the command should be different, as to point to the correct screen:

startx -- :2

and another would be:

startx -- :3

You get the point?:)

This probably won't work if you've just installed ubuntu, because you don't have any window manager configured to run when using the startx command. Edit the file .xsession in your home directory by doing:

nano .xsession

(hope you know how to use nano. It's easy, commands such as Save or Quit are done by pressing Ctrl+<letter associated to function shown in the bottom of the screen> .)

and write (to launch gnome when using startx):

exec gnome-session

and save it.

It could be xfce or fluxbox or any other windowmanager you have instaled.

startx should work now.

"...gnome session set up so that someone else can switch to a new x session and log in."

Neither GDM(Graphical Greeter) nor Gnome have a button to do this in a graphical way (only by doing what I said previously).
Right, only if you use KDM and KDE, there's an option in Shutdown that's called "run session as a different user"(or something) which basically avoids doing all of what I wrote.

As for documentation, most documentation which targets users coming from windows and/or new to linux will not mention this stuff :) But still, if you haven't, search in ubuntu's wiki at [http://www.ubuntulinux.org/wiki](http://www.ubuntulinux.org/wiki) and [http://www.tldp.org/](http://www.tldp.org/) , the website of the Linux Documentation Project, probably the place where the in and out's of linux are best documented, although in a sometimes overwhelming way (specially to new users).

---

### Post by graigsmith on 2005-05-01
it just drives me crazy that theres no easy way to task out of a full screen 3d session. 
 ](*,)   :-x

i got neverwinter nights and as far as i can see there is no way to switch task and go back to the gnome desktop.

for quake 3 and enemy territory at least i can alt-tab and then bring up the console to task out.   But thats kind of cumbersome.

---

