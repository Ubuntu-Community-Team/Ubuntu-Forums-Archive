---
title: "Conky Not working with gutsy or just an error"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by fedex1993 on 2007-10-19
Okay well i cant seem to get conky working. i installed from source everything went right but when i tried to start it i got an error 
```

Conky: desktop window (e000cf) is subwindow of root window (58)
Conky: drawing to desktop window
Conky: drawing to single buffer
conky: timed_thread.c:90: timed_thread_create: Assertion `(start_routine != ((void *)0)) && (interval_usecs >= 50000)' failed.
Aborted (core dumped)

```

---

### Post by fedex1993 on 2007-10-19
*bump*

---

### Post by fedex1993 on 2007-10-20
(bumpbump)

---

### Post by phil++ on 2007-10-20
Post your .conkyrc please.  

The hard-coded limit on thread timing for conky  is 0.05 secs.  There were some changes with 1.4.8 to correct a race condition
 in the thread system that the cfs sceduler (the new 2.6.23 scheduler) exposed.

There were some other changes that may be tripping you up.   First, be aware, that 1.4.8 introduces a 
new config item: music_player_interval for setting the mpd and audacious thread update interval.  
If you do not specify music_player_interval, conky will use your update_interval for that value.

Now, if you had been pushing conky really fast with an update_interval < 0.05 secs *and* you use mpd or audacious *and* you 
do not set music_player_interval, you WILL see that assertion.

Increase ALL thread timings above 0.05 secs:

If you use a fast (< 0.05) update_interval and use mpd or audacious vars, set music_player_interval >= 0.05.
If you use execi or texeci vars, always set the timing >= 0.05.

There may yet be a deeper problem, but these are the obvious things that occur to me.

---

### Post by phil++ on 2007-10-20
might also happen if you push the pop3 or imap threads too fast also.

---

### Post by phil++ on 2007-10-21
OK, there is a minor problem with the built-in conky config that will cause that start-up error.

For 1.4.8, you *must* use a real .conkyrc to use conky.

The problem has been patched in conky svn.

---

