---
title: "Reports on old Loki games compatibility"
date: 2005-03-20
forum: Gaming &amp; Leisure
---

### Post by ACK!! on 2005-03-20
Ok, listen this thread is for reporting luck in getting the old school loki games running on the new bright and shiny Hoary.  

Let me start this off:

It seems that Sid Meir's Alpha Centauri works.

Both Heretic2 and Myth2 (my first linux game :(  ) segfaulted when running on Hoary.

---

### Post by fackamato on 2005-03-20
[QUOTE=ACK!!]Ok, listen this thread is for reporting luck in getting the old school loki games running on the new bright and shiny Hoary.  

Let me start this off:

It seems that Sid Meir's Alpha Centauri works.

Both Heretic2 and Myth2 (my first linux game :(  ) segfaulted when running on Hoary.[/QUOTE]

Descent3 doesn't work. :(

fackamato@fackamato:~ $ descent3
SIGNAL 11 caught, aborting
Recursive signal cleanup! Hard exit! AHHGGGG!

---

### Post by v6sa on 2005-03-20
descent3 works, some file required renaming, that fixed segfault problem. i dont remember exact filename (/usr/local/xxx/descent3/xxx.hog)

---

### Post by fackamato on 2005-03-20
[QUOTE=v6sa]descent3 works, some file required renaming, that fixed segfault problem. i dont remember exact filename (/usr/local/xxx/descent3/xxx.hog)[/QUOTE]


Yes, google revealed it:

> Q: Descent 3 doesn't work on my 2.6 kernel, how can I fix it?

A: su - to root, cd to your Descent 3 directory (/usr/local/games/descent3, usually). Then ln -s ppics.hog PPics.Hog

---

### Post by mglukhovsky on 2005-03-20
After a lot of research I've finally managed to get SimCity 3000 running! Moreover, I think that this might solve a lot of these "Segmentation fault" problems.

With a basic install, this is what happens:
```
michael@ubuntu:/opt/cxoffice$ sc3u
sc3u: relocation error: sc3u: symbol _dl_global_scope, version GLIBC_2.0 not defined in file ld-linux.so.2 with link time reference
```

I installed libg++2.8.1.3-glibc2.2 and libstdc++2.10-glibc2.2, but I'm not sure if this is the root of the problem. Just in case, make sure these are installed.

Updating the game is a good next step. Although Loki is closed, there are still product updates available on the net. The site I used was [http://public.planetmirror.com/pub/lokigames/patches/](http://public.planetmirror.com/pub/lokigames/patches/) , but any site listed on [http://updates.lokigames.com/](http://updates.lokigames.com/) will do. Instead of using the generic Loki update tool, which I suspect will not work because their updates server is down, downloaded the latest patch as a ".run" file.

Just to be sure, I made the update script executable:
```
chmod +x  sc3u-2.0a-x86.run
```
Run the update script with "--keep". The "--keep" option is VERY important, I was not able to get the script to run otherwise: ```
sh sc3u-2.0a-x86.run --keep
```

Running the game with just "sc3u" results in a segfault. The solution is to instead start ALL Loki games with: ```
LD_ASSUME_KERNEL=2.2.5 /usr/local/bin/[NAME OF GAME]
```
In other words, to start SimCity 3000:
michael@ubuntu:~$ LD_ASSUME_KERNEL=2.2.5 /usr/local/bin/sc3u

NB: Some have reported that using LD_ASSUME_KERNEL=2.2.4 works better for them. I haven't had a problem with 2.2.5 so far.

References:
[http://updates.lokigames.com/](http://updates.lokigames.com/)
[http://public.planetmirror.com/pub/lokigames/patches/](http://public.planetmirror.com/pub/lokigames/patches/)
[http://www.linuxquestions.org/questions/showthread.php?s=&postid=956088#post956088]http://www.linuxquestions.org/questions/showthread.php?s=&postid=956088#post956088](http://www.linuxquestions.org/questions/showthread.php?s=&postid=956088#post956088]http://www.linuxquestions.org/questions/showthread.php?s=&postid=956088#post956088) 
[http://www.linuxquestions.org/questions/showthread.php?s=&postid=1308916#post1308916](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1308916#post1308916)
[http://www.linux-gamers.net/modules/newbb/viewtopic.php?viewmode=flat&topic_id=934&forum=15](http://www.linux-gamers.net/modules/newbb/viewtopic.php?viewmode=flat&topic_id=934&forum=15)
[http://www.linuxquestions.org/questions/history/55591](http://www.linuxquestions.org/questions/history/55591)

Hope this helps!

-Mike Glukhovsky

---

### Post by atf487 on 2005-03-20
soldier of fortune works great.

---

### Post by jdodson on 2005-03-21
unreal tournament goty works fine.

---

### Post by grendelkhan on 2005-03-26
Tried the above solutions and still could not get Eric's Ultimate Solitaire to load.

---

### Post by mglukhovsky on 2005-03-27
Are you getting a segfault? What sort of problems? If you haven't already, launch it from a Gnome Terminal and let me know what errors come up.

---

### Post by grendelkhan on 2005-03-27
Yeah, it's a seg fault.  No other error messages, just the seg fault

I am TOTALLY bumming too, since it's by far the best solitaire game I've found and it's totally addictive.

---

### Post by mglukhovsky on 2005-03-27
Not to re-iterate, but this is by far the key to fooling most Loki games into running. Make sure you are starting it with: 
LD_ASSUME_KERNEL=2.2.5 /usr/local/bin/[NAME OF GAME]

Try older kernels as well, i.e. 2.2.4 or 2.2.3. I'll have a look around and let you know if I see something on the net.

---

### Post by mglukhovsky on 2005-03-27
Alright, that was quick! Some more research with Google yielded a few AMAZING websites that should help everyone out.

Check the following sites for more help with installing/running older Loki games and many other native Linux games:
This seems to get right to the point, try this first- [http://members.shaw.ca/dan.mckay/LokiInst.html](http://members.shaw.ca/dan.mckay/LokiInst.html)
This helps with newer versions of the Loki Update tool and custom installers- [http://www.liflg.org/](http://www.liflg.org/)
This is a nice guide to getting a lot of games working in Linux- see specifically the Loki updater guide- [http://www.easylinuxguide.com/index.php?name=PNphpBB2&file=viewtopic&t=735](http://www.easylinuxguide.com/index.php?name=PNphpBB2&file=viewtopic&t=735)
A nice thread (towards the middle/end) that has a lot of useful tips- [http://www.happypenguin.org/forums/viewtopic.php?t=1493&view=previous&sid=354569bc702f15f8b616f0db512a8921](http://www.happypenguin.org/forums/viewtopic.php?t=1493&view=previous&sid=354569bc702f15f8b616f0db512a8921)  

I suspect that you haven't updated the game, as this seems to be the primary problem seen among Loki gamers. Look around these sites, see if something comes up. Let me know if things don't work out.

-Mike

---

### Post by grendelkhan on 2005-03-28
I skipped the updater and got the patch for eus to work by using the -target=$INSTALLDIR flag - worked like a champ but still segfaults.

What I don't get is it worked fine under Fedora Core 3 and SuSE 9.2, but no dice under Hoary or Componetized Linux (both Debian based).

You tell me what's the diff.

---

### Post by mglukhovsky on 2005-03-28
Just checking: you ran the updates as the user you installed the game from, right?

Also, I would STRONGLY reccommend using the loki update tool from this site:
[http://www.liflg.org/](http://www.liflg.org/)

---

### Post by grendelkhan on 2005-03-29
Yup. Didn't need to under Fedora or SuSE, but I did anyways, just to be safe.

---

### Post by skoal on 2005-04-06
Here are my steps for **SimCity 3000 Unlimited**, which I've used succesfully for at least a year.  It works fine here, running hoary and the latest Nvidia drivers-7174.

1. Insert 'Sim City 3000 Unlimited' (SC3U) CD-Rom.
2. Open up a terminal.
3. cd /media/cdrom
4. sudo sh setup.sh

The installation begins and prompts you for several options.  I used all installation default paths:

/usr/local/games/SC3U
/usr/local/bin

and selected '[Yy]' for every installation option -> ~610 MB.

5. After the installation is done, you are given a prompt:

Would you like launch the game now? [Y/n] n

Answer no.

6. Download the file 'sc3u-2.0a-x86.run' (patch) from:

(i) [ftp://sunsite.auc.dk/pub/os/linux/loki/patches/sc3u/](ftp://sunsite.auc.dk/pub/os/linux/loki/patches/sc3u/)
(ii) [http://www.3ddownloads.com/linuxgames/loki/patches/sc3u/sc3u-2.0a-x86.run](http://www.3ddownloads.com/linuxgames/loki/patches/sc3u/sc3u-2.0a-x86.run)
(iii) or another site hosting this file.

7. Apply the patch file:
```
sudo /bin/bash sc3u-2.0a-x86.run
```
8. Answer a few prompts:

...
Would you like to apply this update? [Y/n]: y
Please enter the installation path: []: /usr/local/games/SC3U

9. Remove the following symlink:
```
sudo rm /usr/local/bin/sc3u

```
10. Replace it with your own shell script:
```
sudo sh -c 'cat > /usr/local/bin/sc3u << EOF
#!/bin/bash
LD_ASSUME_KERNEL=2.4.2 /usr/local/games/SC3U/sc3u
EOF'
```
11. Make it executable:
```
sudo chmod +x /usr/local/bin/sc3u
```
* Type 'sc3u' in a terminal or add this file to a menu entry.

This game never gets old.  Spend several days creating your own little Utopia.  Then, spend several minutes launching wave after wave of UFOs, ushering in the 'New Millenium' on those little 'ants'...

muahahaha...

---

### Post by mike998 on 2005-04-07
I almost started another thread about Sim City 3000 but managed to figure it out - Google was no help whatsoever, but these threads.... the motherload!

THAT'S why I stay with Ubuntu... the community are great, and very helpful...

---

### Post by Avi on 2005-04-08
I've just installed and played **Heroes of Might and Magic 3**  -
Smooth as can be, no problems at all...!

---

### Post by Equinox on 2005-04-08
With a basic install, this is what happens:
```
michael@ubuntu:/opt/cxoffice$ sc3u
sc3u: relocation error: sc3u: symbol _dl_global_scope, version GLIBC_2.0 not defined in file ld-linux.so.2 with link time reference
```

I installed libg++2.8.1.3-glibc2.2 and libstdc++2.10-glibc2.2, but I'm not sure if this is the root of the problem. Just in case, make sure these are installed.

I don't suppose these exist under AMD64? .. I don't see them anywhere in synaptic.

---

### Post by plcdfa on 2005-09-21
Greetings to everyone!

I've got some problems here: I just can't get Simcity's patch to work. It always exits like this:

Uncompressing SimCity 3000 Unlimited 2.0a Updatetrap: usage: trap [-lp] [arg signal_spec ...]

Any ideas what on earth this could mean? It would be important cos I can't start the game, it always halts with the aformentioned "relocation error" thingy, and I've tried all other possible workarounds but none worked. Please help if you can, I remember this game from Win and it's plain fun.

And I can't update Heroes3 either, that one exits with some kind of segfault. I feel like being cursed...  ](*,)

---

### Post by Mishura on 2005-09-23
Loki games that work for me:

Heavy Metal FAKK 2 (Due to LIFLG.org's installer.)
Descent 3 Mercenary
Unreal Tournament 1999 GOTY
Quake III Arena (Hey, it was listed at Loki's website.  More of an Id port, tho)
Soldier of Fortune
Rune:  Halls of Valhalla
Postal GOLD (Thats Postal 1, not the recent Postal 2)

Loki games that Don't work.

Heretic II (Though, somebody here got it to work.  Search the forums.)

---

### Post by Burbruee on 2005-09-25
Unreal Tournament 2004 works just perfect too.

---

### Post by plcdfa on 2005-09-25
OK, I've managed to patch Simcity, I've found the solution in another topic. Maybe  I should have done a bit more reading before posting. :oops: Quite strange though, google didn't reveal that topic. Anyway the game still doesn't work well: after the intro I only get a black screen with a mouse pointer. The building architect runs fine. Have anybody experienced a similar problem with any games?

---

### Post by bodyhead on 2005-10-04
I haven't been able to get alpha centauri to work or update.  I get a bus error with hoary.  Any tips?

---

### Post by bodyhead on 2005-10-04
Ok I've followed the directions on this website::

[http://patrick.wagstrom.net/weblog/linux/ubuntu](http://patrick.wagstrom.net/weblog/linux/ubuntu)

and I managed to install the patch but the damn game still just says 'bus error' when I try to run it from the command line.

Even when I try to trick it with other kernel options.
For anyone who didn't see my previous post, this is the Alpha Centauri game with the expansion packaged by loki.  

I just cannot get it to run.

Any tips are welcome.

---

### Post by jmonteiro on 2005-10-23
The SimCity 3000 Unlimited just worked for me (Ubuntu 5.10), I have some problems in the beggining, but after I patched it and used the "LD_ASSUME_KERNEL"'stuff it just worked!

But I have an problem:

I am brazilian (so I speak Portuguese :P), I would like to use the portuguese locales, but they haven't been installed. Do anybody know how do I install them? Thanks!

---

### Post by luopio on 2005-12-16
[QUOTE=bodyhead]Ok I've followed the directions on this website::

[http://patrick.wagstrom.net/weblog/linux/ubuntu](http://patrick.wagstrom.net/weblog/linux/ubuntu)

and I managed to install the patch but the damn game still just says 'bus error' when I try to run it from the command line.

Even when I try to trick it with other kernel options.
For anyone who didn't see my previous post, this is the Alpha Centauri game with the expansion packaged by loki.  

I just cannot get it to run.

Any tips are welcome.[/QUOTE]
I have the same problem. Installation went fine and I updated the game like instructed here: [http://patrick.wagstrom.net/weblog/linux/ubuntu/alphaCentauri.xml](http://patrick.wagstrom.net/weblog/linux/ubuntu/alphaCentauri.xml). After that it didn't work, so I followed gentoo instructions for old Loki games ([http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games)](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games)). But running ```
LD_PRELOAD=/usr/local/games/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/local/games/Loki_Compat/libsmpeg-0.4.so.0.1.3 smacpack
```
Results in a segmentation fault..

---

### Post by drews_blunted on 2005-12-21
I cannot get sim city 3000 to work in breezy badger 5.10 ? does anyone know why.

i get this error:

BUG!  Exception triggered, cleaning up.
SimCity 3000 Unlimited 2.0.955a
Built with glibc-2.1 on x86
Please send the text of the failed assertion,
along with the contents of autosave to: [email]support@lokigames.com[/email]
Unable to execute loki_qagent - exiting


The game is updated and everything, im also used the LD_ASSUME_KERNEL junk.

---

### Post by bignickel on 2006-12-16
I've followed all of the instructions in this thread to get simcity 3000 working on Edgy.  It's updated and I no longer get the segmentation fault, but now if I run it with this command:

```
LD_ASSUME_KERNEL=2.4.2 /usr/local/games/SC3U/sc3u
```

(or any other kernel < 2.6) I get the following error:

```
/usr/local/games/SC3U/sc3u: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

```

Anyone know where I can get that library?

---

### Post by bignickel on 2006-12-16
Well, I've found some other people with similar problems on newer systems.  Apparently lbdl.so.2 is from an old version of glibc.  Someone got it working on a new version of Fedora Core using some old libraries.  His solution is posted [here]("http://www.fedoraforum.org/forum/archive/index.php/t-118038.html").  I tried using his copies of the old libraries and the game started (I could hear sound) but the video just showed a black screen with the cursor.  I'm not that surprised since those libraries would have been compiled for Fedora.

If anyone has it working I'd really like to hear how.  I can't get the windows version of simcity 3000 to work under wine, and although simcity 4000 works, it's too slow to play.  So getting the native linux version to run is the only hope.

---

### Post by Mapassy on 2006-12-16
The following games worked for me on Dapper:

Railroad Tycoon 2 Gold Edition 
Shogo
Quake 3 - installer + copy and paste .pk3 files
Return to castle Wolfenstein - installer + copy and paste the .pk3 files
Postal 2 Demo
Soldier of Fortune
Heavy Gear 2 - followed this: [http://ubuntuforums.org/showthread.php?p=1106525#post1106525](http://ubuntuforums.org/showthread.php?p=1106525#post1106525)
Rune

---

### Post by Entity` on 2007-11-13
> **skoal said:**
> Here are my steps for **SimCity 3000 Unlimited**, which I've used succesfully for at least a year.  It works fine here, running hoary and the latest Nvidia drivers-7174.

1. Insert 'Sim City 3000 Unlimited' (SC3U) CD-Rom.
2. Open up a terminal.
3. cd /media/cdrom
4. sudo sh setup.sh

The installation begins and prompts you for several options.  I used all installation default paths:

/usr/local/games/SC3U
/usr/local/bin

and selected '[Yy]' for every installation option -> ~610 MB.

5. After the installation is done, you are given a prompt:

Would you like launch the game now? [Y/n] n

Answer no.

6. Download the file 'sc3u-2.0a-x86.run' (patch) from:

(i) [ftp://sunsite.auc.dk/pub/os/linux/loki/patches/sc3u/](ftp://sunsite.auc.dk/pub/os/linux/loki/patches/sc3u/)
(ii) [http://www.3ddownloads.com/linuxgames/loki/patches/sc3u/sc3u-2.0a-x86.run](http://www.3ddownloads.com/linuxgames/loki/patches/sc3u/sc3u-2.0a-x86.run)
(iii) or another site hosting this file.

7. Apply the patch file:
```
sudo /bin/bash sc3u-2.0a-x86.run
```
8. Answer a few prompts:

...
Would you like to apply this update? [Y/n]: y
Please enter the installation path: []: /usr/local/games/SC3U

9. Remove the following symlink:
```
sudo rm /usr/local/bin/sc3u

```
10. Replace it with your own shell script:
```
sudo sh -c 'cat > /usr/local/bin/sc3u << EOF
#!/bin/bash
LD_ASSUME_KERNEL=2.4.2 /usr/local/games/SC3U/sc3u
EOF'
```
11. Make it executable:
```
sudo chmod +x /usr/local/bin/sc3u
```
* Type 'sc3u' in a terminal or add this file to a menu entry.

This game never gets old.  Spend several days creating your own little Utopia.  Then, spend several minutes launching wave after wave of UFOs, ushering in the 'New Millenium' on those little 'ants'...

muahahaha...

Is there any modification of steps for 7.10?  It doesn't seem to work for me.  All I get is:

```
user@user-desktop:~/simcity$ sc3u
/usr/local/games/SC3U/sc3u: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
/usr/local/bin/sc3u: line 3: EOF: command not found

```

I really want to play this game again.  Any help would be of great use to me.

---

### Post by cogadh on 2007-11-13
It would seem that you are missing a required library:
```
error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
```
I would start by fixing that. Search Synaptic for the file, it should be able to find it.

---

### Post by Entity` on 2007-11-13
its not even in synaptic.  However, google did yeild me a debain package [here]("http://packages.debian.org/cgi-bin/search_contents.pl?word=libdl.so.2&searchmode=searchfiles&case=insensitive&version=unstable&arch=i386").

---

### Post by Entity` on 2007-11-13
also libdl.so.2 is already present in my computer. the dir is: /lib/tls/i686/cmov  hmmm.... what to do, what to do...

Edit:  Ah never mind, i just downloaded the wrong package.  However, I still get this:

```
user@user-desktop:~$ sc3u
/usr/local/games/SC3U/sc3u: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
/usr/local/bin/sc3u: line 3: EOF: command not found

```

What do I do?  And whats with the 3rd line thing?:confused:

---

### Post by cogadh on 2007-11-13
Chances are, the second error is related to the first, so fixing the first may eliminate the second. Unfortunately, I'm not in front of my 'buntu box right now, so I can't check for any details on that library on my system. However, one thing that may help is creating a symlink to the libdl.so.2 library in the /usr/local/games/SC3U directory:
```
sudo ln -s /usr/libdl.so.2 /usr/local/games/SC3U/libdl.so.2
```
Like I said, I'm not in front of my 'buntu box, so I can't be sure those paths are 100% accurate, you will need to confirm that yourself.

---

### Post by Entity` on 2007-11-14
The command you gave me worked in the respect that it did not give me an error when I hit enter.  However I still got the same exact answer when I typed 'sc3u'.

---

### Post by Sockerdrickan on 2007-11-16
Closed source apps are begging for death, kind of pathetic :(

---

### Post by Felson on 2007-11-16
@Entity
Are you running 32bit or 64bit ubuntu?
If you are running 64bit, you may need to find lib32 versions of the .so file.

---

### Post by dandy-handy on 2007-11-16
Hey all, I'm having the same problem following all of the advice and try to run the game and the following error occcurs 

/usr/local/games/SC3U/sc3u: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
/usr/local/bin/sc3u: line 3: EOF: command not found

did a quick search of my system and found libdl.so.2 is installed, showing in two locations  /lib  &  /lib/tls/i686/cmov
I'm running 32-bit Ubuntu.  I also ran the command that cogadh suggested 3 posts ago and the same problem continues.

I'm really not quite what else to do, is a shame as Simcity is a great game.

M

---

### Post by cyrus_the_virus on 2007-12-30
Hi everybody,

I've finally got it working :) This how I did it:

- I first followed *mglukhovsky's* tutorial from an earlier topic on this forum
([http://ubuntuforums.org/showthread.php?t=21087&page=1&highlight=sim+city+3000+unlimited]("http://ubuntuforums.org/showthread.php?t=21087&page=1&highlight=sim+city+3000+unlimited"))

- But in the last step I got an error (usr/local/games/SC3U/sc3u: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory)

- I found this page and followed the instructions from that
([http://bashu.wordpress.com/2007/04/15/simcity-3000-on-ubuntu-edgy/]("http://bashu.wordpress.com/2007/04/15/simcity-3000-on-ubuntu-edgy/"))
I extracted the archive in /opt/games/ so I don't have the modify the path in the script. I saved the script in the install path of SC3K (as run.sh)
and gave it exe permission (chmod +x run.sh)

- I was then able to play the game with sh run.sh from the install folder
- However to change the resolution I had to run the game as root:
sudo sh run.sh

Hope this will work for you too!
Marty

---

### Post by paulderol on 2008-01-12
any luck on getting Myth 2 to work under 7.10 and x86? I can't seem to lock down an installer/updater, and i'm getting a little frustrated. all of these pieces of advice change small parts of my problem, but i'm thinking that there's got to be someone who's got myth 2 working.....???eh?

EDIT--nevermind as of yet.

---

### Post by aitvo on 2008-01-13
SC3U works, but not without hacking a custom lib directory (this worked with 7.04 and 7.10)

cd /usr/local/games/SC3U
Move the sc3u binary to sc3u.dynamic, and create a script that points at the original binary called sc3u:

```
#!/bin/bash
SCPATH=/usr/local/games/SC3U
echo Running from $SCPATH
LANG=english
cd $SCPATH
export LD_LIBRARY_PATH=$SCPATH/Loki_Compat/
LD_ASSUME_KERNEL=2.2.5 $SCPATH/Loki_Compat/ld-linux.so.2 $SCPATH/sc3u.dynamic
```

Put these files in /usr/local/games/SC3U/Loki_Compat:

```
-rwxr-xr-x 1 root root  103044 2007-10-19 21:43 ld-linux.so.2
-rwxr-xr-x 1 root root 1549556 2007-10-19 21:43 libc.so.6
-rwxr-xr-x 1 root root   15084 2007-10-19 21:43 libdl.so
lrwxrwxrwx 1 root root       8 2007-10-19 21:43 libdl.so.2 -> libdl.so
-rwxr-xr-x 1 root root  211876 2007-10-19 21:43 libm.so.6
-rwxr-xr-x 1 root root  196716 2007-10-19 21:43 libopenal-0.0.so
-rwxr-xr-x 1 root root  103104 2007-10-19 21:43 libpthread.so.0
-rwxr-xr-x 1 root root  381071 2007-10-19 21:43 libSDL-1.1.so.0
-rwxr-xr-x 1 root root  264557 2007-10-19 21:43 libsmpeg-0.4.so.0
-rwxr-xr-x 1 root root  264557 2007-10-19 21:43 libsmpeg-0.4.so.0.1.3
-rwxr-xr-x 1 root root  264557 2007-10-19 21:43 libsmpeg.so
-rw-r--r-- 1 root root  288540 2007-10-19 21:43 libstdc++-3-libc6.2-2-2.10.0.so
-rw-r--r-- 1 root root  288540 2007-10-19 21:43 libstdc++-libc6.2-2.so.3
-rwxr-xr-x 1 root root  908016 2007-10-19 21:43 libX11.so.6
-rwxr-xr-x 1 root root   53520 2007-10-19 21:43 libXext.so.6
```

Download Loki_Compat.tar.gz here: [http://www.stangdude.com/download.pl?filename=Loki_Compat.tar.gz]("http://www.stangdude.com/download.pl?filename=Loki_Compat.tar.gz")



Run the game by calling ./sc3u

:guitar:

---

### Post by Sockerdrickan on 2008-01-15
robin@PC:/usr/local/games/SC3U$ sh sc3u
/usr/local/games/SC3U/sc3u.dynamic: relocation error: /usr/local/games/SC3U/sc3u.dynamic: symbol _dl_global_scope, version GLIBC_2.0 not defined in file ld-linux.so.2 with link time reference

---

### Post by Sockerdrickan on 2008-01-15
Ok it works now :) thanks, will these libs work with later versions of Ubuntu... it should right?

[http://img47.imageshack.us/img47/7640/sc3kpz7.png](http://img47.imageshack.us/img47/7640/sc3kpz7.png)

---

### Post by aitvo on 2008-01-15
> **Tux0r said:**
> Ok it works now :) thanks, will these libs work with later versions of Ubuntu... it should right?

[http://img47.imageshack.us/img47/7640/sc3kpz7.png](http://img47.imageshack.us/img47/7640/sc3kpz7.png)


Yes, it should. I just created a package out of that which I install whenever I re-roll the OS.

I'd be interested in knowing if it can be modified to work for other Loki games.

---

### Post by ceixeoida on 2008-01-18
Well it doesn't work for me...

```
$ sh sc3u
Running from /usr/local/games/SC3U
/usr/local/games/SC3U/sc3u.dynamic: relocation error: /usr/local/games/SC3U/sc3u.dynamic: symbol _dl_global_scope, version GLIBC_2.0 not defined in file ld-linux.so.2 with link time reference
```

I don't know what's wrong... I did it as you said, but with no results... help, please...

---

### Post by doorknob60 on 2008-01-21
That works for me except I get no sound :'( Any ideas? (I tried starting with aoss but then the game wouldn't even start )

EDIT: My terminal output is this ```
open /dev/dsp: Device or resource busy

``` Also my sound card works fine with both ALSA and OSS.

---

### Post by doorknob60 on 2008-01-21
Never mind, apperantly some program wasn't shut down right or something because sound worked when I restarted...BUT it's scratchy sound :( Any solutions to this one?

---

### Post by skoruppa on 2008-01-22
Yes my to, after changing my oldsoundblaster to hda intel Realtek ALC888 integrated soundcard all loki games have scratchy sound.... someone know why??? I want play heroes3 and sc3000 with normal sound!

---

### Post by skoruppa on 2008-01-23
hah i fixed it :D if someone have also problem with hda intel and loki games, install linux-backports-modules
```
sudo aptitude install linux-backports-modules
```

---

### Post by aitvo on 2008-02-04
> **aitvo said:**
> SC3U works, but not without hacking a custom lib directory (this worked with 7.04 and 7.10)

cd /usr/local/games/SC3U
Move the sc3u binary to sc3u.dynamic, and create a script that points at the original binary called sc3u:

```
#!/bin/bash
SCPATH=/usr/local/games/SC3U
echo Running from $SCPATH
LANG=english
cd $SCPATH
export LD_LIBRARY_PATH=$SCPATH/Loki_Compat/
LD_ASSUME_KERNEL=2.2.5 $SCPATH/Loki_Compat/ld-linux.so.2 $SCPATH/sc3u.dynamic
```

Put these files in /usr/local/games/SC3U/Loki_Compat:

```
-rwxr-xr-x 1 root root  103044 2007-10-19 21:43 ld-linux.so.2
-rwxr-xr-x 1 root root 1549556 2007-10-19 21:43 libc.so.6
-rwxr-xr-x 1 root root   15084 2007-10-19 21:43 libdl.so
lrwxrwxrwx 1 root root       8 2007-10-19 21:43 libdl.so.2 -> libdl.so
-rwxr-xr-x 1 root root  211876 2007-10-19 21:43 libm.so.6
-rwxr-xr-x 1 root root  196716 2007-10-19 21:43 libopenal-0.0.so
-rwxr-xr-x 1 root root  103104 2007-10-19 21:43 libpthread.so.0
-rwxr-xr-x 1 root root  381071 2007-10-19 21:43 libSDL-1.1.so.0
-rwxr-xr-x 1 root root  264557 2007-10-19 21:43 libsmpeg-0.4.so.0
-rwxr-xr-x 1 root root  264557 2007-10-19 21:43 libsmpeg-0.4.so.0.1.3
-rwxr-xr-x 1 root root  264557 2007-10-19 21:43 libsmpeg.so
-rw-r--r-- 1 root root  288540 2007-10-19 21:43 libstdc++-3-libc6.2-2-2.10.0.so
-rw-r--r-- 1 root root  288540 2007-10-19 21:43 libstdc++-libc6.2-2.so.3
-rwxr-xr-x 1 root root  908016 2007-10-19 21:43 libX11.so.6
-rwxr-xr-x 1 root root   53520 2007-10-19 21:43 libXext.so.6
```

Download Loki_Compat.tar.gz here: [http://www.stangdude.com/download.pl?filename=Loki_Compat.tar.gz]("http://www.stangdude.com/download.pl?filename=Loki_Compat.tar.gz")



Run the game by calling ./sc3u

:guitar:


I've created a deb for Gutsy that installs the libraries for you, and another that creates the shell scripts to start SimCity 3000 which is cleaner than extracting the tarball, and hacking the files by hand. It's available here:

[http://www.stangdude.com/news/articles/9035971607236/](http://www.stangdude.com/news/articles/9035971607236/)

---

### Post by -Vampyre- on 2008-02-08
I followed the instructions on your site, and installed all the debs. The games starts and I can hear the music, but my screen just goes black

---

### Post by aitvo on 2008-02-08
I'm actually not sure what would cause a black screen. Are you using Compiz?

---

### Post by -Vampyre- on 2008-02-08
yes i am . that is if I run as root. if I try to just run as me. I get an error i can see

fcntl: Operation not permitted
fcntl: Operation not permitted
X Error:  BadMatch
  Request Major code 140 (XVideo)
  Request Minor code 19 ()
  Error Serial #20
  Current Serial #21
joseph@MiniHQ:~$

---

### Post by -Vampyre- on 2008-02-08
I get the same error if I turn compiz off

---

### Post by aitvo on 2008-02-08
> **-Vampyre- said:**
> yes i am . that is if I run as root. if I try to just run as me. I get an error i can see

fcntl: Operation not permitted
fcntl: Operation not permitted
X Error:  BadMatch
  Request Major code 140 (XVideo)
  Request Minor code 19 ()
  Error Serial #20
  Current Serial #21
joseph@MiniHQ:~$

That looks like a problem with your video driver, or your color depth. I have it working just fine on two computers with different video cards, as a normal user.

Make sure xvinfo returns data, that could cause problems with SC I think.

---

### Post by -Vampyre- on 2008-02-08
Yeah i get info with that command
> X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon Video Overlay"
    number of ports: 1
    port base: 131
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
      depth 24, visualID 0x33
      depth 24, visualID 0x34
      depth 24, visualID 0x35
      depth 24, visualID 0x36
      depth 24, visualID 0x37
      depth 24, visualID 0x38
      depth 24, visualID 0x39
      depth 24, visualID 0x3a
      depth 24, visualID 0x3b
      depth 24, visualID 0x3c
      depth 24, visualID 0x3d
      depth 24, visualID 0x3e
      depth 24, visualID 0x3f
      depth 24, visualID 0x40
      depth 24, visualID 0x41
      depth 24, visualID 0x42
      depth 24, visualID 0x43
      depth 24, visualID 0x44
      depth 24, visualID 0x45
      depth 24, visualID 0x46
      depth 24, visualID 0x47
      depth 24, visualID 0x48
      depth 24, visualID 0x49
      depth 24, visualID 0x4a
      depth 24, visualID 0x4b
      depth 24, visualID 0x4c
      depth 24, visualID 0x4d
      depth 24, visualID 0x4e
      depth 24, visualID 0x4f
      depth 24, visualID 0x50
      depth 24, visualID 0x51
      depth 24, visualID 0x52
      depth 24, visualID 0x53
      depth 24, visualID 0x54
      depth 24, visualID 0x55
      depth 24, visualID 0x56
      depth 24, visualID 0x57
      depth 24, visualID 0x58
      depth 24, visualID 0x59
      depth 24, visualID 0x5a
      depth 24, visualID 0x5b
      depth 24, visualID 0x5c
      depth 24, visualID 0x5d
      depth 24, visualID 0x5e
      depth 24, visualID 0x5f
      depth 24, visualID 0x60
      depth 24, visualID 0x61
      depth 24, visualID 0x62
      depth 24, visualID 0x63
      depth 24, visualID 0x64
      depth 24, visualID 0x65
      depth 24, visualID 0x66
      depth 24, visualID 0x67
      depth 24, visualID 0x68
      depth 24, visualID 0x69
      depth 24, visualID 0x6a
      depth 24, visualID 0x6b
      depth 24, visualID 0x6c
      depth 24, visualID 0x6d
      depth 24, visualID 0x6e
      depth 24, visualID 0x6f
      depth 24, visualID 0x70
      depth 24, visualID 0x71
      depth 24, visualID 0x72
    number of attributes: 12
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_COLORKEY" (range 0 to -1)
              client settable attribute
              client gettable attribute (current value is 30)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)


Thanks for your help

---

### Post by aitvo on 2008-02-08
> **-Vampyre- said:**
> Yeah i get info with that command


Thanks for your help

I'm afraid I can't help you. I just installed it all on a third machine, and it's working ok. I've tested it on the fglrx, vmware, and nvidia drivers.

---

### Post by -Vampyre- on 2008-02-08
tis ok see what i can figure out

---

### Post by -Vampyre- on 2008-02-08
I have read some people having only trouble with the intro. Gonna retry with the intro movie files

---

### Post by -Vampyre- on 2008-02-08
Success. redid and excluded intro and it worked. I also have to turn off compiz

---

### Post by aitvo on 2008-02-08
> **-Vampyre- said:**
> Success. redid and excluded intro and it worked. I also have to turn off compiz

Awesome, good to hear.

---

### Post by aitvo on 2008-02-29
I've gotten Erics Ultimate Solitare working, it wasn't too bad compared to Simcity 3000..

Here's the process:

Download eus-lib.tar [ [HERE]("http://www.stangdude.com/news/articles/12628991215256/") ]
tar -xvf eus-lib.tar
sudo mv libstdc++-libc6.1-1.so.2 /usr/lib

Insert the EUS installation CD

sudo bash /media/cdrom/setup.sh
sudo cp /media/cdrom/bin/x86/EricsSolitaire.dynamic /usr/local/games/EUS/EricsSolitaire.dynamic

Download the EUS 1.0a patch [ [HERE]("http://mirrors.sunsite.dk/lokigames/patches/eus/") ]
sudo bash eus-1.0a-x86.run
sudo ln -sf /usr/local/games/EUS/EricsSolitaire.dynamic /usr/local/bin/eus

Then you can just run eus, or put an icon in your panel for it manually. 

:guitar:

---

### Post by kendricbeachey on 2008-05-31
Does anyone have an alternate source for the files that are supposed to come from stangdude.com?  I am having no luck getting any response from that server.

(Eric's Ultimate Solitaire is the one I'm wanting to get going.)

---

### Post by aitvo on 2008-06-06
> **kendricbeachey said:**
> Does anyone have an alternate source for the files that are supposed to come from stangdude.com?  I am having no luck getting any response from that server.

(Eric's Ultimate Solitaire is the one I'm wanting to get going.)


Sorry, it's been down for a while. I've been migrating from the blog code that I wrote to blogger.

Here's what you are looking for: [http://www.fewt.com/2008/06/get-eus-working-in-ubuntu.html]("http://www.fewt.com/2008/06/get-eus-working-in-ubuntu.html")

---

### Post by ernstblaauw on 2009-05-07
Does anyone has sound in Jaunty with Railroad Tycoon II? (I don't, and I can't get it to work)

---

### Post by fackamato on 2009-05-07
> **ernstblaauw said:**
> Does anyone has sound in Jaunty with Railroad Tycoon II? (I don't, and I can't get it to work)

Railroad Tycoon II?

Is that a game?

Do you use WINE to run it?

If so, then I guess you should use the latest WINE version and ask for help upstream?

:KS

---

### Post by ELD on 2009-05-07
> **fackamato said:**
> Railroad Tycoon II?

Is that a game?

Do you use WINE to run it?

If so, then I guess you should use the latest WINE version and ask for help upstream?

:KS

Yes it is a game a simple googling will tell you that.

This thread is about LOKI games, linux native ports so it will not be using WINE.

---

### Post by dolson on 2010-04-20
> **aitvo said:**
> Sorry, it's been down for a while. I've been migrating from the blog code that I wrote to blogger.

Here's what you are looking for: [http://www.fewt.com/2008/06/get-eus-working-in-ubuntu.html]("http://www.fewt.com/2008/06/get-eus-working-in-ubuntu.html")

This no longer appears to work. :(

Here's what I was getting:

dana@jadis:~$  /usr/local/games/EUS/EricsSolitaire.dynamic
/usr/local/games/EUS/EricsSolitaire.dynamic: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


So then I ran the library update from the LGFAQ, and tried again. Different error:

dana@jadis:~$ eus 

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
EricsSolitaire: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
/usr/local/bin/eus: line 59: 29762 Aborted                 ./EricsSolitaire "$@"

Btw, /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so exists on my system.

If anyone has any tips, please share... I wish it wasn't such a hassle to run older games on Linux.

---

### Post by Perfect Storm on 2010-04-20
Install libgtk1.2

You can find it here; [http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=jaunty&section=all)

---

### Post by rettichschnidi on 2010-04-20
> **dolson said:**
> This no longer appears to work. :(

You could just try my installer: [http://liflg.org/?catid=7&gameid=92](http://liflg.org/?catid=7&gameid=92)

Please report back if it works. Either here or in the liflg forum. Thanks.

---

### Post by dolson on 2010-04-20
> **rettichschnidi said:**
> You could just try my installer: [http://liflg.org/?catid=7&gameid=92](http://liflg.org/?catid=7&gameid=92)

Please report back if it works. Either here or in the liflg forum. Thanks.

I actually just found this myself on google and was coming back here to link to it, because yep, it worked! I am grateful... Best solitaire game ever. :)

---

### Post by rettichschnidi on 2010-04-21
Thanks for reporting. Could you pls tell me also which version of ubuntu you are using? x86 or x86_64?

---

### Post by dolson on 2010-04-27
> **rettichschnidi said:**
> Thanks for reporting. Could you pls tell me also which version of ubuntu you are using? x86 or x86_64?

x86, 10.04 updated daily.

---

### Post by buanzo on 2010-07-25
I'm using fglrx and sof stopped working. I removed the config file and started clean, but no luck.

```

buanzo@murray:~/.loki/sof$ sof
execing default.cfg
execing default_sound.cfg
execing configs/default_keys.cfg
execing default_misc.cfg
execing default_video.cfg
execing menus/reset.cfg
execing config.cfg
----------- Cpu info -----------
Processor : Intel Pentium III and Pentium III Xeon
Type      : Original OEM processor
Speed     : 2348 MHz
Proc ID   : 0000-0000-0000-0000-A760-1000
MMX instructions supported
RDTSC instruction supported
--------------------------------
Using default memory value--use +set cpu_memory <n> to change
65MB of physical memory
Hostname: murray
   IP #1: 127.0.1.1
=== Server Initalization ===
Console initialized.
------- Loading ./ref_gl.so -------
ref_gl version: GL 0.01
Initialzing OpenGL display
... setting mode 3: 640 480 FS
GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon HD 4800 Series          
GL_VERSION: 3.3.9901 Compatibility Profile Context
GL_EXTENSIONS: GL_AMDX_debug_output GL_AMDX_vertex_shader_tessellator GL_AMD_conservative_depth GL_AMD_draw_buffers_blend GL_AMD_name_gen_delete GL_AMD_performance_monitor GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_AMD_texture_cube_map_array GL_AMD_texture_texture4 GL_AMD_vertex_shader_tessellator GL_ARB_blend_func_extended GL_ARB_color_buffer_float GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_snorm GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_buffer GL_EXT_copy_texture GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_buffer_object_rgb32 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_explicit_multisample GL_NV_float_buffer GL_NV_half_float GL_NV_primitive_restart GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays GL_WIN_swap_hint WGL_EXT_swap_control
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
```

Any ideas?

---

### Post by MaximB on 2010-07-26
WOW, this thread begun in 2005, that's 5 years and no necromancy !

---

### Post by z00s on 2010-10-16
Unfortunately in 10.10 sound in these old games isn't working.  The game itself works, but has no sound.  Prior to upgrading to 10.10 I was on 9.10 and the sound worked fine.

Rune's error:

Bound to ALAudio.so
open /dev/dsp: No such file or directory
open /dev/dsp: No such file or directory
Audio initialization failed.

Heretic 2's error:

Initializing SDL sound
Couldn't open SDL audio: No available audio device.

**OK - Found a solution:**

Just open these games with padsp for example:

padsp ./heretic2

padsp ./rune

---

### Post by thewarlock on 2010-12-22
alas, this does not work with Civ:CTP

no luck with sound so far in 10.10 either 32 or 64 bit.


> **z00s said:**
> Unfortunately in 10.10 sound in these old games isn't working.  The game itself works, but has no sound.  Prior to upgrading to 10.10 I was on 9.10 and the sound worked fine.

Rune's error:

Bound to ALAudio.so
open /dev/dsp: No such file or directory
open /dev/dsp: No such file or directory
Audio initialization failed.

Heretic 2's error:

Initializing SDL sound
Couldn't open SDL audio: No available audio device.

**OK - Found a solution:**

Just open these games with padsp for example:

padsp ./heretic2

padsp ./rune

---

