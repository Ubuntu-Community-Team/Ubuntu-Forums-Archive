---
title: "gnome is slow with separate X-screens"
date: 2007-12-23
forum: Desktop Environments
---

### Post by as0l0 on 2007-12-23
Hi,

  I have a LCD monitor and a crt HDTV.  I have each device set to show a separate X-screen and it's working fine..except...

  Gnome is very slow with this config.  Drop down menus, autocompletes, things like that, take 1-2 seconds rather than being "instant".  Applications are generally fast, as fast as normal.

  If I turn off my second x-screen or use twinview, then i don't have the problem.  I'm not sure how to start diagnosing this problem.

---

### Post by as0l0 on 2007-12-26
any thoughts at all on how to diagnose this issue?

---

### Post by as0l0 on 2007-12-27
any thoughts at all from anyone?

this is pretty much a deal breaker for me and it will be a shame to go back to vista because of a silly thing like this :(

---

### Post by moktor on 2007-12-28
Howdy,

I just got a new LCD and had the same problem setting up dual monitors. I was able to get things functioning from the advice in this thread. While it isn't optimal, it does function.:

[http://ubuntuforums.org/showthread.php?t=536045](http://ubuntuforums.org/showthread.php?t=536045)

Specifically gtaluvit's recommendation: [http://ubuntuforums.org/showpost.php?p=3426504&postcount=14](http://ubuntuforums.org/showpost.php?p=3426504&postcount=14)

> **gtaluvit said:**
> I seem to have the same problem but also a temporary workaround.  With today's updates to Gutsy, I wanted to see if I could finally use the Appearance tab to do compiz instead of my manual method.  Basically, I have the problem of wanting to run compiz on one monitor but not the other as it's not supported.  Here's basically what I see:

If I run compiz using the Appearance preference bar, compiz tries to load on both monitors.  I seem to have wobbly windows and such on my main, not on my secondary.  I don't have any window decoration at all on my secondary.  Also, on my main screen, menus are very slow.

If I run compiz delayed 5 seconds as a session startup (and have it only replace my main screen), then I have compiz running on my main, and metacity on the secondary.  Both seem to work fine without any menu issues.

So, I would suggest the following script to add to your session:

```

#!/bin/bash
sleep 5
compiz --replace --only-current-screen &
gtk-window-decorator --replace &

```

---

### Post by as0l0 on 2007-12-30
thanks for helping mate.  in the end i just gave up and went back to Vista.  There are just too many things that are just too hard to achieve.  

I'm happy with my choice, but disappointed in Ubuntu :(

---

