---
title: "Alien arena single player - no enemies?"
date: 2012-03-23
forum: Gaming &amp; Leisure
---

### Post by kurja on 2012-03-23
Hi,

I'm looking for a fps game with a single player mode, and installed alien arena. Ok, there is a single player mode, but it looks like a deathmatch game with no enemies. I'm just running around collecting weapons without seeing anything to use them on, this isn't what it's supposed to be like?

---

### Post by Dlambert on 2012-03-24
Set up bots, somewhere in one of the screens

---

### Post by Irritant on 2012-03-25
It looks like Unbuntu has a problem with their installation of Alien Arena.  Some people in our community are looking into it.

---

### Post by baby_panda on 2012-03-25
> **Dlambert said:**
> Set up bots, somewhere in one of the screens
Hi, how can we set up bots? I checked the menus, but couldn't see such an option.

---

### Post by kurja on 2012-03-25
> **baby_panda said:**
> Hi, how can we set up bots? I checked the menus, but couldn't see such an option.

That doesn't seem to work, you have to add them via console. Hit tilde (the ~ sign) to open the console, then use command ```
sv addbot
```

---

### Post by kurja on 2012-03-25
> **Irritant said:**
> It looks like Unbuntu has a problem with their installation of Alien Arena.  Some people in our community are looking into it.

Yes, like many others I had to use the chown- command on the game folders to get it started.

edit - typos..

---

### Post by kurja on 2012-03-25
> **Irritant said:**
> It looks like Unbuntu has a problem with their installation of Alien Arena.  Some people in our community are looking into it.

also see this: [http://ubuntuforums.org/showthread.php?t=1945916](http://ubuntuforums.org/showthread.php?t=1945916)

---

### Post by Irritant on 2012-03-26
> **baby_panda said:**
> Hi, how can we set up bots? I checked the menus, but couldn't see such an option.

In the "Host server" menu, at the bottom is "Deathmatch and Bot Flags".

You may be able to add the bots there via the menu, but I can't be sure it works given the problems with the Ubuntu/Debian installation of the game.

---

### Post by Irritant on 2012-03-26
Also, since it appears that the Debian/Ubuntu installer is not correctly installing the game, I'd recommend downloading the game from [http://red.planetarena.org](http://red.planetarena.org) and installing it manually.

---

### Post by baby_panda on 2012-03-26
How can we load and save games? (These menu options are not present.) Also I cannot start the server. It prints like this:

ln: creating symbolic link `/home/user/.config/alien-arena/data1': File exists
Found server config /home/user/.config/alien-arena/arena/server.cfg...

Stale server.cfg.pid file, erasing...
Attempting to Restart Alien Arena
/usr/lib/games/alien-arena/launch-server: 80: /usr/lib/games/alian-arena/crx-ded: not found

---

### Post by kurja on 2012-03-26
> **Irritant said:**
> In the "Host server" menu, at the bottom is "Deathmatch and Bot Flags".

You may be able to add the bots there via the menu, but I can't be sure it works given the problems with the Ubuntu/Debian installation of the game.

Did not work for me "out of the box", but there is a fix: [http://corent.proboards.com/index.cgi?action=display&board=rookie&thread=6667&page=2](http://corent.proboards.com/index.cgi?action=display&board=rookie&thread=6667&page=2)

---

### Post by Valezan on 2012-05-16
Hi,
I have found a solution here ([http://corent.proboards.com/index.cgi?board=rookie&action=display&thread=6667&page=2](http://corent.proboards.com/index.cgi?board=rookie&action=display&thread=6667&page=2)).
Simply make sure the “/home/username/.config/alien-arena” exists and then copy both the “botinfo” and the “arena” directories from “/usr/share/games/alien-arena” into it.
 Regards

---

### Post by kurja on 2012-05-19
ummm didn't I give that same link in the previous post? btw that was me at the forum you (we) linked to =)

I guess I should have remembered to mark this as solved!

---

### Post by Valezan on 2012-05-20
Erfff, really sorry Kurja, I found the solution and this thread (and many other) while I was looking for the solution and I didn't saw that you already gave that same link in the previous post. Next time, promise, I will read more carefully! Congratulations for your solution and thank you.

---

### Post by rcain on 2012-07-28
i had same prob: ubunto 12.04, using software manager autoinstaller to open download - installed ok, but, attempting to run app - nothing.

suggestion above to copy files - not applicable. it is a permissions thing - bug in autoinstall script. has someonw raised a bug already?


solution that worked for me: try: 

just bring up ubuntu term session, then:

sudo /usr/games/alien-arena

 - worked fine for me after that. good performance/response. game play a bit manic for my liking on the server i joined - but will suite many i'm sure.

best of luck

---

