---
title: "Savage 2"
date: 2009-06-15
forum: Gaming &amp; Leisure
---

### Post by tommah04 on 2009-06-15
hey all,

trying to install savage 2, everything seemed to be going well

but when I tried launching it, it started then closed right away.... I decided to run it in the terminal and I got this...

/home/tom/.Games/Savage2/savage2.bin: error while loading shared libraries: libk2.so: cannot open shared object file: No such file or directory

I think its a dependency issue, but when I look in synaptic for libk2 there wasn't anything.... so what should I do?

---

### Post by Sigurd Suhm on 2009-06-15
Didn't check the error message when I installed. But I just ran the dedicated server program. Let it run for a while and eventually it will run an update. After that my game started without any problems.

As I said your error message could be due to something else but I know that many have had the same problem that I had.

EDIT: You might have to leave the dedicated server running for quite some time by the way. Mine updated after like 10 minutes but some people say they had to leave it running for over an hour.

---

### Post by donkyhotay on 2009-06-15
Known issue, you need to update savage to it's most recent version. Unfortunately the only way to do that is in-game. If you just run the dedicated server from the CLI for about 10 minutes or so it will automatically download/install the update and resolve the issue.

---

### Post by SerenityKill3r on 2009-06-15
I had a similar problem and I just ran savage2_update.bin at it worked straight away!

---

### Post by tommah04 on 2009-06-15
hey all

I tried all the suggestions and I got this

[email]tom@tom-desktop:~/.Games[/email]/Savage2$ ./dedicated_server.sh
./savage2.bin: error while loading shared libraries: libk2.so: cannot open shared object file: No such file or directory
./savage2.bin: error while loading shared libraries: libk2.so: cannot open shared object file: No such file or directory
./savage2.bin: error while loading shared libraries: libk2.so: cannot open shared object file: No such file or directory
./savage2.bin: error while loading shared libraries: libk2.so: cannot open shared object file: No such file or directory
./savage2.bin: error while loading shared libraries: libk2.so: cannot open shared object file: No such file or directory
^C
[email]tom@tom-desktop:~/.Games[/email]/Savage2$ 




and then the update.bin...
[email]tom@tom-desktop:~/.Games[/email]/Savage2$ ./savage2_update.bin
./savage2.bin: error while loading shared libraries: libk2.so: cannot open shared object file: No such file or directory


I'm really confused about this libk2.so
and I can't update it cause it never actually starts... I must be missing a dependency I'm just clueless as to what it is

---

### Post by v3xtra on 2009-06-16
```
./savage2_update.bin --update-runpath
```

do anything better?  Have you tried doing a fresh install of the program as well, as something may not have been added that should have been.

---

### Post by SerenityKill3r on 2009-06-16
> **v3xtra said:**
> ```
./savage2_update.bin --update-runpath
```

do anything better?  Have you tried doing a fresh install of the program as well, as something may not have been added that should have been.

Yeah, reinstall the game and try it.

Running the update worked for me on a fresh install.

---

### Post by meborc on 2009-06-16
if you install a game using sudo, then it is not advised to run it straight away from the installer START button... this is due to then creating all the game conf folders with sudo and the permissions get messed up

this is reported to happen for several games like ET, WoP etc... may be similar case here?

just close the installer after installation and then start the game from menu/terminal

then it will complain about something else, and you need to update it like said before... :) the installer is old, a lot of updates have been made, but no single linux install file :(

---

### Post by tommah04 on 2009-06-16
hey all,

before everyone started giving me suggestions i decided to run the update bin again, and left it running..... its going on at least 6 hours.... that's not normal is it?

well if this doesn't work i'll try all your ideas

---

### Post by tommah04 on 2009-06-16
> **v3xtra said:**
> ```
./savage2_update.bin --update-runpath
```do anything better?  Have you tried doing a fresh install of the program as well, as something may not have been added that should have been.


hey, I tried this and it got this message while updating...

"Error 1 updating runpath: game/libgame_shared.so"

:-\

Edit:

although now that I think about it it might be because the other updater is running (for like 6 hours) in the background...

---

### Post by Sealbhach on 2009-06-16
When I ran update_server I left it running for about an hour, then just closed the terminal. It worked after that, I'm not sure how long exactly it should take but six hours should be more than enough.

.

---

### Post by tommah04 on 2009-06-16
I re-installed it... didn't work out of box but gave me a different error code, I guess that's improvement... 

ran the updater and its going on about 2 hours... thinking about quiting it....

---

### Post by Nussi on 2009-11-06
The libraries in question are all there. However, it seems that there are linking problems. I solved them like this:
```
me@/game/dir$ LD_LIBRARY_PATH='/game/dir':'/game/dir/libs' '/game/dir/savage2.bin'
```

---

### Post by Wulfrunner on 2010-06-03
> ./savage2_update.bin --update-runpath

Worked for me!

---

### Post by uazure on 2012-03-03
I used fresh Ubuntu 12.04 beta and downloaded fresh savage2 installer for x86_64. I faced the same problem. Problem was caused by apparmor.

Here is how I resolved it:

```

cd ~/Savage2
sudo aa-genprof ./savage2.bin
```
Then in another terminal launch savage2.bin (as user, not as root)

In first terminal (where you have aa-genprof running) press (S) and allow access to requested features. Then save the profile.

---

