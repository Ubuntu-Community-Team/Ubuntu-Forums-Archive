---
title: "FPS/Action games performance in Ubuntu"
date: 2007-03-30
forum: Gaming &amp; Leisure
---

### Post by species8471 on 2007-03-30
I was interested in hearing how different FPS action games
worked In Ubuntu for different people.  The ones I have
tried so far in Ubuntu edgy:

Sin (demo) couldn't get sound to work, screen flickers

Shogo (demo) no sound

Descent3 (demo) no sound

Quake 3  no sound unless the "/proc/asound/card0/pcm0p/oss
/proc/asound/card0/pcm0c/oss" commands are used then the
game becomes unstable and locks up constantly.

Return to Castle Wolfenstein runs well with sound after 
"<game> 0 0 direct" > /proc/asound/card0/pcm0p/oss is
invoked first, did not crash on me like Quake3 (yet) after
playing through 5 or 6 levels

Alien Arena 2007, runs well, after moving "crx" file to another 
folder and renaming "crx.sdl" to "crx" the sound works but is
a little scratchy.

Nexuiz, runs well with sound

PRboom (Doom clone) runs well, sound works.
The other Doom ports available through Synaptic I couldn't
get the sound working

I hope that when Feisty is released that it clears up some of
these sound issues in games

---

### Post by ygarl on 2007-03-30
How odd!

I am using Half-life through WINE with no probs (in fact better than it was on WinXP!)

Also, I use LXDoom without any probs.

Tremolous works fine too...

---

### Post by Perfect Storm on 2007-03-30
Havn't any problems with these game either.

Have you started a sound issue thread in our hardware section to find a solution for your problem?

---

### Post by species8471 on 2007-03-30
> **Artificial Intelligence said:**
> Havn't any problems with these game either.

Have you started a sound issue thread in our hardware section to find a solution for your problem?

I haven't started a thread yet because there are so many existing threads
on these sound problems already.  I have tried all suggestions I found on
these forums except for installing JOSS, which I am doing now, and there
is nothing that has worked for me yet.

---

### Post by Cappy on 2007-03-30
I have to run "aoss <gamename>" (such as "aoss ut2004") to get sound in my games.

---

### Post by species8471 on 2007-03-31
Open Arena, [http://openarena.ws/?about](http://openarena.ws/?about) , a Quake3 port that uses assets 
from IOquake3, works well on my system, the sound works without any
tinkering or "<game> 0 0 direct" > /proc/asound/card0/pcm0p/oss . You
do have to install libopenaloa.   It's not the most polished Quake3 port in
the world but it runs for me with sound and doesn't lock up on me like
the other Q3 builds I tried.  You don't need retail Q3 pak0 to install this.
(I'm not involved with this game, I'm just happy to finally find a version
of Q3 that I can just install and run right off the bat)

---

