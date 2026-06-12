---
title: "sdlmame, QMC2, and cheating"
date: 2009-06-08
forum: Gaming &amp; Leisure
---

### Post by Zeikcied on 2009-06-08
I just installed sdlmame 0.131u4 (via a .deb file I found) and QMC2 0.2b8 (via source and checkinstall), and I'm running into a bit of an issue.

sdlmame starts up just fine, and I have everything pretty much configured.  But I can't get the cheats to work.

In the /etc/sdlmame/mame.ini file, I have cheat set to 1 (which is true), and the cheatpath set to the cheat.zip file.  I also have QMC2 set with the exact same options.  Yet when I start sdlmame and bring up the menu via Tab, it doesn't give me the cheat option.

I don't know if sdlmame doesn't support cheats anymore, or if something isn't working properly.  I'm absolutely lost, and I'm sure it's probably something trivial.  But I need help. :(

---

### Post by disturbedite on 2009-06-08
my first guess would be you have an outdated cheat file, assuming you're using an up-to-date mame version (0.132 release today).

i believe it was about 0.130 that cheats were "broken" due to some major changes. pugsy has since updated his cheat file to work again. get it here:
[http://cheat.retrogames.com/](http://cheat.retrogames.com/)

---

### Post by Zeikcied on 2009-06-08
> **disturbedite said:**
> my first guess would be you have an outdated cheat file, assuming you're using an up-to-date mame version (0.132 release today).

i believe it was about 0.130 that cheats were "broken" due to some major changes. pugsy has since updated his cheat file to work again. get it here:
[http://cheat.retrogames.com/](http://cheat.retrogames.com/)

Well, I installed sdlmame 0.131u4, as stated above.  And I found and downloaded the latest cheat file from that site last night.  So it should be up to date.

Usually if it's an issue with the cheat file, it at least gives me the option of going to the Cheat menu.  It will say on the Cheat menu that the cheat file wasn't found or is outdated, but I will at least see it on the main menu.

When I look at the main menu (via Tab), there isn't any mention of cheats.  It's as if cheats were turned off.  But as I said, both the mame.ini and QMC2 configurations have the Cheat option turned on.  I don't understand why sdlmame isn't activating cheats.

EDIT: Even running sdlmame from the terminal (without the QMC2 frontend) doesn't activate cheats. :(

---

### Post by disturbedite on 2009-06-09
well, here is the sdlmame forum: [http://www.bannister.org/forums/ubbthreads.php?ubb=cfrm](http://www.bannister.org/forums/ubbthreads.php?ubb=cfrm)

and here is the QMC2 forum: [http://sourceforge.net/forum/?group_id=187890](http://sourceforge.net/forum/?group_id=187890)

there is also a QMC2 mailing list: [http://sourceforge.net/mailarchive/forum.php?forum_name=qmc2-devel](http://sourceforge.net/mailarchive/forum.php?forum_name=qmc2-devel)

i think asking about it there is a much better idea (more likely to be answered).

---

### Post by Zeikcied on 2011-04-15
Nearly two years later and I'm having the same issue.

I installed the Mame package (formerly sdlmame) from the official repositories, and I installed QMC2 from their own Ubuntu repos.

I tried configuring QMC2 to enable cheats and point to the cheatpath, but it doesn't seem to call Mame with the cheatpath option.

Also, I have /etc/mame/mame.ini and ~/.mame/mame.ini set properly.  I have cheat set to 1 and the cheatpath is the directory that has my cheat.zip file.  I even ran "mame -showconfig" and it shows that cheat and cheatpath are properly set.

Now, I got my cheat.zip file from the cheat0141.zip file I downloaded, but KPackageKit says Mame is version 0.139.  Would that have something to do with it not working?  I just assumed that Mame version numbers wouldn't affect whether or not the cheat files work.

---

### Post by wellsilva on 2011-07-11
Hey man, I've got it working**. **I've tried billions of command lines, but at the  time I've put it in the ~/.mame/ directory it worked. I don't understand  why it simply ignore  the specifications given at the command line. Really strage. ¬¬

**Reading the README.Debian gave me the idea.**

wellington@Sage:/home/arquivos/jogos/mame$ grep -A1 -i cheat /usr/share/doc/mame/README.Debian
*   zipped cheat files can be put either in main directories like baseline
    (i.e. $HOME/.mame/ and /usr/local/share/games/mame/) or the cheat/
    subdirectory
wellington@Sage:/home/arquivos/jogos/mame$


**I did the following steps:**

[B]-- install using the instructions here (I think that doesn't make difference if it's without this mirror, but I didn't test) [http://sdlmame.wallyweek.org/repository/](http://sdlmame.wallyweek.org/repository/)
(evidences bellow)[/B]

wellington@Sage:/home/arquivos/jogos/mame$ dpkg -l mame
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nome                              Versão                           Descrição
+++-=================================-=================================-==================================================================================
ii  mame                              0.142u6-0ubuntu1~ppa1~maverick    The Multiple Arcade Machine Emulator - MAME
wellington@Sage:/home/arquivos/jogos/mame$

**-- download the last cheatfile from here (used the version 0.142) **[http://www.mamecheat.co.uk/](http://www.mamecheat.co.uk/)

**-- putting the cheat in my ~/.mame directory (evidences bellow):**
wellington@Sage:/home/arquivos/jogos/mame$ ls -ltr ~/.mame
total 65196
-rwxr-xr-x 1 wellington wellington 40445845 2011-07-10 17:01 roms
drwxr-xr-x 2 wellington wellington      160 2011-07-10 20:12 nvram
drwxr-xr-x 2 wellington wellington      240 2011-07-10 20:12 cfg
-rw-r--r-- 1 wellington wellington 26244223 2011-07-10 20:17 cheat.zip
drwxr-xr-x 2 wellington wellington      112 2011-07-10 20:17 cheat
drwxr-xr-x 3 wellington wellington       72 2011-07-10 20:26 memcard
drwxr-xr-x 3 wellington wellington       72 2011-07-10 20:30 sta
wellington@Sage:/home/arquivos/jogos/mame$

**--- change the cheat option to 1  on /etc/mame/mame.ini, with some text editor (evidences bellow):**
wellington@Sage:/home/arquivos/jogos/mame$ grep -i cheat /etc/mame/mame.ini |tail -1
cheat                     1  
wellington@Sage:/home/arquivos/jogos/mame$ 


Good Luck

---

### Post by wellsilva on 2011-07-11
There's one more thing:

[B]--- I've changed the option video to* soft* on */etc/mame/mame.ini *file. Before this, the game did start, but too slowly.
[/B]
wellington@Sage:/home/arquivos/jogos/mame$ grep -B 2 -i soft /etc/mame/mame.ini
# VIDEO OPTIONS
#
video                     soft
wellington@Sage:/home/arquivos/jogos/mame$ 

Good Luck

---

### Post by disturbedite on 2011-07-12
Shouldn't use software as the renderer unless your hardware is incapable of running mame with openGL. It takes away a lot of functionality. However, if it is the only way you can run games at decent speed, then it is your only option (short of getting new hardware).

---

