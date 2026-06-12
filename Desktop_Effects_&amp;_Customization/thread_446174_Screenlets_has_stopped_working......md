---
title: "Screenlets has stopped working....."
date: 2007-05-16
forum: Desktop Effects &amp; Customization
---

### Post by Izobalax on 2007-05-16
I seem to have developed a problem with screenlets.....

I did have it working fine. Just had the "Now Playing" screenlet only. Then, when I added the weather screenlet. It had a California location, so I changed the ZIP code and entered my UK one. Only, screenlets then froze, popped-up a couple of error messages that wouldn't go away. So I Ctrl+Alt+BackSpace to log back in again. 

Now, if I tell screenlets to add another screenlet, nothing happens. I've reinstalled Screenlets a number of different ways but the problem remains. The system tray icon is there, but I cannot add any screenlets onto my desktop anymore. :(

How do I fix this?

/izo

---

### Post by Izobalax on 2007-05-17
Bumpy goodness! :grin:

/izo

---

### Post by Soybean on 2007-05-17
Ah, I had a similar problem. When it says "zip code," it's actually looking for the code used by Yahoo Weather, which isn't a zip code at all. ;) And if you give it something that doesn't work, it freaks out and breaks everything.

In my case, the problem was that a screenletsd process was still running, but wasn't doing whatever it's supposed to do. Since the process is still there but not responding properly, the other screenlets programs refuse to start a new screenletsd (and can't interact with the existing one).

It was tricky to track down, too, because a standard "ps" just shows "python" and doesn't mention screenletsd at all.

The following command found the process for me. I killed it, and then everything went back to working as expected. :)
```
ps axo "%p,%a" | grep screenletsd
```

---

### Post by Izobalax on 2007-05-17
Wow! Thanks for that! One last question.... how did you kill it? The command gave me this in the terminal:

```
izo@izo-desktop:~$ ps axo "%p,%a" | grep screenletsd
11752,python /usr/local/share/screenlets/screenletsd.py start
13718,grep screenletsd
```

/izo

---

### Post by Soybean on 2007-05-17
Yeah, that 11752 line is the problem -- same thing I had.

I believe it's
```
kill -s 9 11752
```
to get rid of it. Then run the ps command again to see if it worked... if not (if the line beginning with 11752 still shows up), then do
```
sudo kill -s 9 11752
```

---

### Post by Izobalax on 2007-05-17
Got it! Soybean, you are an ***angel***.

/izo

---

