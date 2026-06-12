---
title: "Dwarf Fortress has gone linux native"
date: 2008-12-29
forum: Gaming &amp; Leisure
---

### Post by juanoleso on 2008-12-29
The maker of Dwarf Fortress has released a linux native port:

The [[COLOR="Blue"]Dev log[/COLOR]]("http://www.bay12games.com/dwarves/dev_now.html") has links to the forums and the program.

If you haven't tried dwarf fortress, it is a complex social sim where dwarves try to eek out a living and fend off nature and goblins by digging a fortress into a mountain.  The UI is rough around the edges, but once that is overcome the game is fantastic.

You can use your imagination to:
-Build your fortress inside volcano calderas
-catch dragons and trap goblins and force them to fight in arenas
-filter the ocean to catch mer-people and then slaughter their offspring to make bone totems to sell to traders
-pump water into your Dining Hall to make a recurrsive waterfall

Dwarf Fortress is still in alpha stages and the creator is constantly making changes.  Donations are requested.

---

### Post by Handyman Felting on 2008-12-29
Fantastic news! I've been looking forward to this for months.

---

### Post by juanoleso on 2008-12-31
Just one bump.

I would just like to give this game the attention it deserves and try and spread the word.

---

### Post by donkyhotay on 2008-12-31
Sweet, a friend of mine was showing it to me on his mac the other day. I really wish it was FOSS (I would love to look at the code behind it) but non-FOSS native linux is good nonetheless.

---

### Post by Vadi on 2008-12-31
Thanks for the bump, I'll check it out.

---

### Post by fiddler616 on 2009-01-06
Brilliant, KMandla just finished raving about it [here]("http://kmandla.wordpress.com/2009/01/05/the-rebirth-of-the-uncool/"), and only posted the Crux install script (or something(?) (Crux is not my forte)). I was forseeing having to boot up XP just to try it out, but a quick Google turned up this thread. Thank you.

---

