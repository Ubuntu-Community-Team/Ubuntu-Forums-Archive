---
title: "sdlmame. an up to date sdl port of mame"
date: 2006-11-12
forum: Gaming &amp; Leisure
---

### Post by NESFreak on 2006-11-12
searching for the latest version of xmame i came to x.mame.net logically. There i found this.

the latest newsmessage on [http://x.mame.net/](http://x.mame.net/) states> I thought it might be good to let you know that we're still alive, but that there's been a change in the past couple of months: I've stepped down as maintainer and command has been assumed by Laurent Desnogues. Unfortunately for him, he stepped in during the big video rewrite for MAME 0.107, and it's going to take some time and effort to get xmame and xmess working again.

In the meantime, if you'd like to play with 0.108, I recommend that you try SDLmame and SDLmess, which are available from [Arbee's WIP Emporium]("http://rbelmont.mameworld.info/?page_id=163"). Laurent is basing his work off of RB and OG's baby, so you'll have an idea of what's in store. RPMs for Fedora Core 5 and 6 are also available, courtesy of XulChris.

it's a complete new port of the windows version of mame to SDL. AND the latest version 0.110u1 which in fact is the latest version of mame. So if you feel that xmame v0.106 is a bit outdated. Check it out. Unfortunately there isn't a .deb package.

NESFreak

---

### Post by leech on 2006-11-12
Hopefully this gets .deb packages and is put into the Debian / Ubuntu repositories when it's all caught up.  So I can keep my MythTV box up to date with Mame.  Not that the thousands of roms that Mame 0.106 supports isn't enough anyhow, but it never hurts to have more :D

Leech

---

### Post by NESFreak on 2006-11-20
since i couldn't find a proper front-end to sdlmame i decided to make one myself.
the problem: i only have limited bash skills, don't wanna even talk about other languages.
so i used what i could use: bash.

it's a small script that creates desktop icons for your roms.
it can even use iconpacks (like mame32)
-it's so stupid it should work with any version of mame and it integrates nice into your desktop.
btw, you do need to edit some settings first

-bug fix: not all icons end with ".ico".
-bug fix: turbo and maybe others are now named correctly.

Hope someone else likes it as well.
NESFreak

---

### Post by NESFreak on 2006-11-24
fixed some bugs.

-bug fix: not all icons end with ".ico".
-bug fix: turbo and maybe others are now named correctly.

NESFreak

---

