---
title: "Quake2"
date: 2005-03-30
forum: Gaming &amp; Leisure
---

### Post by yusufk on 2005-03-30
To Quote Martin Lawrence from Bad Boys: "Me and this MF aint vibing right now...."

yusuf@AngelDEB:~ $ quake2
QuakeIIForge 0.3
using /home/yusuf/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
oss: buffer size is 16384, 8192 samples
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so") failed: No such file or directory
Refresh failed
Trying mode 0
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so") failed: No such file or directory
SNDDMA_Shutdown
recursive shutdown
Error: Couldn't fall back to software refresh!


Any ideas??

Found this thread, and I'm trying out the recommended fixes....

---

### Post by mike998 on 2005-03-30
Hate to say it, but... 
"This old chestnut... AGAIN??"
I had this problem myself and so did MANY others.  If you get a solution, please post it, I would be very interested in a solution to this problem.

---

### Post by yusufk on 2005-03-31
Eureka!
Problem: 
Seems to need audio driver files
Solution:
Got them from a debian package and copied them to /usr/lib/games/quake2/ 

I've archived and attached all the files (not including any of the subdirectories) that need to be in /usr/lib/games/quake2/ , so that you can just extract it there.

Audio was pretty bad except for when I tried the sdl driver, you need to edit the config file ~/.quake2/baseq2/config.cfg and make sure that the snddriver key is set to sdl, i.e. :
set snddriver "sdl"

That ought to sort things out

I do however get the occasional segmentation fault, but I just re-run it a few times and it works!

---

### Post by tont on 2005-04-17
there is no file ~/.quake2/baseq2/config.cfg ..

---

### Post by yusufk on 2005-04-18
Then create it with just that line :
set snddriver "sdl"

The config file is usually created/updated after the quake2 runs for the 1st time or when settings are changed from within the game, so check after the 1st run whether the snddriver line is still the same.

---

### Post by tont on 2005-04-20
how did you make it to execute oss ?

---

### Post by spiderworm on 2005-04-24
Funny, when I follow these directions, I get the following errors:

------- sound initialization -------
loading sdl sound output driver
load /usr/lib/games/quake2/snd_sdl.so failed: /usr/lib/games/quake2/snd_sdl.so: cannot open shared object file: No such file or directory
------- Loading ref_glx.so -------
LoadLibrary("ref_glx.so") failed: /usr/lib/games/quake2/ref_glx.so: cannot open shared object file: No such file or directory
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so") failed: /usr/lib/games/quake2/ref_softx.so: cannot open shared object file: No such file or directory
Refresh failed
recursive shutdown
Error: Couldn't fall back to software refresh!

It says the files aren't in the directory, and yet I'm staring right at them!  They're there!

user@host:~$ ls -l /usr/lib/games/quake2/
total 1452
drwxr-xr-x  4 root root   4096 2005-04-24 07:04 baseq2
drwxr-xr-x  2 root root   4096 2005-04-24 07:04 ctf
-rw-r--r--  1 root root    868 2005-04-24 07:33 ref_glx.la
**-rw-r--r--  1 root root 276976 2005-04-24 07:33 ref_glx.so**
-rw-r--r--  1 root root    878 2005-04-24 07:33 ref_sdlgl.la
-rw-r--r--  1 root root 245904 2005-04-24 07:33 ref_sdlgl.so
-rw-r--r--  1 root root    805 2005-04-24 07:33 ref_soft.la
-rw-r--r--  1 root root    885 2005-04-24 07:33 ref_softsdl.la
-rw-r--r--  1 root root 196624 2005-04-24 07:33 ref_softsdl.so
-rw-r--r--  1 root root 189040 2005-04-24 07:33 ref_soft.so
-rw-r--r--  1 root root    875 2005-04-24 07:33 ref_softx.la
**-rw-r--r--  1 root root 216304 2005-04-24 07:33 ref_softx.so**
-rw-r--r--  1 root root    805 2005-04-24 07:33 ref_tdfx.la
-rw-r--r--  1 root root 237648 2005-04-24 07:33 ref_tdfx.so
-rw-r--r--  1 root root    840 2005-04-24 07:33 snd_alsa.la
-rw-r--r--  1 root root   7124 2005-04-24 07:33 snd_alsa.so
-rw-r--r--  1 root root    820 2005-04-24 07:33 snd_ao.la
-rw-r--r--  1 root root   5696 2005-04-24 07:33 snd_ao.so
-rw-r--r--  1 root root    793 2005-04-24 07:33 snd_oss.la
-rw-r--r--  1 root root   7088 2005-04-24 07:33 snd_oss.so
-rw-r--r--  1 root root    861 2005-04-24 07:33 snd_sdl.la
**-rw-r--r--  1 root root   5040 2005-04-24 07:33 snd_sdl.so**

What the hell am I doing wrong???

spiderworm

---

### Post by nautilus on 2005-04-25
Are you guys using the official Q2 source or binaries?

You're lucky, as it happens I'm a developer of Quake2 :D

---

### Post by ducko on 2005-04-25
Hello fellow human beings!

