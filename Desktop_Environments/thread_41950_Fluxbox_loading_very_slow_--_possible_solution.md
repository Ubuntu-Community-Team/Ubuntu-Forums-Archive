---
title: "Fluxbox loading very slow -- possible solution"
date: 2005-06-15
forum: Desktop Environments
---

### Post by pestilence4hr on 2005-06-15
I was having trouble with fluxbox taking longer than KDE or Gnome to load, and I seem to have solved that problem so I thought I would share what I did, so that others having the same problem can see if it works for them.

The change that I think made the difference was editing ~/.fluxbox/init and modifying the value of session.keyFile and  session.menuFile to read:

```
session.keyFile:        ~/.fluxbox/keys
session.menuFile:       ~/.fluxbox/menu
```

At this point I restarted fluxbox and the problem was solved.

Two other changes that I made that did not resolve the problem was commenting out in my /etc/X11/xorg.conf file as follows:

```
#       Load    "GLcore"
#       Load    "dri"
```

I am also starting fluxbox from my .xsession file as follows:

```
export LC_ALL=C
startfluxbox
```

Additionally, I am running the backports version of fluxbox.  But if you are having this problem, try the change to ~/.fluxbox/init before you try the other changes I made.

---

### Post by Norgg on 2005-06-18
I tried all of these, none of them have fixed the problem.  I do find, however, that if I switch to TTY1 and manually kill gdm and run startx, X and fluxbox start quickly.  I have a suspicion that it's loading gnome support or something.  Things do look a lot rougher when not running it through gdm and it's Xorg rather than fluxbox that's doing all the processing on starting.

---

### Post by pestilence4hr on 2005-06-21
Alright, something must have happened that I didn't know about.  I have installed on a different box and these changes don't make any difference.  So back to the drawing board.  (and as far as I know, I don't have any gnome installed on this machine)

*Update:  I retract this.  I can't follow my own hints....I forgot  LC_ALL=C and that seemed to correct it this time.*

---

### Post by trash on 2005-06-25
I was so hoping this would be a fix for my three minute login LOL... didn't change anything here but then again I am running an extremely limited resource server install. auto sign in might help a tad, anybody know how to make it happen?

---

