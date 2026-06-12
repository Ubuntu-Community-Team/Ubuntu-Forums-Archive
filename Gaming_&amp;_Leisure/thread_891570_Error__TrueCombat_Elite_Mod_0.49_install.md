---
title: "Error | TrueCombat: Elite Mod 0.49 install"
date: 2008-08-16
forum: Gaming &amp; Leisure
---

### Post by taamir on 2008-08-16
Hi everyone..
I am new to Ubuntu and Enjoying it very much.
Recently I installed Wolfenstein: Enemy Territory and now i want to install TrueCombat: Elite Mod 0.49.
I used the guid on [http://tce.helpz0r.net/instlin1.html](http://tce.helpz0r.net/instlin1.html)
but i get an error :
[B]
gilad@Gilad-Desktop:~$ sudo sh true.combat.elite_0.49b-english-4.run
true.combat.elite_0.49b-english-4.run: 1: Syntax error: newline unexpected
gilad@Gilad-Desktop:~$ 
[/B]

Please help (try to give detail instructions couz Im new..)

THX:(

---

### Post by cristo-father on 2008-08-16
What is your version of Ubuntu? Architecture(32bit or 64bit)?

---

### Post by taamir on 2008-08-16
hardy 8.04 32bit

more info-
I made the file "true.combat.elite_0.49b-english-4.run" executable and double clicked it.
it verified and uncompressed, and then when it started search for W-ET the terminal EXITED I didn't even got to read the output!!

AGRRRRRR SO Annoying !!!!!

---

### Post by taamir on 2008-08-16
I managed to install the game but when i try to run it 
using command 

et +set fs_game tcetest

it outputs:

/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/gilad/.etwolf/tcetest/ui.mp.i386.so)... 
Sys_LoadDll(/home/gilad/.etwolf/tcetest/ui.mp.i386.so) failed:
"/home/gilad/.etwolf/tcetest/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so)... 
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so) failed:
"libstdc++.so.5: cannot open shared object file: No such file or directory"
Sys_LoadDll(ui) failed dlopen() completely!
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: VM_Create on UI failed

I don't know but maybe it has to do something with a change i made for the sound to work properly on W:ET (from the install instructions:mad:)

HELP PLEASE:confused:

---

### Post by Perfect Storm on 2008-08-16
> "libstdc++.so.5: cannot open shared object file: No such file or directory"

Install libstdc++5

---

### Post by taamir on 2008-08-16
I installed libc++5 and updated punkbuster but now i have no sound and I cant pplay online or download maps..

---

### Post by Perfect Storm on 2008-08-16
Are you running the game with sudo permission? (launched it from the installer window).

---

### Post by taamir on 2008-08-16
Yeh it works with sudo only NO SOUND problem now

---

### Post by Perfect Storm on 2008-08-16
okay. As you're new to Linux/Ubuntu, you should know that running stuff with sudo is highly _not_ recommendable. It's a security risk, especially with games and apps that connect via the net.

I suggest that you uninstall the game and install it in your home directory - or install the game with sudo **but don't launch it while having sudo power**.
Then we can take a look at your sound problem afterwards.

---

### Post by taamir on 2008-08-16
Realy.. I just had it going..
Will it work if I MOVE the folder as is ?

---

### Post by Perfect Storm on 2008-08-16
No, I'm afraid not. It will break.

---

### Post by taamir on 2008-08-17
So how do I make uninstall?

---

### Post by Perfect Storm on 2008-08-17
Check if there's a uninstaller script in its folder. If not you have to manually delete it.

---

### Post by taamir on 2008-08-18
Is the True Combat and Enemy Territory installed in the same folder (.etwolf)?
and can I just change the permission -> owner: root
to User ?

---

### Post by Perfect Storm on 2008-08-18
As a rule, it's not a good idea to messsing around the permission system of the system files. You can mess things up badly.

> Is the True Combat and Enemy Territory installed in the same folder (.etwolf)?
I believe so, I don't play those games.

---

