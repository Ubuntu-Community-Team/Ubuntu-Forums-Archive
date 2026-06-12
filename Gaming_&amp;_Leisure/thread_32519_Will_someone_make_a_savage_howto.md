---
title: "Will someone make a savage howto?"
date: 2005-05-08
forum: Gaming &amp; Leisure
---

### Post by DarkGreen16 on 2005-05-08
I'm getting frustrated with the game savage...I downloaded the cd installed via

sudo sh INSTALL.linux

it asks me where want to install I change the defaults to /usr/local/games/

and 

/usr/local/bin

it installs just fine and when I run savage it gives me an error in the updater and says it has to bail out...so ok I do some searching and find a thread about savage on this forum. One other person complains about having problems starting but says he fixes it by running ./savage.bin I try to run ,/savage.bin and it gives me an error saying I dont have blah then bleh then blah then bleh...so i make a soft link for every file it complains about not having. Then I run it with no errors and it still quits saying it "can't get local patch index". Then I read on the internet on forums.s2games.com that I should just run ./silverback.bin because the updater no longer works for linux. So I do that and now i get this error

./silverback.bin: /usr/lib/libGL.so.1: no version information available (required by ./silverback.bin)
System_Init()
Game error during initialization:

Couldn't open scripts.log

this is really pissing me off...considering every other commercial distribution of a linux game I have tried works right from the install. 

Did something go wrong with the install or is s2 just bad at making linux ports?

Any idea how to fix this or wanna just write a how to from square 1  :-P ?

_________________________________________________________________________________

update: I now only have 1 error but haven't install SEP. It is my understanding that SEP might cause the version error.

I get this now

Game error during initialization:

Couldn't open scripts.log

---

### Post by DarkGreen16 on 2005-05-08
another update....

I found that this error happens in more than just 1 program...and i saw 1 website that said to fix it u need to install the official nvidia drivers...not ones already packed. So this may be an option. Although, i have no idea how to install the ones off the website on ubuntu.

---

### Post by skoal on 2005-05-08
I'll see if I can't help you out brother.  This is mostly from memory, but here it goes:

1. After installing Savage to /usr/local/games, the installer asks you to "Start" or "Exit".  Exit for now.  You will *not* use the builtin Savage auto updater to make your game current.

2. Download the 2.00b and 2.00c patches for linux.  Here's one such place:
[http://www.3dgamers.com/games/savage/downloads/](http://www.3dgamers.com/games/savage/downloads/)

3. Change to the root of /usr/local/games/Savage folder and untar/gunzip 'savage_patch_200b.tar.gz' first, then 'savage_patch_200b_to_200c.tar.gz'.

tar xvzf savage_patch_200b.tar.gz
tar xvzf savage_patch_200b_to_200c.tar.gz

* After this, you should be able to play Savage succesfully while using XQF (and you're all up to date on linux with 2.00c).  I had used the EX2 mod for linux.  EX2 is nice to have since it actually updated you to 2.00e and has some really handy features in it.

NOTE: If you ever get errors complaining that some file cannot be opened or written to, just fix the permissions for those files in the /usr/local/game/Savage folder.  I have that directory owned by my user, not root.  That is what causes the "Couldn't open scripts.log" error message.  

You can safely ignore the libGL.so.1 warning.  From Zander @ Nvidia Corp:

> There was a bug in earlier NVIDIA driver releases that resulted in libGL.so symbols being stamped with version information; when applications are linked against these versions of libGL.so, they pick up a dependency on this version stamp. As of 1.0-6106, NVIDIA's libGL.so is no longer stamped with version information, hence the problem some users are seeing. The solution is to rebuild any affected packages against 1.0-6106's libGL.so.

Anyway, the ingame server browser for Linux is broken and well known.  Check the S2 forums for more information.  Warning: Your screen might melt from the numerous flames posted by Linux users.  Yes, I plopped down $30 for this game and share some of those same sentiments expressed there.  You basically need the 2.00e patch to correct this, but only 2.00c is available for Linux.  Here's 2 workarounds for that:

XQF:

1. sudo apt-get install xqf
2. Using your favorite editor, make the following file and call it 'savage.xqf'.

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd /usr/local/games/Savage
#LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./savage.bin /usr/local/games/Savage
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin $@ /usr/local/games/Savage
exit 0

* Or, alternatively, you can just modify the original /usr/local/games/Savage/savage script and make the one change shown above.  If so, be sure to substitute "savage" for "savage.xqf" in the XQF instructions below.

3. Make the file executable with chmod ug+x savage.xqf.
4. Move/copy that file into the /usr/local/games/Savage directory.
5. Launch XQF from your desktop menu or simply type xqf from a terminal.
6. Right click over the Savage entry in the Source menu (bottom left pane) > Add Master.  Make these entries:

Master Name: Master Server (or whatever you want to call it)
Master Address: [http://masterserver.savagedemo.s2games.com/gamelist_full.dat](http://masterserver.savagedemo.s2games.com/gamelist_full.dat)
* select the 'http' radio button at the bottom.

click OK.

NOTE: By the way, I just saw my post and vbulletin insists on wrapping url tags around that Master Address string I gave above. Here's the same url with a space after the http so that vbulletin will play nice:

http ://masterserver.savagedemo.s2games.com/gamelist_full.dat

7. Select Preferences > Games from the main menu.
8. Find the Savage entry and make the following changes under the "Invoking" tab:

Command Line: /usr/local/games/Savage/savage.xqf
Working Directory: /usr/local/games/Savage/

Click OK.

9. Go back to the left Source pane and you should see 2 entries under the Savage game:

S2 Games
Master Server

Click on the Master Server entry and click Update.  You should get a list of servers for Savage now.  You will launch the game through XQF from now on, unless you install the EX2 mod.

EX2:

1. Download the 'EX2_R4z_2.tar.gz' from [http://subsentient.com/savage/](http://subsentient.com/savage/)
2. Copy that file to the root directory of /usr/local/games/Savage just like you did for the 2.00b and 2.00c patches.  Untar/Gunzip it:

tar xvzf EX2_R4z_2.tar.gz

* You can now launch Savage by just typing 'savage' from a terminal or using your menu entry.  You will be presented with a login screen.  For some strange reason my original account doesn't work.  I assume this has to do with the old S2 authentication servers still being wonky for Linux folk like me.  Anyway, just create a unique account again with your CD key etc.  You should be able to launch Savage from within the builtin server browser now, instead of using XQF.

---

### Post by DarkGreen16 on 2005-05-09
thx alot got it running...I used SEP instead of EX2 its alot more recent IMO and serves as a 2.00e update for linux. Browser in game works just fine with it too. My main problem was the permissions (i thought it was smart enough to put it in a .savage folder but i guess not) 

So basically i thought it was the libGL.so.1 error that was preventing the game from running and not the scripts.log considering many other games have a similar error message because it generates them on first run.

Oh well goes to show you that you can't compare apples to oranges.

---

