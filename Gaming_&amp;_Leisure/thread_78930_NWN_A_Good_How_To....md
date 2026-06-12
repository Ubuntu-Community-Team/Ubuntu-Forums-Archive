---
title: "NWN: A Good How To..."
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by the_purulent on 2005-10-19
Hey guys,
I'm looking for a good "how to" on installing neverwinter nights.  I have been unable to find one so far... could be I'm just looking in the wrong places.

---

### Post by bhursey on 2005-10-19
This is as good as you get follow the instructions exactley and you will have nwn working perfictley on your system. 

[http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

---

### Post by the_purulent on 2005-10-19
Perfect! Works like a charm. Thanks man.

---

### Post by bhursey on 2005-10-19
np, have fun... :p

---

### Post by leech on 2005-10-20
I just wrote one as well.  Maybe it should be a sticky, though I may just host it on my own server.  Since I own the 4 CD Platinum Edition of the game, that's what is more geared towards.

I will also include how to get the Movies to work as well, as soon as I find the time.

Leech

---

### Post by the_purulent on 2005-10-20
Oh. by the way, installing from the platinum dvd edition and applying the latest patch is super easy.  The hardest part is actually activating your account on bio-wares website (nearly 12 hours and 4 emails later it is still not active :)) BUT I found the files I needed on  filemirrors.com.

The process was very simple:

create a folder (I used /home/NWN)
extract shared_data.zip to the new folder
extract language_data.zip to the new folder
extract language_shared.zip to the new folder

extract linux client files to the new folder
run the game ./nwn, and enter your nwn cd key
extract the update to version 1.66 to the new folder

run the game again and enter the next two cd keys (sou &hotu)

That's it! Pretty easy and no disk swapping :)

---

### Post by leech on 2005-10-20
Well, of course there isn't any disk swapping, you have the DVD version :D

Unfortunately when I bought mine, the store didn't have the DVD version.  I would just combine everything onto one DVD, but I'm just too lazy :D

It's not like I have to re-install the game a lot, since it IS on linux.

Leech

---

### Post by leech on 2005-10-20
Oh wait, you did it the hard way!  You don't need to download all the data files, they're right there on your disk.  I just grabbed the installation script that someone in the Bioware forums were nice eough to create.

[http://www.paradoxinc.net/~icarus/files/install-nwn.sh](http://www.paradoxinc.net/~icarus/files/install-nwn.sh)

Leech

---

### Post by the_purulent on 2005-10-20
Nah, I didn't download them, I started to, but it seemed stupid to me to download a 1.3 gb file just to install, so I found a decent tutorial in the bioware forums and just got the client install files from the filemirrors site.

And hopefully I will never have to re-install again ;) My goal is not to have to change my os untill the dapper release!

---

### Post by leech on 2005-10-20
I didn't even download the install client, the only thing that needs to be downloaded is the patch, which the install script will do for you.

Leech

---

