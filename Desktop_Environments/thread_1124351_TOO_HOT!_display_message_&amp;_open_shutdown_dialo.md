---
title: "TOO HOT! display message &amp; open shutdown dialog"
date: 2009-04-13
forum: Desktop Environments
---

### Post by Nopposan on 2009-04-13
I'd like to write a little script that I can have my computertemp gnome applet execute when my cpu gets too hot.  The script would display a message via my gnome desktop and nautilus window manager on X11.  The message would say something like "You're computer is too bleeping hot, so unless you're planning to fry an egg then please shut down and wait 15 minutes before you reboot."  Also, the shutdown dialogue would open.  Alternatively, it might be nice to just automate the shutdown, but I don't really want to play around with the sudoer's file too much.

Please help me out if you can.  'Just trying to get the most out of an old processor that's in a laptop I'm giving to a friend.

Hey, actually, there's something very much like this that would automatically log a person out.  It's called with the command gnome-session-save --kill.  I'm going to see if I can find out more about gnome-session commands.

Thanks!

---

### Post by Nopposan on 2009-04-13
O.K.  What I've got is this:
```
gnome-session-save --shutdown-dialog
```

When I check "repeat" under the preference options for the computertemp applet, this works quite well as the shutdown dialogue just keeps showing up again and again.  It would be even better if I could get a dialogue that told the user why the computer was going to shut down though.  Also, it would be great to have an automated process triggered to safely shut down the computer without the user's consent when temperatures above a certain limit are sustained for a specified period of time.  Does anyone know of such an application?

Thanks again.

---

### Post by Nopposan on 2009-04-13
O.K.  Zenity is pretty neat stuff.  Here's what I've got now, and it works well.
```
zenity --warning --text="Your computer is too hot. Please shut down and wait fifteen minutes before rebooting." && gnome-session-save --shutdown-dialog
```

That's actually a bash script; it wasn't possible to use the computertemp's applet to just execute that like bash would.  It works though when I call bash and the script.

However, it would still be nice to trigger an automatic shutdown if temperatures exceed 78 degrees celcius for more than fifteen minutes, for example.  How would I do that?

Thanks again.

---

### Post by schiz on 2009-06-20
Thanks a bunch this helped me with just what I wanted!
Now if I could only make this bakery of a laptop not go crazy hot..

---

### Post by Nopposan on 2009-07-21
Cool.  'Glad I helped someone.  I'm kinda ticked off 'cause the new owner of that very old laptop decided to have her husband install Windows XP on it instead.  I'm thinking that the laptop will probably get fried and/or accumulate malware like her old desktop did.  Oh well.

Let me know how your search for preventing the overheating goes; I'm thinking you could limit your processor speed fairly easily, but I've never done it.  Also, if it's possible to limit processor speed, then it must also be possible to throttle it down when a certain temperature is reached.

Cheers.

---

### Post by haiyun211 on 2009-07-21
As far as the laptop heating up have you tried using a chill pad?

---

### Post by Nopposan on 2009-07-23
'Not a bad idea, Huiyun.  Maybe I'll buy them one for Christmas.

---

### Post by haiyun211 on 2009-07-23
Yeah mine used to overheat all the time and just turn off so I got one and never again

---

