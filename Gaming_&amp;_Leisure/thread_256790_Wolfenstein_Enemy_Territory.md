---
title: "Wolfenstein: Enemy Territory"
date: 2006-09-13
forum: Gaming &amp; Leisure
---

### Post by PPAAUULL on 2006-09-13
I have installed Wolfenstein: Enemy Territory and have been trying to get it working now that I finaly can go into games I find another problem that I have no ides how to fix. When I go into a game and go to choose my team the program just closes, no popup or error message it just closes. anyone have the same problem? Any one know how to fix it?

Thanks for the help.

---

### Post by B0rsuk on 2006-09-13
Run it from console (by typing **et** ). Then once it crashes, check the console for messages.

---

### Post by PPAAUULL on 2006-09-13
I am running it from console but when it closes so does the console.

---

### Post by haxer on 2006-09-13
Try start it from menu "program" then other or others at the top of the line im from sweden and not that good at english but just try it :)

---

### Post by PPAAUULL on 2006-09-13
I still get the same problem

---

### Post by theturtlemoves on 2006-09-13
To confirm: When you open a terminal(such as gnome terminal from Accessories) and type et, after you join a team the terminal closes as well as the game?

---

### Post by PPAAUULL on 2006-09-13
Ya that is the exact problem.

---

### Post by PPAAUULL on 2006-09-13
Tryed it again not as root and I got this output:

----------------------
11413 files in pk3 files
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: failed to remove outdated '/home/paulvolk/.etwolf/etmain/default.cfg' file:
"Permission denied"

Shutdown tty console
paulvolk@paulvolk-desktop:~$

---

### Post by fatsheep on 2006-09-13
> **PPAAUULL said:**
> Tryed it again not as root and I got this output:

----------------------
11413 files in pk3 files
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: failed to remove outdated '/home/paulvolk/.etwolf/etmain/default.cfg' file:
"Permission denied"

Shutdown tty console
paulvolk@paulvolk-desktop:~$

Try this command:

> sudo chown user:user /home/paulvolk/.etwolf/etmain/

Make sure to replace "user:user" with your actual username.  For example, mine would be "fatsheep:fatsheep".

---

### Post by haxer on 2006-09-13
hmm.. remove it then go to 
[http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

---

### Post by PPAAUULL on 2006-09-13
Remove what and how?

---

### Post by PPAAUULL on 2006-09-13
I have tried something else and have captured what it says when it shuts down in a game when I am choosing teams. It says:

et.x86: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwL ock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Received signal 6, exiting...
Shutdown tty console
paulvolk@paulvolk-desktop:~$


I hope that helps a bit.

---

### Post by haxer on 2006-09-13
Hmm.. remove :P hehe.. dont really know but if you try to go "program" then the first option remove or add i dont know the exact english word then a program starts then you can remove it then go to the selected website i posted before that would do the trick :)

---

### Post by PPAAUULL on 2006-09-14
Can anyone tell me how to fix the signal 6 error?

---

### Post by halfvolle melk on 2006-09-14
Hey Paul,

Here's just a suggestion as I have no clue how to fix the error. But maybe removing (I think that may be what haxer meant) and reinstalling the game will fix it.

Do you still have the install files? If not, PM me and I'll host them for you.

If you didn't install it as root just remove ~/enemy-territory and maybe ~/.etwolf. If you installed as root, run
```
locate enemy-territory
```
and
```
sudo rm -r /usr/games/enemy-territory
```
or whereever it went.

Reinstall the game as user. The only thing I see against this that it can't be run system wide / by other users.

[http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

And then join ubu-e :)

---

### Post by PPAAUULL on 2006-09-26
> **halfvolle melk said:**
> Reinstall the game as user. The only thing I see against this that it can't be run system wide / by other users.

[http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

And then join ubu-e :)

Just wondering but when I go to the site I notice that the instructions have you install the game as ```
sudo
``` and not user. How would I install the game as the user?

Thanks.

---

### Post by sigge on 2006-10-02
As far as I see it, there is no reason to not install using sudo.

But it is a huge securityrisk, and also it can break games when you run them as root. So you might even need to reinstall the game, since you allready ran the game as root. Not shure about this though....:-k

Good luck though.

---

### Post by halfvolle melk on 2006-10-02
PAUL, I missed your update. Awnser: remove 'sudo', so just do './et-linux-2.60.x86.run' etc. Just press enter when asked for root passwd.

> **sigge said:**
> As far as I see it, there is no reason to not install using sudo.

But it is a huge securityrisk, and also it can break games when you run them as root. So you might even need to reinstall the game, since you allready ran the game as root. Not shure about this though....:-k

Good luck though.
Don't think there's a security risk because you invoke the game as user. A reason for me is that I've got a 10GB root partition and a 210 GB home partition. ET + TCE is about 750MB. Nexuiz is about 200MB and so on. They run nicely from /home :)

---

### Post by VexVishnu on 2008-06-28
I don't know if anyone will read this seeing as how this is a really old topic, but I did all of that and it still didn't work... Can you think of anything else it might be?

---

### Post by PmDematagoda on 2008-06-29
> **VexVishnu said:**
> I don't know if anyone will read this seeing as how this is a really old topic, but I did all of that and it still didn't work... Can you think of anything else it might be?

Please create a new thread instead of resurrecting old threads, if you want to include this thread then you should link to it. 

This thread is closed.

---