### Post by darkfame on 2005-10-21
Try [http://www.liflg.org/]("http://www.liflg.org/") next time...

---

### Post by leech on 2005-10-22
Yeah, except I don't think the installer that liflg.org works with the Platinum edition.  Has it been updated since the Gold installer that Ravage made?

I know there are installers for the patches, etc.  But it seems kind of overly redundant to me.  The installer I linked to simply has you swap disks (if you have the CD version) and downloads the patch for you, and installs it all, nice and neat.  The only thing it doesn't do, is create an icon for you.  Which is easy enough in Ubuntu anyhow.

Leech

---

### Post by ecletrik on 2005-10-24
Can I install NWN with all the files listend on the bioware website?

I still have my CD Key and playdisc from when the game first came out, but i've lost the install disks.

---

### Post by Sheytan on 2005-10-28
I edited nwn too look like this and i copied it too usr/local/bin

> #!/bin/sh

# This script runs Neverwinter Nights from the current directory
cd "/home/sheytan/Games/nwn/"

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

exec ./nwmain "$@"


Is it ok?

---

### Post by Jenda on 2005-10-29
I used the loki installer. Will updating the game fix the game "not finding module" when a new game is started?

---

### Post by leech on 2005-10-29
[QUOTE=Sheytan]I edited nwn too look like this and i copied it too usr/local/bin



Is it ok?[/QUOTE]


Yeah, that should work.  Though you'd still have to start it from the command line.  The way I described how to do it, you'll have either a Icon on the desktop or in the Games menu of Gnome.

Leech

---

### Post by leech on 2005-10-29
[QUOTE=Jenda]I used the loki installer. Will updating the game fix the game "not finding module" when a new game is started?[/QUOTE]

It should, some modules require a specific version of the game to be installed (due to new tilesets, creatures, etc.)

---

### Post by l0c0dantes on 2005-10-30
Can somone help me?

I copied and pasted the Command line inputs from the website, I go to run the fixinstall and i get this ```
loco@Shuteyetrain:~/Program Files/nwn$ ./fixinstall
Checking for required files

PASSED: ambient directory exists
PASSED: data directory exists
PASSED: music directory exists
PASSED: override directory exists
PASSED: miles directory exists
PASSED: nwm directory exists
PASSED: chitin.key exists
PASSED: dialog.tlk exists
PASSED: nwmain exists
PASSED: xp1.key exists

Fixing case

ambient
....................................................................................................
data
...................................
dmvault
..
hak
.
localvault
.......................
music
................................................................
override
....

Checking for problem files


Checking for permissions

PASSED: nwn.ini is writable
PASSED: nwnplayer.ini is writable
PASSED: nwncdkey.ini is writable
PASSED: saves is writable
PASSED: localvault is writable
PASSED: tempclient is writable
PASSED: dmvault is writable
./fixinstall: line 126: [: /home/loco/Program: binary operator expected
WARNING: /home/loco/Program Files/nwn is not writable

You are ready to run Neverwinter Nights.

loco@Shuteyetrain:~/Program Files/nwn$ ./nwn
```

can anyone help me?

---

### Post by Jenda on 2005-10-30
It seems you do not have write permissions to /home/loco/Program Files/nwn.
It also seems UNIX is having troubles recognising the space in Program Files: > /home/loco/Program: binary operator expected
WARNING: /home/loco/Program Files/nwn 
If you entered a path containing "Program Files" anytime during the whole process - repeat the step with "Program\ Files" - that's the proper way to do it. When you just write "Program Files", UNIX inerprets this as two seperate arguments: "/home/loco/Program" and "Files/nwn", neither of which is valid.
I'm guessing it's talking about a text file it is using: a script, since it talks about line 126. Check that out. If you have any ideas what script this could be, look at 126. Isn't fixinstall itself a script? If it is, replace the "Program Files" on line 126 with "Program\ Files".

It does' however, say that you can run nwn now. Was there an error after you ./nwn'ed?
> 
It should, some modules require a specific version of the game to be installed (due to new tilesets, creatures, etc.)
It did. Now the game segfaults on me because of permissions. I temporarisy solved this by sudoing it. Bad idea, securitywise, I know...

---

### Post by Sheytan on 2005-10-30
!

---

### Post by l0c0dantes on 2005-10-30
Opps, sorry about that

Yes, the error is after I type ./nwn
All it says is "ERROR"
Is there a way to debug it to see what went wrong?

---

### Post by madjo on 2005-10-30
The Howto from this thread worked wonders for me:
[http://nwn.bioware.com/forums/viewtopic.html?topic=417536&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=417536&forum=72)

(though it is for the platinum version, it might help for you)

---

### Post by Cuppa-Chino on 2005-11-27
I am thick and withdraw what I asked earlier...

I only get a black screen after startup I can hear the music though?

before you ask:
```
@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 1.3.5461 (X4.3.0-8.19.10)

```

 any ideas

---

### Post by Cuppa-Chino on 2005-11-27
found a solution (or at least part of one):

edit the **nwn** shell script with a text editor and remove the reference to **[COLOR="Red"]./lib[/COLOR]** in the [COLOR="Blue"]**export**[/COLOR] line

```
#!/bin/sh
# This script runs Neverwinter Nights from the current directory
export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
[COLOR="Blue"]**export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH**[/COLOR]
## the previous export line was : export LD_LIBRARY_PATH=**./lib:**./miles:$LD_LIBRARY_PATH
./nwmain $
```

all worked well I could run NWN at least until the setup screen but when upgrading to Shadows of Unrentide system cracked again... will keep you posted

---

### Post by PhoenixAndy on 2005-12-05
I read on the Bioware site that the native linux client doesn't play the in-game movies. Can anyone tell me whether this is actually the case? If so, I'll probably try to get it working with Cedega, ratehr than use the native client

---

### Post by the_purulent on 2005-12-05
Movie worked ok for me.
I just followed the directions from the bioware forums and viola! worked like a charm.

---