For two days I've been trying to find a way to install quake2 but no go! Is there something fundamental I'm missing: I've tried to install it from ubuntu universe and debian repositories without success:

...

QuakeIIForge 0.3
using /home/ducko/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok

then system hangs!!
...

What is the best method proven to succeed? From binaries or with Lokigames installer or ... ? And where to put the data files from the original CDs?

Thanks!
-ducko

---

### Post by Wardhog on 2005-04-27
[QUOTE=ducko]

------- sound initialization -------
loading oss sound output driver, ok

then system hangs!!
...

[/QUOTE]

I'm not 100% certain it's the same issue I had with Quake3, have you tried killing esd before starting Quake2?

killall esd
./quake2
esd &

Quake 3 would hang on startup if esd was running.  Try killing it first.

Edit : I installed Quake 2 last night and hit the same problem as you.  I then followed my own advice (killall esd) and now have the problem the original poster had.

---

### Post by Maniak on 2005-04-28
Perhaps the Unofficial Ubuntu 5.04 Starter Guide ( [http://www.ubuntuguide.org](http://www.ubuntuguide.org) ), with its section on fixing the sound issues will help. I am going to do that before getting my copy of Quake 2 back out.

---

### Post by yusufk on 2005-04-29
[QUOTE=nautilus]Are you guys using the official Q2 source or binaries?

You're lucky, as it happens I'm a developer of Quake2 :D[/QUOTE]


Interesting! Using the Ubuntu Q2 binary package, with missing files from the debian q2 package.

---

### Post by ducko on 2005-05-02
Hi!

I tried to killall esd but without success - it still crashes. I don't know how people have managed to install it. Do I have to install from sources or with loki installer etc.? There's so much voodoo in this thing. Is QII so rare/old that people don't install it anymore or why there's so little info about it?

-ducko

---

### Post by Wardhog on 2005-05-03
[QUOTE=ducko]Hi!

I tried to killall esd but without success - it still crashes. I don't know how people have managed to install it. Do I have to install from sources or with loki installer etc.? There's so much voodoo in this thing. Is QII so rare/old that people don't install it anymore or why there's so little info about it?

-ducko[/QUOTE]
 Is it still crashing at the same point, or getting a little further?  
When I tried the killall esd, I noticed q2 would get slightly further in its startup before crapping out, it looked the same as the original post.

I wound up installing the Windows version under Cedega and it works fine.  I didn't have the attention span to get the Ubuntu packaged q2 going.  I needed a fix of q2.

---

### Post by ducko on 2005-05-04
Hi!

Yes - it did proceed a bit further but ended to the same errors as you mentioned.

-ducko

---

### Post by ducko on 2005-05-04
Wardhog,

Forgot to ask in the previous message which version of cedega you used - free or paid?

-ducko

---

### Post by Wardhog on 2005-05-04
[QUOTE=ducko]Wardhog,

Forgot to ask in the previous message which version of cedega you used - free or paid?

-ducko[/QUOTE]

Cedega 4.3.1, I think.  It's the paid version.

---

### Post by NightwishFreak on 2005-05-05
[QUOTE=Wardhog]I'm not 100% certain it's the same issue I had with Quake3, have you tried killing esd before starting Quake2?

killall esd
./quake2
esd &

Quake 3 would hang on startup if esd was running.  Try killing it first.

Edit : I installed Quake 2 last night and hit the same problem as you.  I then followed my own advice (killall esd) and now have the problem the original poster had.[/QUOTE]
I had the same problem with Quake 3, and killing esd fixed'er up! thanks.

---

### Post by reuben on 2005-05-07
I have the same problem as Spiderworm. Running AMD64, perhaps that makes a difference?

---

### Post by liberal_tugboat on 2005-05-23
I downloaded the zip file the OP posted and moved the file it was hanging on over to the quake2 directory as he said and it booted up just fine.
only problem I have now is it wont save any settings when I try to configure anything
Im guessing its a permissions problem but I will figure it out
:)

---

### Post by liberal_tugboat on 2005-05-23
ok got everything working great...
I copied all the files from the zip provided on the first page... now I have full sound and full glx
to get the settings to stick I went into the config file in ~/.quake2/baseq2/ and changed to permissions to 777 (read write execute for everyone...) and now everything works great- Full screen 1280-1024 full sound (kill esd first)
I played the first few levels... Now I remeber how fricking awesome of a game this is!
I think I will write a how to later to help everyone out
 \\:D/

---

### Post by spiderworm on 2005-05-29
[QUOTE=reuben]I have the same problem as Spiderworm. Running AMD64, perhaps that makes a difference?[/QUOTE]

Reuben, we're both running 64 bit.  This probably has something to do with what's going on.  I'm still not able to get it to work.

---

### Post by nautilus on 2005-06-02
If you're using the ATI fglrx drivers, you may need to move your 64-bit DRI library out of the way:

mv /usr/X11R6/lib64/modules/dri/fglrx_dri.so /usr/X11R6/lib64/modules/dri/fglrx_dri.so.amd64

then, use the 32-bit one:

cp /usr/X11R6/lib/modules/dri/fglrx_dri.so /usr/X11R6/lib64/modules/dri/fglrx_dri.so

Or, alternatively, recompile Quake2 for AMD64, quite simply, which will then use the 64-bit GLX/DRI libraries (the best choice).

Then again, I could be wrong, but give it a try.

If it doesn't work, just move the AMD64 version back into place.

---

### Post by Dissem Faé on 2005-07-16
For those of you whom yusufk's file didn't help: You might try to chmod a+x the .so and .la files in /usr/lib/games/quake2. There seems to be some problems with those rights in some packages, e.g. Java needed this too for making the bowser plugins work.
I understand that those packages aren't part of the official Ubuntu distro, but I had some better experience with Gentoo ebuilds than I have with some of those packages lately. :-(

---

### Post by c-m on 2005-08-10
i've tried everything in the thread mine still doesn't load, here is the ouput:

> 
carl@ubuntu:~$ quake2
QuakeIIForge 0.3
using /home/carl/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
oss: buffer size is 16384, 8192 samples
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
SNDDMA_Shutdown
recursive shutdown
Error: Couldn't load pics/colormap.pcx
carl@ubuntu:~$




---

### Post by olivierp on 2005-08-14
[QUOTE=c-m]i've tried everything in the thread mine still doesn't load, here is the ouput:[/QUOTE]

- Open a shell
- sudo dpkg-reconfigure quake2-data

---

### Post by hammett111 on 2005-08-14
[QUOTE=spiderworm]Reuben, we're both running 64 bit.  This probably has something to do with what's going on.  I'm still not able to get it to work.[/QUOTE]

Spiderworm and Rueben I have compiled a 64bit version of quake2 with a "tweaked" x64_amd64 binary file and start script. I am running the game now and its awesome under 64bit, but I need testers to iron out any bugs that may creep in. Are you two game? Its only the demo levels at the mo' but you can put the full version pak files in the baseq folder and run the full version.

Reply to this thread, personal message or email me at [email]hammett@xtra.co.nz[/email] if you are interested. I also need another guinea pig if you can find a 64bitter willing,

Cheers

---

### Post by spiderworm on 2005-08-15
[QUOTE=hammett111]Spiderworm and Rueben I have compiled a 64bit version of quake2 with a "tweaked" x64_amd64 binary file and start script. I am running the game now and its awesome under 64bit, but I need testers to iron out any bugs that may creep in. Are you two game? Its only the demo levels at the mo' but you can put the full version pak files in the baseq folder and run the full version.[/QUOTE]

I'm in.  You can send me more information at [email]david@tellim.com[/email]

---

### Post by dakilla on 2005-09-21
hi all!! 
i got the same problem as c-m
are there any solution?

> QuakeIIForge 0.3
using /home/dakilla/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading sdl sound output driver, ok
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx 

please help!! 
and thanks for the nice support :)

