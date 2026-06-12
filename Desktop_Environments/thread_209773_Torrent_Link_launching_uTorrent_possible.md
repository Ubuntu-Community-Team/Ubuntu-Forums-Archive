---
title: "Torrent Link launching uTorrent possible ?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by orb9220 on 2006-07-05
When I click torrent link and chose to have firefox open with uTorrent.exe
nothing happens.

uTorrent runs fine if I save the link then add from within uTorrent.

Any workarounds for this issue?

#-o 

Any Help is Welcomed.

---

### Post by kinematic on 2006-07-05
may i ask why you're running utorrent when azureus,bittorrent,ktorrent and bittornado run natively on linux?

---

### Post by orb9220 on 2006-07-05
Azureus is a mem and resource Hog as far as I'm concerned.
Bittorrent has to  open a new window for every torrent. I don't need 10 Individual windows to keep track of.
ktorrent and bittornado have no near the details and functions that uTorrent,bitcomet,ect..

Azureus is also a pain to setup. From all the other posts u have been in.

uTorrent took me 3 mins to have up and running without all that setting up permissions and crap.

All I needed was info on this little issue.

Thanks for yer suggestions tho

---

### Post by Doovoo on 2006-07-05
I agree, uTorrent is the superior Bittorrent client. I wish someone would port it.

---

### Post by stoeptegel on 2006-07-06
[QUOTE=Doovoo]I agree, uTorrent is the superior Bittorrent client. I wish someone would port it.[/QUOTE]

If utorrent was gpl someone would probably already have done so, but it's not.

---

### Post by flip314 on 2006-07-06
[QUOTE=orb9220]When I click torrent link and chose to have firefox open with uTorrent.exe
nothing happens.

uTorrent runs fine if I save the link then add from within uTorrent.

Any workarounds for this issue?

#-o 

Any Help is Welcomed.[/QUOTE]

Have you tried setting the "open with" command to "wine /path/to/uTorrent.exe" ?  I haven't tried it, but that's my suggestion.

I hate Azureus.  It's large, bloated with things I never use, a memory and CPU hog, and crashes a lot.  uTorrent can run with a dozen torrents at ~2% CPU and >10MB memory usage.  It also has all the features Azureus has that I need, and seems to run perfectly under wine.

---

### Post by latebeat on 2006-08-25
Did you find a solution to this ? I'm trying to figure out the same thing

thanks

---

### Post by srunni on 2006-08-25
I would be interested in a solution to this problem as well. I just installed uTorrent under wine today, and haven't used it much. I didn't realize that I would have this problem, but I guess I will. I'll look into this, but one suggestion I have is to make a script that will open the file in uTorrent, and have Firefox send the .torrent to the script.

---

### Post by latebeat on 2006-08-25
> **srunni said:**
> I would be interested in a solution to this problem as well. I just installed uTorrent under wine today, and haven't used it much. I didn't realize that I would have this problem, but I guess I will. I'll look into this, but one suggestion I have is to make a script that will open the file in uTorrent, and have Firefox send the .torrent to the script.

that's what I'm doing at the moment but it doesn't work.
The strange thing is that if I type wine pathto/utorrent.exe pathto/foo.torrent in a terminal it works

---

### Post by asplode on 2006-08-25
This is a good question and I'd like to know an answer too..

I would use Transmission but it's banned on Oink, and its a pain to have 2 clients running at once, soaking up all my bandwidth...

But dammit if uTorrent isn't ugly under WINE.  And its got a few issues when I switch desktops and the window isn't minimized to its little tray icon.

I doubt it will ever be ported to anything, not necessarily because its not open source, but because it was designed with special libraries and a LOT of windows API under the hood.

---

### Post by 505 on 2006-08-25
Yes, it is possible launch the torrent automatically. You need a special script.

Steps to get it:
1. Open a terminal
2. Type ```
sudo gedit /usr/bin/utorrent
```
3. Paste the following text
```

#!/bin/sh

cd ~/.wine/drive_c/Program\ Files/utorrent
if [ "$1" != "" ]; then
	var="`echo $1 | sed 's/\//\\\/g'`"
	var="Z:${var}"
	wine utorrent.exe "$var"
else
	wine utorrent.exe
fi

```
Modify the path to the utorrent directory where needed
4. Save and close Gedit
5. Type ```
sudo chmod a+x /usr/bin/utorrent
```

You can now launch utorrent from anywhere by typing 'utorrent' (no .exe)
To open .torrents automatically from firefox set the utorrent file as the default program.

---

### Post by latebeat on 2006-08-25
> **505 said:**
> Yes, it is possible launch the torrent automatically. You need a special script.




thanks!! Really elegant!

can you explain the 
```
sed 's/\//\\\/g'
``` part?

thanks!

---

### Post by Spudgun on 2006-08-25
*man sed* :P

---

### Post by sciphre on 2006-11-06
This [http://www.linux.com/article.pl?sid=06/07/27/183221](http://www.linux.com/article.pl?sid=06/07/27/183221)
is MUCH more elegant.

---

### Post by of_darkness on 2006-11-10
> #!/bin/sh

cd ~/.wine/drive_c/Program\ Files/utorrent
if [ "$1" != "" ]; then
	var="`echo $1 | sed 's/\//\\\/g'`"
	var="Z:${var}"
	wine utorrent.exe "$var"
else
	wine utorrent.exe
fi

I had to change it to > #!/bin/sh

cd ~/.wine/drive_c/Program\ Files/uTorrent
if [ "$1" != "" ]; then
	var="`echo $1 | sed 's/\//\\\/g'`"
	var="Z:${var}"
	wine utorrent.exe "$var"
else
	wine utorrent.exe
fi

when running uTorrent-1.6-install.exe ...

---

### Post by pppetter on 2007-02-05
or just create utorrent.sh, with this instead:

> 
#!/bin/sh
wine /path/to/utorrent.exe "$*"

$* = the path to the thing you want to open, given by firefox, nautilus, konqueror or whatever. You made a great script. This is just easier ;)

---

### Post by AlucardXXVII on 2007-03-04
thanks, this script worked for me!

---

### Post by pt123 on 2007-06-09
Thanks great script now I can open torrent files directly into utorrent

I just had to change the T to a capital T in uTorrent in the folder path.

---

### Post by dansued on 2007-06-26
I used this

```

#!/bin/sh

cd ~/.wine/drive_c/Program\ Files/utorrent
if [ "$1" != "" ]; then
    var="`echo $1 | sed 's/\//\\\/g'`"
    var="Z:${var}"
    wine utorrent.exe "$var"
else
    wine utorrent.exe

```

and it works, I type in utorrent into terminal, and it opens.

but what do I do in firefox? When the pop-up asks you if you want to save or run, I go to "open with" and in the location field, I type in utorrent. This only gives me an error. It says, "the application (null) cannot be found. Check filename"

---

### Post by michaelzap on 2007-06-26
I know this was already mentioned, but I went through this exact same process so I'm going to chime in anyway. kTorrent is actually very similar to uTorrent and works very well in Ubuntu. I get just as good download speeds in kTorrent as I did using uTorrent, and everything integrates as it should (system icon and notifications, easy downloading from Firefox, etc.).

---

### Post by AriciU on 2007-06-26
> **505 said:**
> Yes, it is possible launch the torrent automatically. You need a special script.


Always wanted to have this. Thanks! :D

---

