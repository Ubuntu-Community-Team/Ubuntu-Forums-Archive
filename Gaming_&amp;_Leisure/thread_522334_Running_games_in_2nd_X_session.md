---
title: "Running games in 2nd X session"
date: 2007-08-10
forum: Gaming &amp; Leisure
---

### Post by Zylar on 2007-08-10
The biggest problem I seem to run into is that root privileges are needed at some point to start the 2nd session. Here's my Diablo II script:
```
X :3 -ac & nvidia-settings --load-config-only
sleep 2
DISPLAY=:3 WINEDEBUG=-all wine "c:\Program Files\Diablo II\D2Loader-1.11b.exe" > /dev/null
```

So what I end up doing is opening a terminal and:
```
sudo ./scripts/d2.sh
```

Is there a way to have a launcher that does the same thing?  I tried this script:
```
gksudo X :3 -ac & nvidia-settings --load-config-only
sleep 2
gksudo DISPLAY=:3 WINEDEBUG=-all wine "c:\Program Files\Diablo II\D2Loader-1.11b.exe" > /dev/null
```
I was hoping that it would ask for my password for the first gksudo, which it did,  and remember it for the 2nd.  Doesn't work though, never starts the 2nd session.  Ctrl-alt-F9 just gets me the blinking cursor.  If I try it in a terminal it's showing the help for gksudo, so I must be doing something wrong.  Maybe need a --preserve-env in there?  Or a gksudo for the nvidia-settings?

Also is there a way to have the 2nd session end when the game is exited?  I left a game running and a family member couldn't figure out how to get back to the desktop after exiting the game.

Thanks for any help,

---

### Post by cogadh on 2007-08-10
Open the file /etc/X11/Xwrapper.config in a text editor and change the line "allowed_users=console" to "allowed_users=anybody". Save the file and restart X, you will now be able to start the X session without sudo.

As for ending the second session, you just need to hit CTRL-ALT-BACKSPACE to stop it and go back to the default desktop.

---

### Post by Duncan_Idaho on 2007-08-10
I'm a bit curious
why would someone want to start a 2nd X sesion for gaming? :confused:
besides the just-'cause-I-can answer :lolflag:

---

### Post by Zylar on 2007-08-10
Wonderful, thanks Cogadh.

As to why, mainly just because I seem to have better performance and can more easily alt-tab (or ctrl-alt-F* actually); many games seem to have alt-tab issues when running fullscreen.

Edit: so no way to ctrl-alt-backspace at the end of the script?

---

### Post by cogadh on 2007-08-10
> **Duncan_Idaho said:**
> I'm a bit curious
why would someone want to start a 2nd X sesion for gaming? :confused:
besides the just-'cause-I-can answer :lolflag:
Mainly it is a performance tweak. Since Windows games run through Wine don't need a window manager to run in X, having the window manager running in the same session as the game can sometimes cause issues (like the ALT-TAB problem Zylar mentioned). You can get an even bigger performance boost if you shut down the current X session and then launch the game in its own X session. All of the resources that are normally occupied by the desktop manager and any other GUI apps that normally run are released for use by the game.

Oh, and also just 'cause I can :)

---

### Post by hikaricore on 2007-08-10
> **cogadh said:**
> You can get an even bigger performance boost if you shut down the current X session and then launch the game in its own X session.


Heh, I used to do this to play WoW on my PCI GeForce and 256mb system ram.
Popped over to tty1 run my own kill script to end useless processes.

:popcorn:

I had a script setup that launched fluxbox, and mocp (cli music player) along with WoW.
Everything I needed and no gnome/kde overhead.

---