---

### Post by User-007 on 2005-09-21
You need an original Windows CD or Quake2 shareware package to run that. Be sure that you have wget installed and run 

sudo dpkg-reconfigure quake2-data

And then you are asked to select whether you want to use the original CD or download shareware from the net. If you don't have an original copy, then only select you want to download and that's all. Hope this helps!

Pate

---

### Post by cry0 on 2005-10-12
I had the same problem that everyone had, but to me killing esd worked... but now the sound is lousy :-/
Is there any way to get through this?

And btw... I cannot run it fullscreen. Is this a normal thing to happen?

Tks

---

### Post by SupImMike on 2006-01-24
mine uses default.cfg (and if not found uses config.cfg) - so to remove an error line you might want to put it in there... (not sure if that messes up in game setting changes)

mine installed to /user/local/lib/games/quake2

Mine seems to work

From the README file: 
"If, when you start the game, you get an error that pics/colormap.pcx cannot be found, it means that pak0.pak is not in the game data path."

Also I have a question: 
- I will only be playing action quake 2 (i dont like single player or other versions of the multiplayer) - Do I need to have the games .pak files in there? or can i just put the action quake files there?

[QUOTE=yusufk]Eureka!
Problem: 
Seems to need audio driver files
Solution:
Got them from a debian package and copied them to /usr/lib/games/quake2/ 

I've archived and attached all the files (not including any of the subdirectories) that need to be in /usr/lib/games/quake2/ , so that you can just extract it there.

Audio was pretty bad except for when I tried the sdl driver, you need to edit the config file ~/.quake2/baseq2/config.cfg and make sure that the snddriver key is set to sdl, i.e. :
set snddriver "sdl"

That ought to sort things out

I do however get the occasional segmentation fault, but I just re-run it a few times and it works![/QUOTE]

---

### Post by SupImMike on 2006-01-24
[QUOTE=c-m]i've tried everything in the thread mine still doesn't load, here is the ouput:[/QUOTE]

this is because you need your *.pak files from your quake 2 cd.

---

### Post by BLTicklemonster on 2007-12-23
Wow. My old friend Q2. I had no idea that there was a loader for linux. Thanks for the dpkg tip, this is great!

---

