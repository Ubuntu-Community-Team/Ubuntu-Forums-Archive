---
title: "pydance is stupid"
date: 2005-07-01
forum: Gaming &amp; Leisure
---

### Post by somuchfortheafter on 2005-07-01
well im at a convention now and everyone is playing stepmania and I could not get it installed so i decided to try pydance, all works well until right before I play the game then the screen closes. so umm i got an error so here it is.

```

thanatosys@darkstar:~$ pydance
open /dev/sequencer: No such file or directory
0 joystick(s) found.
pydance 1.0.1 <pyddr-discuss@icculus.org> - irc.freenode.net/#pyddr
W: Psyco optimizing compiler not found.
Searching for songs in /usr/share/games/pydance/songs
Searching for songs in ~/.pydance/songs
Searching for songs in /usr/local/share/games/pydance/songs
Searching for courses in /usr/share/games/pydance/courses
Searching for courses in ~/.pydance/courses
Searching for courses in /usr/local/share/games/pydance/courses
Traceback (most recent call last):
  File "/usr/games/pydance", line 205, in ?
    if __name__ == '__main__': main()
  File "/usr/games/pydance", line 195, in main
    menudriver.do(screen, (songs, crs, screen))
  File "/usr/share/games/pydance/pydance.zip/menudriver.py", line 262, in do
  File "/usr/share/games/pydance/pydance.zip/menus.py", line 184, in display
  File "/usr/share/games/pydance/pydance.zip/menus.py", line 57, in activate
  File "/usr/share/games/pydance/pydance.zip/menudriver.py", line 155, in wrap_ctr
  File "/usr/share/games/pydance/pydance.zip/gameselect.py", line 205, in __init__
  File "/usr/share/games/pydance/pydance.zip/gameselect.py", line 227, in loop
  File "/usr/share/games/pydance/pydance.zip/courseselect.py", line 236, in __init__
  File "/usr/share/games/pydance/pydance.zip/courseselect.py", line 308, in loop  File "/usr/share/games/pydance/pydance.zip/dance.py", line 192, in play
  File "/usr/share/games/pydance/pydance.zip/player.py", line 227, in __init__
AttributeError: 'module' object has no attribute 'Stats'

```

any ideas????


ok now I have added the error that stepmania produces incase anyone has a solution for that


```

thanatosys@darkstar:~/software/StepMania-3.9-rc3$ ./stepmania
./stepmania: error while loading shared libraries: liblua.so: cannot open shared object file: No such file or directory
thanatosys@darkstar:~/software/StepMania-3.9-rc3$

```
and i have no idea where to get that module and i am executing this in the directory in which i extracted the file.

---

### Post by MaX on 2005-07-02
[QUOTE=somuchfortheafter]well im at a convention now and everyone is playing stepmania and I could not get it installed so i decided to try pydance, all works well until right before I play the game then the screen closes. so umm i got an error so here it is.

```

thanatosys@darkstar:~$ pydance
open /dev/sequencer: No such file or directory
0 joystick(s) found.
pydance 1.0.1 <pyddr-discuss@icculus.org> - irc.freenode.net/#pyddr
W: Psyco optimizing compiler not found.
Searching for songs in /usr/share/games/pydance/songs
Searching for songs in ~/.pydance/songs
Searching for songs in /usr/local/share/games/pydance/songs
Searching for courses in /usr/share/games/pydance/courses
Searching for courses in ~/.pydance/courses
Searching for courses in /usr/local/share/games/pydance/courses
Traceback (most recent call last):
  File "/usr/games/pydance", line 205, in ?
    if __name__ == '__main__': main()
  File "/usr/games/pydance", line 195, in main
    menudriver.do(screen, (songs, crs, screen))
  File "/usr/share/games/pydance/pydance.zip/menudriver.py", line 262, in do
  File "/usr/share/games/pydance/pydance.zip/menus.py", line 184, in display
  File "/usr/share/games/pydance/pydance.zip/menus.py", line 57, in activate
  File "/usr/share/games/pydance/pydance.zip/menudriver.py", line 155, in wrap_ctr
  File "/usr/share/games/pydance/pydance.zip/gameselect.py", line 205, in __init__
  File "/usr/share/games/pydance/pydance.zip/gameselect.py", line 227, in loop
  File "/usr/share/games/pydance/pydance.zip/courseselect.py", line 236, in __init__
  File "/usr/share/games/pydance/pydance.zip/courseselect.py", line 308, in loop  File "/usr/share/games/pydance/pydance.zip/dance.py", line 192, in play
  File "/usr/share/games/pydance/pydance.zip/player.py", line 227, in __init__
AttributeError: 'module' object has no attribute 'Stats'

```

any ideas????


ok now I have added the error that stepmania produces incase anyone has a solution for that


```

thanatosys@darkstar:~/software/StepMania-3.9-rc3$ ./stepmania
./stepmania: error while loading shared libraries: liblua.so: cannot open shared object file: No such file or directory
thanatosys@darkstar:~/software/StepMania-3.9-rc3$

```
and i have no idea where to get that module and i am executing this in the directory in which i extracted the file.[/QUOTE]
 lua is a scripting language... have you tried apt-get install liblua? or just lua?

---

### Post by somuchfortheafter on 2005-07-03
i have installed every package in the ubuntu repositories, universe, and multiverse and still not working so it is not a package issue i think it is the way its coded, any fixes/ideas?

---

### Post by Soulfly on 2005-07-03
[QUOTE=somuchfortheafter]i have installed every package in the ubuntu repositories, universe, and multiverse and still not working so it is not a package issue i think it is the way its coded, any fixes/ideas?[/QUOTE]

How did you do that? 

```

# aptitude install ~g.*

```

Aptitude seems to have scalability problems with this (takes very long time). This might be better:

```

# aptitude -F "%p" search ~g . | sort | uniq | xargs aptitude install

```


Did you have to do lots of --force-xxx ? How much diskspace did it take?

---

### Post by somuchfortheafter on 2005-07-03
i ment the lua ones lol

---

### Post by tommy04 on 2005-07-04
I'd suggest asking for support on installing Stepmania, as it's MUCH better then pyDance.

---

### Post by Soulfly on 2005-07-04
lol

A few tips.

* Check that you have the file:
# dpkg -S liblua.so

* Try to re-run ldconfig
# ldconfig
# pydance

* Try to use auto-apt to get packages for files that is needed but not found:
# aptitude update && aptitude install auto-apt
# auto-apt update
# auto-apt run pydance

---