### Post by jplegat on 2007-01-17
Heres is my package [http://www.404notfound.com.br/jpl/upload/sdlmame-0.110u1.deb]("http://www.404notfound.com.br/jpl/upload/sdlmame-0.110u1.deb")
compiled on Ubuntu 6.10.

feel free to check the package contents: dpkg –contents sdlmame-0.110u1.deb

usr/
usr/share/
usr/share/doc/
usr/share/doc/sdlmame/
usr/share/doc/sdlmame/README
opt/
opt/sdlmame/
opt/sdlmame/artwork/
opt/sdlmame/cfg/
opt/sdlmame/chdman
opt/sdlmame/comments/
opt/sdlmame/criar_pacote_deb.sh
opt/sdlmame/diff/
opt/sdlmame/docs/
opt/sdlmame/docs/mame.txt
opt/sdlmame/docs/newvideo.txt
opt/sdlmame/docs/windows.txt
opt/sdlmame/docs/license.txt
opt/sdlmame/file2str
opt/sdlmame/ini/
opt/sdlmame/jedutil
opt/sdlmame/mamepm
opt/sdlmame/mame.png
opt/sdlmame/nvram/
opt/sdlmame/romcmp
opt/sdlmame/roms/
opt/sdlmame/SDLMAME.txt
opt/sdlmame/ui.bdf
opt/sdlmame/whatsnew.txt

After installing the package, run mamepm -createconfig (as root)  to create the configuration file (it will be created at /opt/sdlmame) edit the file as you wish and then move/copy the file to your home directory, under a directory called .mame.

---

### Post by NESFreak on 2007-01-18
> **jplegat said:**
> Heres is my package [http://www.404notfound.com.br/jpl/upload/sdlmame-0.110u1.deb]("http://www.404notfound.com.br/jpl/upload/sdlmame-0.110u1.deb")
compiled on Ubuntu 6.10.

feel free to check the package contents: dpkg –contents sdlmame-0.110u1.deb
[...]
After installing the package, run mamepm -createconfig (as root)  to create the configuration file (it will be created at /opt/sdlmame) edit the file as you wish and then move/copy the file to your home directory, under a directory called .mame.

haven't tried it yet cause i'm using the latest version compiled for my Athlonxp. I've added your package to [https://wiki.ubuntu.com/MOTU/Packages/Candidates](https://wiki.ubuntu.com/MOTU/Packages/Candidates).

NESFreak

---

### Post by ludomatic on 2007-02-17
You'll find SDLMAME packaged for Ubuntu Edgy on a repository at [http://apt.ludomatic.fr]("http://apt.ludomatic.fr/?hl=en"). It's actually available for version 0.112u1.

```
ludo@ludgy:~$ dpkg -c /var/cache/pbuilder/result/sdlmame_0112u1-0ubuntu2_i386.deb
drwxr-xr-x root/root         0 2007-02-16 18:27 ./
drwxr-xr-x root/root         0 2007-02-16 18:27 ./etc/
drwxr-xr-x root/root         0 2007-02-16 18:27 ./etc/sdlmame/
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/sdlmame/
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/sdlmame/roms/
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/sdlmame/artwork/
-rwxr-xr-x root/root  28803012 2007-02-16 18:27 ./usr/share/sdlmame/mame
-rwxr-xr-x root/root    136280 2007-02-16 18:27 ./usr/share/sdlmame/chdman
-rwxr-xr-x root/root      4264 2007-02-16 18:27 ./usr/share/sdlmame/file2str
-rwxr-xr-x root/root     47172 2007-02-16 18:27 ./usr/share/sdlmame/romcmp
-rw-r--r-- root/root      4244 2007-02-16 18:07 ./usr/share/sdlmame/mame.xpm
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/doc/
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/doc/sdlmame/
-rw-r--r-- root/root      3975 2007-02-13 12:20 ./usr/share/doc/sdlmame/SDLMAME.txt.gz
-rw-r--r-- root/root    387475 2007-02-06 01:00 ./usr/share/doc/sdlmame/whatsnew.txt.gz
-rw-r--r-- root/root      3301 2007-02-06 01:00 ./usr/share/doc/sdlmame/newvideo.txt.gz
-rw-r--r-- root/root      3332 2007-02-06 01:00 ./usr/share/doc/sdlmame/mame.txt
-rw-r--r-- root/root       273 2007-02-16 18:07 ./usr/share/doc/sdlmame/README.Debian
-rw-r--r-- root/root      2280 2007-02-16 18:07 ./usr/share/doc/sdlmame/copyright
-rw-r--r-- root/root       839 2007-02-16 18:07 ./usr/share/doc/sdlmame/changelog.Debian.gz
-rw-r--r-- root/root      3475 2007-02-13 02:03 ./usr/share/doc/sdlmame/whatsnew_0112u1.txt.gz
-rw-r--r-- root/root     13680 2007-02-06 01:00 ./usr/share/doc/sdlmame/windows.txt.gz
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/applications/
-rw-r--r-- root/root       200 2007-02-16 18:07 ./usr/share/applications/sdlmame.desktop
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/man/
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/man/man6/
-rw-r--r-- root/root      1601 2007-02-16 18:07 ./usr/share/man/man6/sdlmame.6.gz
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/man/fr/
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/share/man/fr/man6/
-rw-r--r-- root/root      1770 2007-02-16 18:07 ./usr/share/man/fr/man6/sdlmame.6.gz
drwxr-xr-x root/root         0 2007-02-16 18:27 ./usr/games/
-rwxr-xr-x root/root        42 2007-02-16 18:07 ./usr/games/sdlmame
lrwxrwxrwx root/root         0 2007-02-16 18:27 ./etc/sdlmame/mame.ini -> /usr/share/sdlmame/mame.ini

```

It should work fine, all info available at [http://apt.ludomatic.fr]("http://apt.ludomatic.fr/?hl=en") or with ```

$ man sdlmame
``` after install.

happy play :-)

---

### Post by c.falco on 2007-02-26
I was already working on packaging SDLMame 0.112; I'm sorry I didn't read the forums in time... :|

As posted on the [SDLMame  forum]("http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1"), I uploaded the source package on REVU for reviews. I hope they will be included in the official universe/multiverse repository in the future. :)

Binary are also available for dapper, edgy and feisty [here]("http://wallyweek.altervista.org").

---

### Post by ludomatic on 2007-02-26
nice !

by the way, I keep an up-to-date packaging of SDLMAME now in version 0.112u2 :)

you can add the repository in your sources.list :
```
  deb [http://apt.ludomatic.fr](http://apt.ludomatic.fr) edgy contrib
  deb-src [http://apt.ludomatic.fr](http://apt.ludomatic.fr) edgy contrib
```

then simply add my security key :
```
  $ wget [http://apt.ludomatic.fr/ludomatic.key.asc](http://apt.ludomatic.fr/ludomatic.key.asc) -O - | sudo apt-key add -
```
and install sdlmame :
```
  $ sudo apt-get install sdlmame
```

you will have an up-to-date sdlmame every time a release is done :)

---

### Post by ludomatic on 2007-02-28
Update: sdlmame version 0112u3 is out and packaged ;)

---

### Post by jplegat on 2007-02-28
> **ludomatic said:**
> Update: sdlmame version 0112u3 is out and packaged ;)


Works like a charm, thanks a lot for the repository and packaging it properly ;-)

The only bizarre thing is when I launch SDLMame from the Games menu, it loads a pre-selected game rom -I  can´t remember the name now- which sends my mouse to oblivion. I can only get the mouse back if I restart the X server. 

It would be nice if SDLMame could be packaged along Sdlanza frontend [http://it.geocities.com/pinguinogoloso/]("http://it.geocities.com/pinguinogoloso/") and the entry added to the Games menu, instead of launching a pre-selected rom.

---

### Post by plb on 2007-03-06
113 is now out

---

### Post by ludomatic on 2007-03-06
plb > 113 is now out

Hi, yes sdlmame package v0.113 (i386) for Edgy is [available]("http://apt.ludomatic.fr/") since a few hours :)

jplegat > Works like a charm, thanks a lot for the repository and packaging it properly

Thanks, I've tried several months before being able to understand the packaging process and figure out how to patch the sdlmame makefile...

jplegat > The only bizarre thing is when I launch SDLMame from the Games menu, it loads a pre-selected game rom -I can´t remember the name now- which sends my mouse to oblivion. I can only get the mouse back if I restart the X server.

You're right, as a wanted to launch SDLMAME for the 10th anniversary, I've packaged it "as-is" without any frontend. I actually publish a recent extra package that contains ALL up-to-date files necessary to run a frontend (full artworks, history, samples, and so on) named "sdlmame-extra" : you can already search and install the "sdlmame-extra" package ;) but note that I'm testing this package and the "beta" stage contains only files for Free roms. I'll put a "final" package as soon as files for version 0.113 will be available.

My idea is to stick on every stable release of MAME and offer an up-to-date :
- sdlmame package (executable and minimal directories and Free roms)
- sdlmame-extra package (group of extra files)
- a frontend (I personaly use WahCade but it needs hack to work with sdlmame)

jplegat > It would be nice if SDLMame could be packaged along Sdlanza frontend [http://it.geocities.com/pinguinogoloso/](http://it.geocities.com/pinguinogoloso/) and the entry added to the Games menu, instead of launching a pre-selected rom.

Actually, I wanted to try the menu icon so I used sdlmame with gridlee by default, so if you want to play another game you have to just type it in a terminal (ex: "$ mame circus"). I'll look for Sdlanza right now, as I wanted to offer a configurated frontend with sdlmame :)

Happy play!

---

### Post by ludomatic on 2007-03-07
Ok I've tried SDLAnza and I just had to customize the command line in the .cfg to play with SDLMAME. It's a lightweight FrontEnd but the bad things are :
- Snapshots must be .gif and not in the default .png format
- Can't use extra files (mameinfo, catver, etc) that are (in my opinion) very usefull to do filters or to know if a rom is in a preliminary stage and so on...

I think it could be possible to use .PNG snapshots but adding functionnalities to read extra files are far away from my "null" skills in Tcl/Tk :/

I personally use [WahCade]("http://www.anti-particle.com/wahcade.shtml") that offers a lot of possibilites :
    * It's MameWAH for GNU/Linux!
    * It uses MameWah's config files and layouts.
    * It has a keyboard controlled GUI - Perfect for those arcade controls.
    * It runs x.mame games and other emulators too.
    * A History Viewer.
    * A Control Panel Viewer.
    * A Layout Editor.
    * A Setup Editor.
with a minimum requirements :
    *  python >= 2.4
    * pygtk2 >= 2.6
    * elementtree / celementree (for extra speed)
But [path seems to bug with sdlmame]("http://www.anti-particle.com/forum/viewtopic.php?t=10"), it seems it only reads mame.ini into the "~/.mame/" folder...


If someone has in its bag a free frontend, with no big KDE/Gnome dependances, that reads extra files and can be tweaked to use SDLMAME let me know.

---

### Post by c.falco on 2007-03-08
> **ludomatic said:**
> 
My idea is to stick on every stable release of MAME and offer an up-to-date :
- sdlmame package (executable and minimal directories and Free roms)
- sdlmame-extra package (group of extra files)
- a frontend (I personaly use WahCade but it needs hack to work with sdlmame)


As you know, I'm working to put a set of sdlmame related packages in the Universe repository, so I think we could join our efforts to make it full policy compliant. :)

At present my source package builds two binary packages:
**sdlmame** (the emulator itself)
**sdlmame-tools** (chdman, jedutil, romcmp etc.)

I'm testing a further package **sdlmame-cheat**, which will depend on **sdlmame** and will install the cheat.dat file along with the necessary changes to the default mame.ini file. It should be uploadable in a couple of days.

I'm planning extra packages too, but I think that we shouldn't put a giant 50mb-or-so .deb file in a repository. A set of sdlmame-sample-*<game_name>* would be more desiderable, to improve maintainance and saving download time for users.

If you are willing to share ideas and anything more, I'll be glad to work with you! :)

---

### Post by ludomatic on 2007-03-08
> 
As you know, I'm working to put a set of sdlmame related packages in the Universe repository, so I think we could join our efforts to make it full policy compliant.


Hi, first of all you could have seen my package was published and referenced in several forums **before** publishing yours and ask integration in the official Ubuntu repository.

That said, I hope we share the Ubuntu spirit and yes, it could be nice if we can join efforts to offer a well policy compliant sdlmame package. In my mind, the final user is more important.

> 
At present my source package builds two binary packages:
sdlmame (the emulator itself)
sdlmame-tools (chdman, jedutil, romcmp etc.)


Ok, my current packages are :
[LIST]
[*]sdlmame (minimal structure in /usr/share/sdlmame and some practical links and menus elsewhere)
[*]sdlmame-extra (addons files like cheats, history, mameinfo and addons uptodate folders like artworks, samples, etc.) this package depends on sdlmame and is available in a lightweight version because I'm waiting for some files to be published for version 0.113.
[/LIST]

> 
I'm testing a further package sdlmame-cheat, which will depend on sdlmame and will install the cheat.dat file along with the necessary changes to the default mame.ini file. It should be uploadable in a couple of days.
I'm planning extra packages too, but I think that we shouldn't put a giant 50mb-or-so .deb file in a repository. A set of sdlmame-sample-<game_name> would be more desiderable, to improve maintainance and saving download time for users.


As you have noticed, sdlmame-extra is a *big* package (~600Mb) if all files are inside. The method I have in mind is a small scripting package to let the user directly choose to download the files he needs :) then he can just have the files for some games or the full pack if he wants.

Along with those packages, I've tested multiple frontends  and I think that I will offer sdlanza in a preconfigured package to let the final user play in a gui interface, not in command-line. This Frontend does not support .png nor mameinfo and catver but I will contact the author to ask him what he thinks about that

> 
If you are willing to share ideas and anything more, I'll be glad to work with you!


well, you've just read my roadmap ;) comments are opened

---

### Post by c.falco on 2007-03-09
> **ludomatic said:**
> Hi, first of all you could have seen my package was published and referenced in several forums **before** publishing yours and ask integration in the official Ubuntu repository.
Well, I **did** look for existing packages even before starting to **work** on mine. Simply didn't find yours, and I apologize for that. :(
That's definitely bad _luck_, not bad _will_. :)

> **ludomatic said:**
> 
That said, I hope we share the Ubuntu spirit and yes, it could be nice if we can join efforts to offer a well policy compliant sdlmame package. In my mind, the final user is more important.
Of course we do, or we would be using some different OS! ;)

> **ludomatic said:**
> 
well, you've just read my roadmap ;) comments are opened
I think we should ask the forum moderator(s) if this is the right place for packaging discussions, before flooding other users with looooong posts... ;)

For now, [a new thread]("http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=27606&page=1#Post27606") was started on the SDLMame forum by groucho, who is preparing the debian packages.

---

### Post by fireedo on 2007-03-24
Also consider "QMC2" QT MAMECAT II Launcher as it's an active project and I think it's the most atractive SDLmame or Xmame frontend :)
[http://www.mameworld.net/mamecat/](http://www.mameworld.net/mamecat/)

---

### Post by ludomatic on 2007-03-25
hi fireedo,

I have difficulties to get the good QT version (Qt 4.2.0+) when doing the '$ make'
do you have a guide somewhere to easily build QMC2 with correct dependencies ?

---

### Post by gaspar on 2007-03-26
Anyone ever tried [Loemu]("http://loemu.pegueroles.com/body.html")?

---

### Post by ludomatic on 2007-03-27
nope, never heard of it but I'll try it asap, thanks for the info

---

### Post by gaspar on 2007-03-27
Ok, so I tried Loemu, could not make it work. Back to wah!cade then.
The problem is, when I try to load a game, it shows the progress, then, at "load complete", it goes back to the game list.
What could that be?

---

### Post by ludomatic on 2007-03-28
hi!

I use Wah!Cade on my mamecab too, it's the the frontend I finally prefer but it doesn't like sdlmame : you have to reconfigure your mame.ini.

1/ Create a ".mame" directory in your home path and link your "/usr/share/sdlmame/mame.ini' here.

2/ Use full path (not relative) to the MAME folders. Edit those lines of your fresh "~/.mame/mame.ini" like this :
```
#
# CORE SEARCH PATH OPTIONS
#
rompath                   /full/path/to/roms
samplepath                /full/path/to/samples
artpath                   /full/path/to/artwork
ctrlrpath                 /full/path/to/ctrlr
inipath                   $HOME/.mame;.;ini
fontpath                  .

#
# CORE OUTPUT DIRECTORY OPTIONS
#
cfg_directory             /full/path/to/cfg
nvram_directory           /full/path/to/nvram
memcard_directory         /full/path/to/memcard
input_directory           /full/path/to/inp
state_directory           /full/path/to/sta
snapshot_directory        /full/path/to/snap
diff_directory            /full/path/to/diff
comment_directory         /full/path/to/comments

```

3/ Create missing directories you've just defined (cfg, nvram, memcard, ...) if they dont exist.

Wahcade should correctly lauch sdlmame now (don't forget to reload gamelist in the wahcade menu)

4/ If ever you have the same problem, don't hesitate to ask sdlmame to generate logs. In your "mame.ini", apply those values :
```
#
# DEBUGGING OPTIONS
#
log                       0
oslog                     1
verbose                   1

```

After having launched sdlmame via wahcade you should have a new "~/.wahcade/emulator.log" file with maybe those kind of errors inside :
```
19xu.03 NOT FOUND
19xu.04 NOT FOUND
19xu.05 NOT FOUND
19xu.06 NOT FOUND
19x.07 NOT FOUND
19x.13m NOT FOUND
19x.15m NOT FOUND
19x.17m NOT FOUND
19x.19m NOT FOUND
19x.14m NOT FOUND
19x.16m NOT FOUND
19x.18m NOT FOUND
19x.20m NOT FOUND
19x.01 NOT FOUND
19x.11m NOT FOUND
19x.12m NOT FOUND
ERROR: required files are missing, the game cannot be run.

```

I hope that will help to resolve your "silent" error !

---

### Post by gaspar on 2007-03-28
Thanks a lot for the quick reply!
I´ll give it a try tonight, and let you know :)

---

### Post by zcal on 2008-01-16
> **ludomatic said:**
> you can add the repository in your sources.list

Is your repository still being maintained?  I recently added it to my sources.list in Debian Etch (which is no longer numbered 3.2, by the way).  Aptitude updates just fine with it, but the sdlmame package is nowhere to be found.

---

### Post by ludomatic on 2008-01-16
not actually, I had errors with Falcon (soft used to create the debian/ubuntu repository) since they have changed their version and new one still have pbs.

another deb is available now : [http://wallyweek.altervista.org/](http://wallyweek.altervista.org/)

---

### Post by ludomatic on 2008-04-20
up to date now: [http://apt.ludomatic.fr/]("http://apt.ludomatic.fr/") for Debian and Ubuntu :)

---

