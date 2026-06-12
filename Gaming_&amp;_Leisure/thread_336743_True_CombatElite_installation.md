---
title: "True Combat:Elite installation"
date: 2007-01-12
forum: Gaming &amp; Leisure
---

### Post by j.miller565 on 2007-01-12
I'm trying to install the TC:E mod for Enemy Territory but for some reason I can't. here is what happens in the terminal:

> simon@ubuntu:~$ sh true.combat.elite_0.49-english.run
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english.................................................................................................................
Please visit [http://www.liflg.org](http://www.liflg.org)
Searching Return to Castle Wolfenstein: Enemy Territory....
Return to Castle Wolfenstein: Enemy Territory found in /usr/local/games/enemy-territory
Installing in /usr/local/games/enemy-territory
-e Permission denied!!!
You do not have write permission                        in /usr/local/games/enemy-territory
Maybe YOU have to be root?
simon@ubuntu:~$ 

So what can I do to install it?

---

### Post by aidanr on 2007-01-12
```
sudo ./true.combat.elite_0.49-english.run
```
and then type your password

---

### Post by j.miller565 on 2007-01-12
Thanks man it's working now

---

### Post by H3R3T1K on 2011-07-04
Installation of Enemey Territory worked fine for me, but after it shows me the Readme an error occurs:

```
Initial test release. ver .230c
This release is not compatible with the win32 builds
Please enter the installation path [/usr/local/games/enemy-territory]

No write permission to /usr/local/games
```

Is that because my home folder is encrypted? What do I gotta do to make it install properly?

Ok I figured out I forgot "sudo".

Now it tells me:

```
Please enter the path in which to create the symbolic links [/home/arno/Enemy Territory/symbolic links/] /home/arno/symbolic links/
No write permission to /home/arno/symbolic links/
```

I know it lucks silly. I have no idea what symbolic links are. Whats wrong anyways? Is it still the fact that my home folder is encrypted?

---

### Post by Perfect Storm on 2011-07-04
Necromancy is a forbidden art on Ubuntuforums.


Thread closed.

---

