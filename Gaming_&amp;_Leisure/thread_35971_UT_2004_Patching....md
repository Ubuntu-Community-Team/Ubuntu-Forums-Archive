---
title: "UT 2004 Patching..."
date: 2005-05-21
forum: Gaming &amp; Leisure
---

### Post by robtotheb on 2005-05-21
Using the link 
[http://0day.icculus.org/ut2004/](http://0day.icculus.org/ut2004/)
I downloaded the patches to UT2004.  Unzipped them and placed them in the correct folder (choosing the replace option).  Now when I try to launch UT2004 nothing happens.  Was working fine before.  What did I do wrong?

Just tried it from terminal and got this error...

./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by Zeroedout on 2005-05-21
try launching it with just "ut2004"

---

### Post by Watcher on 2005-06-16
This may look as a very silly question but i just downloaded some patches for ut2004 but they are in .tar.bz2 format so i guess i need to unzip in a directory, but don't really have a clue where. can anyone give me some help on this?

---

### Post by Takis on 2005-06-16
There's a readme that should come with the files, if I remember correctly. Just put them in your ut2004 directory, overwriting any files you're prompted about.

Out of curiousity, I did this patch recently and suddenly 'Bonus Vehicles' rocked up in Onslaught mode. I'm yet to see any of these vehicles, has anybody seen them?

---

### Post by Khannie on 2005-06-17
[QUOTE=Watcher]This may look as a very silly question but i just downloaded some patches for ut2004 but they are in .tar.bz2 format so i guess i need to unzip in a directory, but don't really have a clue where. can anyone give me some help on this?[/QUOTE]

tar -jxvf filename.tar.bz2

---

### Post by Khannie on 2005-06-17
[QUOTE=Takis]There's a readme that should come with the files, if I remember correctly. Just put them in your ut2004 directory, overwriting any files you're prompted about.

Out of curiousity, I did this patch recently and suddenly 'Bonus Vehicles' rocked up in Onslaught mode. I'm yet to see any of these vehicles, has anybody seen them?[/QUOTE]

Did you install the ECE? 

The latest patch likes you to have the ECE installed first.

You can get a linux friendly version from the [www.unreal.ie](www.unreal.ie) site [here](http://www.unreal.ie/dl/patches/ut2004-ECEBonusPack.tar.bz2).

---

### Post by Takis on 2005-06-19
Coolies cheers.

---

### Post by nrayever on 2005-06-25
this may sound a bit stupid, but can someone tell me, step by step, how to update ut2004??

i tried just to copy patch 3323, but know i got a message:

./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

so i really need to know a howto update ut2004, please!! ](*,)  ](*,)

---

### Post by Curlydave on 2005-06-25
I can't seem to get the tars to extract right, and doing it manually is a pain in the ass.

---

### Post by Takis on 2005-06-25
[QUOTE=nrayever]this may sound a bit stupid, but can someone tell me, step by step, how to update ut2004??

i tried just to copy patch 3323, but know i got a message:

./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

so i really need to know a howto update ut2004, please!! ](*,)  ](*,)[/QUOTE]
So was UT2004 running before you tried to update? It seems really odd that you're getting an error about libSDL because UT would never have worked without it. In any case, get [this](http://www.libsdl.org/release/SDL-1.2.8.tar.gz) file, extract it to a temporary directory and run
```
$ ./configure
$ make
$ sudo make install
```
Now it may have been when I compiled this, or it may have been for AL audio, but one of them complained during make time that it couldn't find 'gmake'. In this case, edit the file 'Makefile' (with a capital 'M') and change 'gmake' to 'make' - it should be very close to the beginning of the file.

---

### Post by Takis on 2005-06-25
[QUOTE=Curlydave]I can't seem to get the tars to extract right, and doing it manually is a pain in the ass.[/QUOTE]
...could you be a little more specific?  :)

---

### Post by nrayever on 2005-06-25
here it's how i installed ut2004, takis.

1) i installed ut2004 from the cd's, it runned smooth. no probs
2) then i tried play online, but i really got some problems. after like an hour of downloading maps, etc.. i still couldn't connect to a server to play.
3) so i tried to get and update patch. i saw the lastest patch, that is 3355. but  i saw this post that said: you must have installed ECE patch to update.
4) i downloaded ECE patch, but when i untar it, i saw only directories and no instructions on how to patch.
5) a file located in help, said: you need at least patch 3323 to use ECE patch
6) i downloaded patch 3323 and only dirs again. so i tried just to copy them to my ut2004 directory.
6) when i tried to run ut2004 i got that message, missing libsdl.....

so i would really like to know how is supposed to apply any patch to ut2004, if there is no "installer type file". may doing something wrong?? please takis if you explain me what i'm doing wrong?? i will really appreciate it.

