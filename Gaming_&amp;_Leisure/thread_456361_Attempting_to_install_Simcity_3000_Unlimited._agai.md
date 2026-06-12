---
title: "Attempting to install Simcity 3000 Unlimited. again. w/ stupid Loki glibc problems"
date: 2007-05-27
forum: Gaming &amp; Leisure
---

### Post by Limitlesschannels on 2007-05-27
Alright, I have ran searches throughout this forum and come up with mixed results all over about attempting to install old Loki games and running into glibc issues.  None of these threads have really helped me at all and are just really confusing.  This link seems to have the closest thing to an answer for what I am trying to do, but I still have no idea what it is talking about; plus, it is for gentoo and i don't know if the command syntax should be different.
[http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games#Sim_City_3000](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games#Sim_City_3000)

I am attempting to install Simcity 3000 Unlimited.  when i mount it and run 
```
 sh setup.sh
```
in the working directory, i get 
```

This installation doesn't support glibc-2.1 on Linux / x86

Please contact Loki Technical Support at support@lokigames.com

```

So, apparently I need to trick the system into using an old version of glibc with "LD_LIBRARY_PATH"...?  I heard mentions of using "LD_ASSUME_KERNEL=2.4.26" to run it as an old kernel version.

I thought myself to be fairly competent with Linux but it is just one of those annoying things about Linux that if you are infamiliar with a command, then you are totally screwed unless there are some ubuntu-gurus around to help out.  So, if anyone can shed some light on LD_ASSUME_KERNEL or let me know if that's even the right way to go about this, then please let me know.

---

### Post by Stephen Howard on 2007-05-27
You're on the right track according to this Gentoo wiki on [running old loki games]("http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games").  

Basically you need to install the old libraries, and then point LD_LIBRARY_PATH to that directory.  If you have any luck, please post because I'd be interested.

---

### Post by Limitlesschannels on 2007-05-28
I'm sorry, could you be more specific?  What libraries do i need to install and how do i use LD_LIBRARY_PATH?

---

### Post by Stephen Howard on 2007-05-28
I can't help much as I've not tried it myself - I'm just passing on the gist of the gentoo link.  It seems that you need to get the pre-packaged old libraries that the author of the gentoo site has put together; then drop those files in a local directory; then each time you run the  loki game define the LD_LIBRARY_PATH variable to point at the old libraries directory.  The website has the specific instructions for each loki game - including simcity.

---

### Post by Limitlesschannels on 2007-05-29
Hm, well, i downloaded the prepackaged libraries and all that, followed the onsite instructions and ran:

the site says to use:

```

LD_LIBRARY_PATH=/path/Loki_Compat/ /path/Loki_Compat/ld-linux.so.2 /path/SimCity3000/sc3u.dynamic

```

for the game, so i tried: 

```

limitlesschannels@Compy:~/Desktop$ LD_LIBRARY_PATH=~/Desktop/Loki_Compat/ ~/Desktop/Loki_Compat/ld-linux.so.2 /media/cdrom0/setup.sh
/media/cdrom0/setup.sh: error while loading shared libraries: /media/cdrom0/setup.sh: invalid ELF header

```
substituting the "path" for whichever path is required.  I have no idea what an "invalid ELF header" error is and google wasn't much help.  I assume the main problem is that I am attempting an install while the page says at the top that the installation and patching of the games is not covered and these commands are for actually running the game.  But i can't even seem to get it installed properly to try running it.  ugh.

---

### Post by Stephen Howard on 2007-05-29
Okay, I did some research and the following works on my Feisty installation [COLOR="Red"](thanks to uth at the [Fedora forum]("http://www.fedoraforum.org/forum/archive/index.php/t-118038.html"))[/COLOR]:

[INDENT]Step 1:   Grab this bundle of loki compatibility files: [http://www.linuxrising.org/files/lokicompat.tar.bz2](http://www.linuxrising.org/files/lokicompat.tar.bz2).  Note that the gentoo loki compatibility files won't work, but these FC5 versions do work.

Step 2:   Extract the files into your loki compatiblilty directory (I have mine at /usr/local/games/loki_compat_libs/).

Step 3:   Bring up a terminal and type the following:

> export COMPAT=/usr/local/games/loki_compat_libs/      # your path will probably be different                                 
export LD_LIBRARY_PATH=$COMPAT


Step 4:   Then to run the game type:

> LD_ASSUME_KERNEL=2.2.5 $COMPAT/ld-linux.so.2 sc3u      



Step 5:    Once you exit the game, you'll need to reset the LIBRARY PATH (this is important):

> unset LD_LIBRARY_PATH 


Step 6:  Presumably you could put the above in a script once you verify that its working.[/INDENT]

---

### Post by Stephen Howard on 2007-05-29
Oops, I just noticed that you're actually trying to install simcity - maybe try [Iculus' installer]("http://www.icculus.org/loki_setup/").

---

### Post by Limitlesschannels on 2007-05-29
I try and download the various loki-installer/patches/setups off icculus' site, but it just drops me to a CVS listing and either the files are no longer there or are deep down in the bowels.  I tried [http://www.liflg.org/?catid=4](http://www.liflg.org/?catid=4) but the simcity game looks like it is the only loki game without an installer on that site.  Any other suggestions?

---

### Post by seditiousmonkey on 2007-07-02
I too am having trouble with Sc3u and this annoying glibc thingy.  Stephen i followed your hints which must have done somthing but on executing

> joe@joe-desktop:/usr/local/games/SC3U$ LD_ASSUME_KERNEL=2.2.4 $COMPAT/ld-linux.so.2 sc3u

i now get 

> SC3U: error while loading shared libraries: SC3U: cannot open shared object file: No such file or directory
now the error reads 

any ideas what this means?

---

### Post by Slammer64 on 2007-07-02
Are you using x86_64, if so, that could be the cause of your problem?  If that's so use the command "linux32 ./setup.sh". It's how I have got it running. I have lots of Loki games already installed and am willing to help anyone who plays these old classics.

---

### Post by seditiousmonkey on 2007-07-03
i think im going around in cirlces now i get 
> /usr/local/games/SC3U/sc3u: error while loading shared libraries: /usr/local/games/SC3U/sc3u: invalid ELF header

 when i use this method to execute
> 
joe@joe-desktop:~$ LD_ASSUME_KERNEL=2.2.5 $COMPAT/ld-linux.so.2 /usr/local/games/SC3U/sc3u

this is so frustrating knowing that most people are getting it to work.  im pretty sure i have a stabdard installation so i wonder what it is.

---

### Post by Slammer64 on 2007-07-03
LD_ASSUME_KERNEL no longer works on the more modern Ubuntu distros, try running without it, I have Kubuntu 7.04 and am running without any compatibility libraries, OBTW, do you have the latest patch for SC3K, if not try installing it first before you run, it fixes lots of errors.

---

### Post by kiddyfurby on 2007-07-11
there is a simcity 3000 floating around, that comes with all patches and run on Feisty x32
but without sound.... 

open /dev/dsp: Device or resource busy

---

### Post by Keith_Beef on 2007-09-03
> **Slammer64 said:**
> LD_ASSUME_KERNEL no longer works on the more modern Ubuntu distros, try running without it, I have Kubuntu 7.04 and am running without any compatibility libraries, OBTW, do you have the latest patch for SC3K, if not try installing it first before you run, it fixes lots of errors.

I just tried to run SC3U, after a long absence...
Without the compatibility libraries, I get:
```
Segmentation fault (core dumped)
```

With them, I get:
```
sc3u: relocation error: /usr/local/lib/loki_compatibility/Loki_Compat/libc.so.6: symbol _dl_starting_up, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference
```

I looked to see if there was a recent path, and loki.update doesn't find any.

```
Listing product updates

SimCity 3000 Unlimited
URL: http://updates.lokigames.com/sc3u/updates.txt
Looking up updates.lokigames.com
Connecting to updates.lokigames.com
Connected
Transfer complete
Retrieved update list
No new updates available
```

I'm running 7.04 (Feisty) with recent updates.

Any ideas how to cure this "relocation error"?

Beef.

---

### Post by Jeruleus on 2007-09-03
> **Slammer64 said:**
> LD_ASSUME_KERNEL no longer works on the more modern Ubuntu distros, try running without it, I have Kubuntu 7.04 and am running without any compatibility libraries, OBTW, do you have the latest patch for SC3K, if not try installing it first before you run, it fixes lots of errors.

Would you mind quickly running through exactly what you did to get Sim City 3000 to work for you?  I almost had it - I thought - but it didn't work.  I made a post about it in frustration...Suppose I should've just posted my issue here.

My issue: > **Jeruleus said:**
> Wow, so I've spent the past 5 hours today, and about an hour and a half each of the past two days, trying to get SimCity 3000 Unlimited to work.  It doesn't.  I've scoured various forums, tried different things, but still, nothing.  The farthest I've gotten is just now when I followed instructions from [this]("http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games") gentoo-wiki which called for running sc3u with old libraries.  But then I read [this]("http://forums.fedoraforum.org/archive/index.php/t-118038.html"), which suggested the use of a different set of libs, so I followed the aforementioned wiki, substituting the libs of the latter link.  So I ran:
```

 LD_LIBRARY_PATH=/usr/local/games/SC3U/Loki_Compat/ /usr/local/games/SC3U/Loki_Compat/ld-linux.so.2 /usr/local/games/SC3U/sc3u
```
But I had a musicplayer running, so all I got was the following error message:
```
open /dev/dsp: Device or resource busy
X Error:  BadMatch
  Request Major code 141 (XVideo)
  Request Minor code 19 ()
  Error Serial #19
  Current Serial #20

```
I killed the musicplayer and tried running it again.  My screen went black, as though the game were starting up, my mouse cursor changed from small and white to big and black, I got excited, music was playing, but then the video crashed.  The music, however, kept on playing.  I got the following error message:
```
fcntl: Operation not permitted
fcntl: Operation not permitted
X Error:  BadMatch
  Request Major code 141 (XVideo)
  Request Minor code 19 ()
  Error Serial #19
  Current Serial #20
```
Now, when I get this error, the music keeps playing, and my term acts as though the program's running - which is to say, the cursor blinks on a blank line, without the usual username@computername: prefix.

I don't know what to do.  Any help would be greatly appreciated.

---

### Post by Dod_basim on 2007-10-17
same problem.... bump

---

### Post by Cochise on 2007-11-02
trying it on gutsy got the compat libs, and:

> john@Desktop:/opt/games/loki_compat$  LD_LIBRARY_PATH=/usr/local/games/SC3U/Loki_Compat/ /opt/games/loki_compat/ld-linux.so.2 /usr/local/games/SC3U/sc3u
Floating point exception (core dumped)
john@Desktop:/opt/games/loki_compat$ 


---

### Post by shadoo00w on 2007-11-07
> /media/sdb7/Games/SC3000U/sc3u.dynamic: error while loading shared libraries: /media/sdb7/Games/SC3000U/sc3u.dynamic: cannot open shared object file: No such file or directory


What it means?Help me plz!And what should I do?
PS. I use ubuntu 7.10

---

### Post by monoufo on 2007-11-07
I am running Gutsy and finally got SC3 installed and patched, but it won't run.

---

### Post by TheIdiotThatIsMe on 2007-11-08
It is quite frustrating. I'm also having a problem with SC3U. I just installed Alpha Centauri (this is all on 7.10) and worked fine with a quick tweak from Xorg.conf, but SC3U seems to be having a lot more troubles. I get the following errors:

/usr/local/bin/sc3u: line 2: 11265 Segmentation fault      (core dumped) /usr/local/games/SC3U/sc3u

or if I use the LD ASSUME I get

/usr/local/games/SC3U/sc3u: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

I haven't tried the whole compatibility thing though.

---

### Post by monoufo on 2007-11-08
if you did try the compatibility think you would just get different error messages.

---

### Post by Keith_Beef on 2007-11-08
I've built a new computer, so I'm trying to install from scratch.

Gutsy 64 bit, installing gets me:
```
This installation doesn't support glibc-2.0 on Linux / x86_64

Please contact Loki Technical Support at support@lokigames.com
```

I suppose I should have expected that a program from way back wouldn't have worked on the 64 bit architecture.

---

### Post by mattmull on 2007-11-11
I just got this working on 7.04:

First install the game like normal off the cd, then download and install the Loki patch sc3u-2.0a-x86.run.

I downloaded the old FC5 libs from:

[http://www.linuxrising.org/files/lokicompat.tar.bz2](http://www.linuxrising.org/files/lokicompat.tar.bz2)

I then extracted that bzip to /usr/local/games/SC3U

Then from the command prompt try running:

$  LD_LIBRARY_PATH=/usr/local/games/SC3U/Loki_Compat /usr/local/games/SC3U/Loki_Compat/ld-linux.so.2 /usr/local/games/SC3U/sc3u.dynamic -intro:off -w

If you're not running the program as the user that's logged into X-Windows, you'll get an error message.  You need to run "xhost +" from a command prompt as the user you're logged into X as first.

---

### Post by JeevesBond on 2007-11-18
Sadly that doesn't seem to work for Gutsy. Following error is returned:
```
 /usr/local/games/SC3U/Loki_Compat/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libsmpeg-0.4.so.0)
```
Any ideas how this could be fixed?

---

### Post by dreamrae on 2007-11-20
After hacking together the game installer and the patch installer I get this after running the game:

> fcntl: Operation not permitted
fcntl: Operation not permitted
X Error:  BadMatch
  Request Major code 141 (XVideo)
  Request Minor code 19 ()
  Error Serial #19
  Current Serial #20

I had better luck running simcity 3 under wine.

On to simcity 4?

[http://tombuntu.com/index.php/2007/04/06/simcity-4-on-ubuntu-with-wine/](http://tombuntu.com/index.php/2007/04/06/simcity-4-on-ubuntu-with-wine/)

---

### Post by michaelxjt on 2008-01-11
I got it working in edgy by following these instructions;

[http://bashu.wordpress.com/2007/02/17/simcity-3000-on-ubuntu-dapper/]("http://bashu.wordpress.com/2007/02/17/simcity-3000-on-ubuntu-dapper/")

then

[http://bashu.wordpress.com/2007/04/15/simcity-3000-on-ubuntu-edgy/]("http://bashu.wordpress.com/2007/04/15/simcity-3000-on-ubuntu-edgy/")

(You have to follow the dapper instructions first even if using edgy)

And it worked fine except choosing resoltuion via the ingame menu doesn't seem to work so I put the -r:1024x768  command switch inside the launch script.

---

