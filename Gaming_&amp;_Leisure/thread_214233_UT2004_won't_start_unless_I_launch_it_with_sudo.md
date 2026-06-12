---
title: "UT2004 won't start unless I launch it with sudo"
date: 2006-07-12
forum: Gaming &amp; Leisure
---

### Post by Sciamano on 2006-07-12
Hello!

I've updated UT2004 installing the latest patch (3369).
Since then, UT won't start anymore! I can only see the splash screen for a hundredth of a second and then nothing.

If I launch it in a terminal, this is what happens:

```
luca@luca-desktop: ut2004
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error

```

But if I launch it using the command "sudo ut2004" IT WORKS! :confused: 

Anyone knows how to solve this? I thought it was a problem of permissions but I chmodded the entire UT2004 directory to 777 and it still won't start.
Any suggestion appreciated. Thanks a lot.
Luca

---

### Post by Rosenrot on 2006-07-12
you're missing a file/command in your .ini file in your system folder

but its odd that it would wokr wiht sudo...

try posting a readout of your ut2004 shell using

sudo gedit /usr/local/ut2004

and copy and paste
/ut2004
i won't be able to help you much (ima newb still : /)and im still trying to figure out my sound issues wiht ut2004
hopefully someone else can help you
good luck

---

### Post by Sciamano on 2006-07-12
Thanks for the hint, but I managed to solve.
It was, as I thought, a problem of permissions, but of the ./ut2004 folder under the home folder.

Found the details here:
[http://ubuntuforums.org/showthread.php?t=211882](http://ubuntuforums.org/showthread.php?t=211882)

Thanks anyway. :)

---

### Post by vem0m on 2006-07-12
so u are using a windows version when there is a native linux version? as the newest UT2004 path on linux is 3355 on windows 3369 so yea what are u running a native copy or what?

---

### Post by Rosenrot on 2006-07-12
the newest patches for linux and windows are 3369...

---

### Post by vem0m on 2006-07-12
hmmmmmm the official site has the newest at 3355 but i did find a linux version of 3369 strange

---

### Post by Rosenrot on 2006-07-12
i guess the official site hasn't been updated lol
or icculus released them elsewhere instead of the official site

---

### Post by Mr_HeNtAi on 2006-07-12
> **vem0m said:**
> hmmmmmm the official site has the newest at 3355 but i did find a linux version of 3369 strange

Yea if you goto another site like filefront they have the newest page listed as 3369. The loki installer is dead on.

---

