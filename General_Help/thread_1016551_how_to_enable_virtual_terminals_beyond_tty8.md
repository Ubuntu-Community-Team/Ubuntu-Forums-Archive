---
title: "how to enable virtual terminals beyond tty8"
date: 2008-12-20
forum: General Help
---

### Post by LordIshamael on 2008-12-20
hey i found a post in the ubuntu forums [http://ubuntuforums.org/showthread.php?t=874757](http://ubuntuforums.org/showthread.php?t=874757) where ibutho says that we can "enable more virtual terminals by editing /etc/inittab or in the case of Ubuntu create the relevant tty files in /etc/event.d."

if i want another virtual terminal, say at ctrl-alt-f9, what kind of file would i have to create, what would it say?id want a gui so i can log in to kde, also id be logging in as the same user on both ctrl-alt-f7 and the new virtual terminal-is that possible?

---

### Post by RealPSL on 2008-12-20
Why not try taking a copy of one of the existing ttyX files and give it the name tty9. Use ```
gksu gedit
``` to replace the lines that reference ttyX to tty9. The most important line in the file is ```
exec /sbin/getty 38400 tty6
```

The rest I do not have an answer for but I will admit that I am curious to see if it will work so please report on your findings.

---

### Post by lswb on 2008-12-20
There are a few issues here.

1, RealIPSL is right about the approach to creating additional vts in ubuntu by duplicating the tty files in /etc/event.d However, as I understand it, X usually expects to have vt 7-12 available for use without a tty running on them. When a 2nd user logs in to a graphical session, his X server will  run on vt8 or higher, whichever is the first available.

2. A default install will already have enough vts available for X to run for 5 or 6 additional gui logins. You can login on a second gui instance (but see next point) by selecting "switch user" or by switching to any vt and typing "startx" and the next available display will automatically be used.

3. There is a setting accessible from Main Menu/System/Admin/Login/General where multiple graphical logins for the same user can be enabled/disabled. You don't need to create additional vts to have multiple logins, unless the usual 7 through 12 are not enough for your purposes.

If you just want additional text vts check out the "screen" package. It basically runs multiple text-mode screens on a single vt, each with it's own shell, processes, etc.

---

### Post by jerome1232 on 2008-12-20
Not to pull this more off the virtual terminal topic but:
Another nice utility is dvtm, it is a tilling terminal manager.

---

### Post by LordIshamael on 2008-12-20
hey i tried 'switch user' and it worked fine, setting up a new gui vt (on ctrl-alt-f9, instead of f8 )
only thing is, in that new terminal, all effects were not working - enabled, but still not working - and both desktop switching and the windows had a gnome look
(and yes it did log in to kde, im not THAT much of a n00b :D)
however, it works well enough for my purposes - thanks guys!
question - wouldnt simply copying a tty6 file to tty9 make it also a text terminal? the 'switch user' solution worked without doing that, so i dont think its needed, but just wondering... ill give that also a try right now with tty10 or something
also, when i tried startx on a separate login on tty6, it says fatal error as x is already running on display 0 - doesnt think of switching to display 1 for some reason

but my needs are met by the solutions so far!thanks guys! and yeah ill check out dvtm too!

edit:f8 ) became translated as f8), lol, changed that

---

