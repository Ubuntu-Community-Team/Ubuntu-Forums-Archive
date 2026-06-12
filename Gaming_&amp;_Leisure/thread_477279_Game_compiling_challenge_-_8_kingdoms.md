---
title: "Game compiling challenge - 8 kingdoms"
date: 2007-06-18
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2007-06-18
this game doesn't have a good graphics but I'm keep coming back to it, it seems interesting.
this game only have a source code and a dependencies hell I didn't ever manage to compile it.
therefor I will try it again (with my clean feisty installation) after you do it and tell me how.

this game should run on Linux.

here are the links :

download : [http://sourceforge.net/projects/kralovstvi/](http://sourceforge.net/projects/kralovstvi/)
homepage : [http://kralovstvi.sourceforge.net/](http://kralovstvi.sourceforge.net/)
dependencies : [http://sourceforge.net/forum/forum.php?thread_id=1602818&forum_id=329816](http://sourceforge.net/forum/forum.php?thread_id=1602818&forum_id=329816)

what I'm asking for you is to give me an exact CLI commands so I can compile it and install all dependencies as well.

I remind you that I use Ubuntu Feisty.

Thanks.

and if you find a .deb or a .package or anything else for easier installation let me know

---

### Post by christhemonkey on 2007-06-18
I get stuck at trying to find tcl im afraid.

Have tcl8.4-dev installed... hmm willl keep trying for you!

---

### Post by MaximB on 2007-06-18
> **christhemonkey said:**
> I get stuck at trying to find tcl im afraid.

Have tcl8.4-dev installed... hmm willl keep trying for you!

any news yet ?

---

### Post by christhemonkey on 2007-06-18
Not yet....

---

### Post by MaximB on 2007-06-19
so who else if up for the challenge ?

---

### Post by NickeM on 2007-06-19
I got past the tcl requirement:
sudo ln -s  /usr/lib/libtcl8.4.so /usr/lib/libtcl.so 
export PATH=$PATH:/usr/include/tcl8.4/
and changing
vi ./8Kingdoms-1.0.0/common/TCL/tcl_script.h
row 11 from
#include <tcl.h> to
#include "/usr/include/tcl8.4/tcl.h"

./configure && make
results in:
ai/PathFind/pathfindtransciever.cpp:25: fel: "PATHFIND_MSG_HANDLER" not declared in scope

---

### Post by NickeM on 2007-06-19
I managed to get it to build, they have made global function definitions below the class definitions
so the g++ compiler could not find the function in the current scope, i had to move all global functions to the top of the file, within the namespace ofcource, in the following files:

pathfindertranceiever.cpp
strategytranceiver.cpp
diplomacytranceiver.cpp
mapanalyzertranceiver.cpp.

I have generated a deb file using checkinstall and uploaded it th rapidshare.de. I give no guarantees that it works though ;-) (no dependencies set in the deb file)

[ Download 8kingdoms_1.0.0-1_i386.deb here]("http://rapidshare.com/files/38161786/8kingdoms_1.0.0-1_i386.deb.html")

---

### Post by Vtaxy on 2007-06-19
Hi,

I have just googled this forum... 

NickeM: You are right, there was a problem with the namespaces. We fixed it few days ago, but it is still only in the CVS repository and not in the released source code. Would you mind if I add the package you have created to the download section at SF.net ? 
I guess many people will appreciate the package...

Regards,
Vta

---

### Post by WW on 2007-06-19
I don't think putting the checkinstall-generated deb file on a public web page is a good idea.  If I understand how checkinstall works (and from what NickeM said), it doesn't check for dependencies.  This means people will download and install the deb, but then when they try to run it, there is a chance it won't work (because they don't have tcl, or they don't have some other library).  Then the developers will start getting questions about why it doesn't work...

If I knew more about creating proper deb files, I'd give it a shot, but the closest I've come to that is using **epm** to package a simple python program. (See [this thread]("http://ubuntuforums.org/showthread.php?t=406069").)

---

### Post by NickeM on 2007-06-19
I have made a new proper debian package with dependencies setup, plus a more verbose description of the game.

@Vtaxy, feel free to use the deb file as you wish :)

[Klick here, 8kingdoms_1.0.0-2_i386.deb]("http://rapidshare.com/files/38196132/8kingdoms_1.0.0-2_i386.deb.html")

---

### Post by MaximB on 2007-06-19
Thank you very much NickeM !
I understand now that the problem was in the source code and not with my system (got stuck in the tcl part too before).

now for the developers :
Vta - what are your plans next regarding this game ? are you still working on it ?

---

### Post by Vtaxy on 2007-06-20
Ye, we want to continue working on it..

Firstly we plan to fix the bugs and improve the GUI engine, which probably causes majority of them. Then we would like to allow scripts in the maps, improve map editor and also there is a plan to separate the server part from the client part. And if we manage to create some models and textures, we could add some better looking units or buildings...

Btw. the debian package is already in the download section. Thanks for it.

---

### Post by MaximB on 2007-06-20
I like your game very much, but you are true to say "it is very buggy".
sometimes I can't load maps, sometimes I can't save games, sometimes the computer not taking his turn, and that is for the first 20 minutes of "playing" the game.

I see a great potential in this game, but you really need to "kill some bugs" ;)

---

### Post by Vtaxy on 2007-07-22
We have made progress - we have just released a new version of 8 Kingdoms.
You can find it in the download section:
[http://sourceforge.net/project/showfiles.php?group_id=95208](http://sourceforge.net/project/showfiles.php?group_id=95208)

---