nrayever

---

### Post by Zeroedout on 2005-06-26
okay, untar 3323 as root (sudo file-roller) to your ut2004 directry (should be /usr/local/games/ut2004). Go to this page [http://liflg.org/?catid=6&gameid=17](http://liflg.org/?catid=6&gameid=17) and grab the ECE pack direct link is [http://liflg.org/?what=dl&catid=6&gameid=17&filename=ece.bonus_1.1-english.run](http://liflg.org/?what=dl&catid=6&gameid=17&filename=ece.bonus_1.1-english.run) but use bitorrent if possible, puts less drain on their servers. execute that as root ( "sudo sh ece.bonus_1.1-english.run" and if that dosn't work, "chmod +x ece.bonus_1.1-english.run" , then "sudo ./ece.bonus_1.1-english.run" ). then grab patch 3355 [http://liflg.org/?what=dl&catid=6&gameid=17&filename=ut2004_3355-multilanguage-x86.update.run](http://liflg.org/?what=dl&catid=6&gameid=17&filename=ut2004_3355-multilanguage-x86.update.run)
thats a direct link again, but best to use bittorrent is possible and run that and let it install  and you should be set. If you already applied some stuff in the worng order, uninstall and reinstall ut2k4 again.

---

### Post by Curlydave on 2005-06-26
[QUOTE=Takis]...could you be a little more specific?  :)[/QUOTE]

I've just done it manually after giving up on the archive manager. If I do it without "recreate folders", it lumps all of the files into the main directory-not cool. If I have the option enabled, it does its thing for a little bit, and then says that it cannot extract most of the files.

---

### Post by nrayever on 2005-06-26
thanks Zeroedout i'm going to try it right now. i hope i have no problems because i have amd64. thanks!

------------------------------------------------------------------------------------------------------

thanks again Zeroedout. now my ut2004 is updated and working!!! a good explaination. maybe used as a howto.

thanks a lot!! \\:D/  \\:D/  \\:D/

---

### Post by Takis on 2005-06-26
Ah this was a bit of a misunderstanding, nrayever. I wanted the ECE pack for the bonus vehicles to work properly, not to get the 3355 patch working. However, I didn't manage to get them working overall so I'll give Zeroedout's solution a go.

As a side note though Zeroedout, you shouldn't really need root priviledges to do any of those things because you don't need them when you install the game. Is there a reason you suggested using root priviledges?

---

### Post by Takis on 2005-06-26
[QUOTE=Curlydave]I've just done it manually after giving up on the archive manager. If I do it without "recreate folders", it lumps all of the files into the main directory-not cool. If I have the option enabled, it does its thing for a little bit, and then says that it cannot extract most of the files.[/QUOTE]
Yeah it was giving me a bit of trouble so I extracted them elsewhere and moved the files myself. Not a particularly elegant solution, but it's not like you need to do it every day so it doesn't really matter.

---

### Post by Zeroedout on 2005-06-26
[QUOTE=Takis]....

As a side note though Zeroedout, you shouldn't really need root priviledges to do any of those things because you don't need them when you install the game. Is there a reason you suggested using root priviledges?[/QUOTE]

ummm, I'm pretty sure you need root to write in /usr/local/games/ i mean correct me if i'm wrong, but if you don't you should. There should be no reason for an oridinary user to be able to modify game files, or write to the game directry. In your own home folder for configureation, yes ofcourse, but no reason in the actual game directry, is there?

---

### Post by Takis on 2005-06-27
[QUOTE=Zeroedout]ummm, I'm pretty sure you need root to write in /usr/local/games/ i mean correct me if i'm wrong, but if you don't you should. There should be no reason for an oridinary user to be able to modify game files, or write to the game directry. In your own home folder for configureation, yes ofcourse, but no reason in the actual game directry, is there?[/QUOTE]
Hmm yeah you're right, I had my own install in my head, where I installed UT in my home directory.

---

### Post by RastaMahata on 2005-06-27
easiest way to install games and easily update them: [http://liflg.org/](http://liflg.org/)

they have installers for wine/cedega, and native games, and they also have an utility to keep them updated :)

---

### Post by Gaming_Junkie on 2006-01-12
Hey, I just patched my UT 2004 to the newest version, 3369.

Here's how:
1. Download both the ECE pack and update 3369 for Linux([http://www.beyondunreal.com/main/ut2004/ut2004essential.php](http://www.beyondunreal.com/main/ut2004/ut2004essential.php))
2.  Open up nautilus (folder browser) as root, and get into the ut 2004 folder
3. Manually overwrite the folders with the new ones, first the ECE, then 3369 update.  

Make sure you overwrite all the folders first with the Editor's choice edition files.  I'm not exactly sure if it makes any difference, but I heard it could.

---

