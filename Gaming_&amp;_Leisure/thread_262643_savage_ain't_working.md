---
title: "savage ain't working"
date: 2006-09-22
forum: Gaming &amp; Leisure
---

### Post by crunchystrike on 2006-09-22
hello, ok, when i went to play Savage, it started a black screen, and then sent me back to the place where i was when i started it.

ok, i decided to launch it from the console


admin@admin-desktop:~$ cd /home
admin@admin-desktop:/home$ cd admin
admin@admin-desktop:~$ cd games
admin@admin-desktop:~/games$ cd Savage
admin@admin-desktop:~/games/Savage$ ./savage
System_Init()
Unknown command: '/home/admin/games/Savage'
admin@admin-desktop:~/games/Savage$
admin@admin-desktop:~/games/Savage$

thats what i get, i don't get what the problem is, can somone help me?

---

### Post by huwshimi on 2006-09-22
It sounds like you might not have 3D enable properly. Have a look through these forums for a tutorial.

Cheers.

---

### Post by slimdog360 on 2006-09-22
better then mine, nothing even happens when I try to run it.

---

### Post by tht00 on 2006-09-23
> **crunchystrike said:**
> hello, ok, when i went to play Savage, it started a black screen, and then sent me back to the place where i was when i started it.

ok, i decided to launch it from the console


admin@admin-desktop:~$ cd /home
admin@admin-desktop:/home$ cd admin
admin@admin-desktop:~$ cd games
admin@admin-desktop:~/games$ cd Savage
admin@admin-desktop:~/games/Savage$ ./savage
System_Init()
Unknown command: '/home/admin/games/Savage'
admin@admin-desktop:~/games/Savage$
admin@admin-desktop:~/games/Savage$

thats what i get, i don't get what the problem is, can somone help me?

2 questions:
What tutorial did you use to install this?  Really, you shouldn't be using the ./savage command to start the game.

Do you have your graphics card driver setup correctly? (nvidia/ati)

---

### Post by Casey on 2006-09-24
admin@admin-desktop:~/games/Savage$ ./savage
System_Init()
Unknown command: '/home/admin/games/Savage'
admin@admin-desktop:~/games/Savage$

Did you, by chance, move the game directory (where is Savage)

If it's in /home/admin/games/Savage then it really needs to be executing /home/admin/games/Savage/savage

You can use nano to fix this.

nano -w /home/admin/savage

Then add /savage after /Savage

ctrl-w to write, ctrl-x to exit.

Hope this helps.
-- Casey

---

### Post by Xanni on 2006-09-30
I have the exact same problem.  xi0nblue, 3D is working fine.  

tht00, I'm using the SEP Package Primary Download (Linux) from [http://www.s2games.com/savage/downloads.php](http://www.s2games.com/savage/downloads.php)
"http://www.happypuppy.com < 2.00e Linux Retail + SEP3T"
[http://www.happypuppy.com/s2games/Savage_with_sep3t.run](http://www.happypuppy.com/s2games/Savage_with_sep3t.run)

This installs the following softlinks:
savage -> /usr/local/games/Savage/Savage
savage-graveyard -> /usr/local/games/Savage/Graveyard
savage-server -> /usr/local/games/Savage/Dedicated_server

These are shell scripts.

Casey, you're on the wrong track - the error message is emitted by silverback.bin after being invoked by the script as follows:

LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin `pwd`

The exact output from silverback.bin is:

System_Init()
Unknown command: '/usr/local/games/Savage'

Further assistance welcome.

---

### Post by poupouille on 2006-10-06
Hi,

Here is how I solved the entire problem.

First, I edited the "Savage" script inside the installation directory, replacing:

LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin `pwd`

by:

LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin

This removed the error message, but proved to be unsufficient. I found the origin of the true problem looking at the "~/.savage/debug.log" file:

> 
Vid_Init():
 * Adding mode 1: 1440x900x32
attempting to set the following video mode: 0 x 0 x 0 (32 bit depth buffer)
attempting to set the following video mode: 0 x 0 x 0 (24 bit depth buffer)
Screen Res: 0 x 0
Screen BPP: 32
Depth Buffer Size: 24


I quickly realized that my "/etc/X11/xorg.conf" was only allowing one video mode.

To fix this, just look inside for the "Display" subsections of this file (as root), and add the following to the "Modes" lines:

"1024x768" "800x600" "640x480"

Then restart the X server, and run Savage.

This worked just fine for me.

Have fun!

---