### Post by fiddler616 on 2009-01-06
(Oh, while I'm here, there's a more recent version on the Jan 4th entry of the log linked to above (I couldn't figure out the permalinking myself))

---

### Post by binbash on 2009-01-06
I am gonna try it out, thanks

---

### Post by Zeroberry on 2009-01-06
Sounds awesome.

---

### Post by GoS_ on 2009-01-06
Finally!  Literally yesterday I was wishing that this game would be ported to Linux, and apparently it already had.  Thanks you for posting this.  Well, here's one less reason to use Windows.

---

### Post by Sockbag on 2009-01-09
Joined the forums to bump this.
Great game

---

### Post by Anthon berg on 2009-01-12
Dwarf Fortress messes with your emotions, just like a good novel.

When I first saw it, I thought it was a lame ASCII game by dorks. Then I played it. It took a week to learn, and I came to the conclusion that it was a military-grade dwarf simulator.

Now, however, my opinion is that it is a narrative generator the size of a small God.

---

### Post by Dedoimedo on 2009-01-12
Looks interesting ... will be checking it.
Cheers,
Dedoimedo

---

### Post by juanoleso on 2009-01-12
> **Anthon berg said:**
> Dwarf Fortress messes with your emotions, just like a good novel.

When I first saw it, I thought it was a lame ASCII game by dorks. Then I played it. It took a week to learn, and I came to the conclusion that it was a military-grade dwarf simulator.

Now, however, my opinion is that it is a narrative generator the size of a small God.

/agree

To anybody interested there are graphics packs available that replace the ASCII into something more readable, but I personally do not use them.  The [[COLOR="Blue"]DF wiki[/COLOR]]("http://dwarf.lendemaindeveille.com/index.php/Main_Page") has good info on how to start and run a fortress as well as how to install those graphics packs.

I started reading the DF forums a little while after playing and some of the stories that people have put up about their fort are just heart wrenching.  I kid you not, there are stories about dwarves wandering aimlessly around forts after their eyes being plucked out by dragons and stories of dwarves beating their spouses (going both directions) after children drowning [[COLOR="Blue"]("Most depressing sight?" thread on DF forums)[/COLOR]]("http://www.bay12games.com/forum/index.php?topic=19445.0").

---

### Post by ziwerliz on 2009-02-18
Re: How to define LD_LIBRARY_PATH for all applications
can someone who is more tech experienced help me?
I get this message when i try to start DF
Code:

./df
./dwarfort.exe: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

I am running ubuntu 8.10 64-bit with Nvidia dirver 180.11

thanks in advance

---

### Post by juanoleso on 2009-02-18
Make sure you have SDL installed.  In synaptic search for libsdl and install it.  Here is something else:

[URL="http://www.bay12games.com/forum/index.php?topic=28841.msg387702#msg387702"] 	
[COLOR="Blue"]Re: Future of the fort: Help test the output code for the next version of DF
« Reply #724 on: January 09, 2009, 11:29:01 PM »[/COLOR][/URL]

From what I read you may need to get the 32 bit versions of SDL?  Read the forum thread from there and then maybe try replying to the thread with your problem.  The thread is still active and someone might be able to help.

---

### Post by ziwerliz on 2009-02-19
Thanks juanoleso i did follow your link. it gave some clues
  
- you need 32bit libs for df (not 64) 

I solved this by installing [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") then i ```
getlibs -l libSDL-1.2.so.0 libSDL_image-1.2.so.0 libaa.so.1 libslang.so.2 libgpm.so.2 

```
now df works thx! :D 
thou i get this kind of message when i start df
```
./df
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
Using OpenGL output path with client-side arrays
Ideal catalog size: 252x248

```

---

### Post by KhaaL on 2009-02-19
Awesome! this is the best roguelike avaible. The only thing its lacking is a better documentation or a tutorial to new players.

---

### Post by donkyhotay on 2009-02-19
> **KhaaL said:**
> Awesome! this is the best roguelike avaible. The only thing its lacking is a better documentation or a tutorial to new players.

You really need someone who's played the game before to sit at the computer with you and guide you through your first year or two. Either that or *alot* of patience as you figure stuff out yourself.

---

### Post by Bios Element on 2009-03-08
Use the Dwarf Fortress Wiki...And these great video guides. [http://www.bay12games.com/forum/index.php?topic=28477.0](http://www.bay12games.com/forum/index.php?topic=28477.0)

---

### Post by zorkerz on 2009-03-15
So im a bit confused. There is no linux download in the downloads area. The first post links to the recent developments section. There you can find a link to download the linux version. Currently the newest is from 01/09/2009 which is version df_28_181_40d9. The newest version on the main download page (again not linux option here) is df_28_181_40. 

So I'm assuming the downloads in the development section are not stable releases but why is there no stable linux release under the downloads section? Is it because the linux port is so new?

Ok so I looked into this a bit before posting. In the development section logs from previous years the first linux mention occurs on 12/22/2008. There a link is provided and thanks to Bernard Heyler for the linux port. 

So I guess this mostly clears up my confusion. Any word on how stable the linux version is vs the windows one in wine? I will go for the linux first because that is much preferable. Also any idea why the linux version is not on the download page.

---

### Post by psilocybin2 on 2009-03-15
cool thanks for update

---

### Post by juanoleso on 2009-03-16
I use the linux version and it seems to be just as stable.  I don't know why he hasn't put a link on the front page except that the linux version was created some time after the .40 windows/mac release.  I imagine he will update the front page with the next release which is still months away.

One caveat/clarification, though, it is still alpha which indicates "not stable enough for everyday use," but I have not been able to crash the game the months I have been playing it.  There is a setting in the init.ini that makes the game save each year/season automatically and this setting is recommended for now.

---

### Post by zorkerz on 2009-03-16
sounds great thanks for the info. Now I just need some free time to give it a whirl.

---

### Post by zorkerz on 2009-03-18
So I found some time to finally give dwarf fortress a shot. Unfortunately I did not make it very far. Ive extracted the game into a folder named dwarfort. In a terminal when I run the df regardless of whether I have CDed into the dwarfort directory I get this error.

```
/home/data/games/dwarfort/df: 5: ./dwarfort.exe: not found
```

I don't know what to do at this point. First I'm a bit confused as to why it is trying to use a .exe file. I don't have wine installed and are talking about running it native in linux but no one else here seems to have had a problem with this so I imagine its alright.

The other issue that I think may come into play here is that this is an x86-64 ubuntu install. I realize I have no idea whether dwarf fortress can run on 64 bit systems.

So any ideas? What can I do?

---

### Post by juanoleso on 2009-03-19
For whatever reason the "df" script can't find the "dwarfort.exe" file (dwarfort.exe is kind of a misnomer as it won't run in wine or windows compiled as it is for linux but it is the binary program in this case).  "dwarfort.exe" needs to be in the same folder as the "df" script.  Could the zip file have been corrupted when you dl'd it?

As for the 64-bit OS you should look at the previous page of this thread posts 15-17 if you have trouble.  They have a link to the DF forums.

---

### Post by jahred on 2009-03-19
not sure if this is the exact problem you described, but dwarfort.exe is not on your path by default, so you'll have to type the entire location of the file.  i.e.,

```

jahred@jahred-vaio:~/df/df_linux$ ~/df/df_linux/dwarfort.exe

```

i'm having a problem running it myself; 

```

jahred@jahred-vaio:~/df/df_linux$ ~/df/df_linux/dwarfort.exe
/home/jahred/df/df_linux/dwarfort.exe: error while loading shared libraries: libfmodex.so: cannot open shared object file: No such file or directory

```

i have the sdl libraries installed.  i tried using the getlibs package that someone suggested earlier, but still no luck

```

jahred@jahred-vaio:~/df/df_linux$ getlibs ~/df/df_linux/dwarfort.exe
No match for libfmodex.so

```

anyone have any ideas?

EDIT:
i realized i had to install fmod, fixed and working great.

---

### Post by juanoleso on 2009-03-19
For that I do know and I think I know what is going on here.  I'm pretty sure you must be in the same folder that the dwarfort.exe file is in.  Then you need to run the "df" script from there.

(i.e.)

```
noleson@tty1093vm:~$ ~/Desktop/df_linux/df
/home/noleson/Desktop/df_linux/df: 5: ./dwarfort.exe: not found
noleson@tty1093vm:~$ ~/Desktop/df_linux/dwarfort.exe 
/home/noleson/Desktop/df_linux/dwarfort.exe: error while loading shared libraries: libfmodex.so: cannot open shared object file: No such file or directory
```

you must:

```

noleson@tty1093vm:~$ cd Desktop/df_linux/
noleson@tty1093vm:~/Desktop/df_linux$ ./df
```

---

### Post by zorkerz on 2009-03-19
I downloaded the df linux files from the dev page again and am still getting the dwarfort.exe not found error regardless of whether I run df from the dwarfort.exe folder or not.

For running an an x86-64 system what packages precisely do I need to install?

I followed the link to the df forums, there it appears I should install ia32-libs and ia32-libs-gtk from the repositories. Also a 32bit version of libsdl. I have not found any package libsdl however there are many that start with this and have a longer name.


ziwerliz above said he needed to install from getlibs  libSDL-1.2.so.0 libSDL_image-1.2.so.0 libaa.so.1 libslang.so.2 libgpm.so.2

---

### Post by juanoleso on 2009-03-19
Well...as a work around, you could open the /df_linux/libs folder and copy as root the files "libfmodex.so" and "libgcc_s.so.1" to your /usr/lib folder and then make sure the permissions on those files lets everyone read them.  Then you should be able to just:

```

noleson@tty1093vm:~$ cd Desktop/df_linux/
noleson@tty1093vm:~/Desktop/df_linux$ ./dwarfort.exe
```

if it still comes up with the cannot find error, then its just that.  The file is missing or renamed or something.  If you want to work on it, would you please do an "ls" on your df_linux folder and then copy the output here?

```

noleson@tty1093vm:~/Desktop/df_linux$ ls
command line.txt  dwarfort.exe      libs          readme.txt
data              file changes.txt  raw           release notes.txt
df                gamelog.txt       README.linux  sdl
noleson@tty1093vm:~/Desktop/df_linux$
```

---

### Post by grfwoot on 2009-05-03
Hi there ;) 
I recently discovered this game,and i thought it was some shitty ascii ugly work...but i was bored...realy bored,bored of all this 3D graphics,of all this recent games...so i tested it !
But...but...but...!!!
If i press the cap key ("majuscule", "cap",mmmh dunno how do english call that realy...the key right down capslock and right up Fn (for me it's Fn,maybe some have Ctrl)) the game crashes...so i cannot use a lot of vital functions !!!
I seeked google all around...can't find any information...the only thing i found is in the df script :
```
export SDL_DISABLE_LOCK_KEYS=1 # Work around for bug in Debian/Ubuntu SDL patch.
```Turning it off doesn't changes anything ...

any sugestion ? thanks in advance for help =)




G N U :guitar:

---

### Post by zorkerz on 2009-05-03
I can't help with your problem but I think the key you are describing is the Shift key. Its below capslock and above fn and also above ctrl (at least on my keyboard). It make letters upper case just like caplock except you need to hold it down. Is that right?

---

### Post by grfwoot on 2009-05-03
yep that's it ^^ Shift key... And with that new word in google...nothing more...

Seems that it's a SDL bug...but i realy don't know anything about SDL,i just programmed a few SDL games some years ago...

Thanks for help :)




G N U :guitar:

---

### Post by grfwoot on 2009-05-03
The console log says :
```
 /usr/lib/libexpat.so.1.5.2./df: line 5: 28187 Abandon                 ./dwarfort.exe $
```Notice that it's the same with other keys (Ctrl and Alt...)
I'm stuck here... If anyone has an answer it'd be nice =)

Thanks in advance ! =)




G N U :guitar:

---

### Post by boonshanka on 2009-07-12
can join me and some dwarf fortress players on irc at za.atrum.org on #dwarf_fortress_sa :) share tips and tricks too (I'm somewhat of an expert already lol)

---

### Post by personjerry on 2009-09-03
I have an error when running native linux version of 40d16, thought I'd post it in both forums. From the df forum [http://www.bay12games.com/forum/index.php?topic=40349.msg741727#msg741727](http://www.bay12games.com/forum/index.php?topic=40349.msg741727#msg741727):



error running 40d16:

[abc@abc-system]@file:/df.16$ ./df -sound_output ALSA
mkdir: cannot create directory `unused_libs': File exists
mv: cannot stat `libs/libSDL*': No such file or directory
Segmentation fault
[abc@abc-system]@file:/df.16$

On the other hand, my 40d15 (i think that's the version, it might be earlier) still works. Good thing I didn't delete it. Any workarounds?

EDIT: From the previous version working and the fact that I'm a developer who works with SDL/OpenGL, yes I have those libraries installed.

I am running Ubuntu Linux 9.04, 32 bit edition.

Strangely, the 40d16 works if I download the Windows version and use WINE.


EDIT: Found a fix... very strange, it works if I just run using this command:

./df ./libs

---

