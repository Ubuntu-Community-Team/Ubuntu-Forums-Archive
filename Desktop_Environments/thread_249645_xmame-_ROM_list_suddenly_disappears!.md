---
title: "xmame- ROM list suddenly disappears!"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Linux BASHer on 2006-09-02
Hello. I'm trying to get MAME to run in Dapper Drake. I spent some time unable to play my ROMs due to a permissions/path issue. I downlaoded GXMame and KXmame and am using them as front ends (haven't decided which I like better yet).

Once the problems were resolved, though, I was able to play all of them, and I spent a while testing/playing them out.Then, I decided to switch the screen resolution to 640x480 to better play the games (full screen, without scaling). After this, all the ROMs listed in "Available games" disappeared. I switched back to my regular screen res., quit xmame, rebooted, re-checked permissions and paths, audited all games, refreshed, rebuilt the ROM list... But nothing has been able to get xmame to display my ROMs.

It's disappointing that I was able to play all of the ROMs perfectly, but in one moment that changed and I haven't been able to figure out how to get it back. What is going on? Does anybody have any clue?

---

### Post by croak77 on 2006-09-02
Try looking in you /home/username directory. There might bi a hidden folder like .xmame which stores settings for xmame. Try deleting it and start again.

---

### Post by Linux BASHer on 2006-09-02
Thanks for the suggestion, croak77. There was a hidden folder by that name, which I deleted (I could always drag it back to the trash in any case), however that didn't seem to change anything.

---

### Post by croak77 on 2006-09-03
You have all the BIOS files? Maybe try remove with purge. sudo apt-get remove --purge xmame and then reinstall.

---

### Post by Linux BASHer on 2006-09-03
Erase and re-install-- pretty sad that I have to do that. Anyway, I did so, and **still** nothing. Perhaps I'm a bit bias at this point, but these are the times I realize why my Mac is my main machine... This is quite frustrating...

---

### Post by klytu on 2006-09-03
> **Linux BASHer said:**
> Erase and re-install-- pretty sad that I have to do that. Anyway, I did so, and **still** nothing. Perhaps I'm a bit bias at this point, but these are the times I realize why my Mac is my main machine... This is quite frustrating...

Can you play the games by running xmame with a command line? If so, the default ROM path in kxmame and gxmame might have changed somehow. That should be simple to correct ....

---

### Post by Linux BASHer on 2006-09-03
> **klytu said:**
> Can you play the games by running xmame with a command line? If so, the default ROM path in kxmame and gxmame might have changed somehow. That should be simple to correct ....

I just tried to run it via the terminal. Let me paste the output here:

> warning: no mixer plugins available
info: trying to parse: /etc/xmame/xmamerc
error: unknown option history_file, on line 13 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option mameinfo_file, on line 14 of file: /etc/xmame/xmamerc
   ignoring line
info: trying to parse: /home/LinuxBASHer/.xmame/xmamerc
info: trying to parse: /etc/xmame/xmame-SDLrc
info: trying to parse: /home/LinuxBASHer/.xmame/xmame-SDLrc
info: trying to parse: /etc/xmame/rc/pacmanrc
info: trying to parse: /home/LinuxBASHer/.xmame/rc/pacmanrc
xmame: could not connect to socket
xmame: No such file or directory
(null): could not open config files /home/LinuxBASHer/.lircrc and /etc/lirc//lircrc
No such file or directory
loading rom 0: pacman.6e
loading rom 1: pacman.6f
loading rom 2: pacman.6h
loading rom 3: pacman.6j
loading rom 4: pacman.5e
loading rom 5: pacman.5f
loading rom 6: 82s123.7f
loading rom 7: 82s126.4a
loading rom 8: 82s126.1m
loading rom 9: 82s126.3m
done
pacman.6e    NOT FOUND
pacman.6f    NOT FOUND
pacman.6h    NOT FOUND
pacman.6j    NOT FOUND
pacman.5e    NOT FOUND
pacman.5f    NOT FOUND
82s123.7f    NOT FOUND
82s126.4a    NOT FOUND
82s126.1m    NOT FOUND
82s126.3m    NOT FOUND
ERROR: required files are missing, the game cannot be run.


I'm also getting a message from the GUI front-end saying that History.dat and mameinfo.dat are missing.

I just don't understand why a new install from synaptic would be broken. Anyway, thanks for the reply. Hopefully I can get this working with your help.

---

### Post by klytu on 2006-09-03
> **Linux BASHer said:**
> I just tried to run it via the terminal. Let me paste the output here:



I'm also getting a message from the GUI front-end saying that History.dat and mameinfo.dat are missing.

I just don't understand why a new install from synaptic would be broken. Anyway, thanks for the reply. Hopefully I can get this working with your help.

From the error output it's clear that xmame doesn't know where to find your ROMS.

try this:

```
xmame pacman -rp /usr/share/games/xmame/roms/
```

You would, of course, substitute the directory where your roms are located for /usr/share/games/xmame/roms/ above. If you are not sure where your roms are located, you can try a simple search. First do this:

```
sudo updatedb
```

Let that finish, then do this:

```
locate roms
```

Examine the output to find where your roms live and then try to run xmame from a command line as above. If that works, the next step will be to update your xmame default configuration files and the settings for kxmame and gxmame. I don't use gxmame, but I can help you set up kxmame and I can help you get up and running from the command line. For command line options this will give you a wealth of information:

```
xmame -help | less
```

---

### Post by Linux BASHer on 2006-09-03
[offtopic]
BTW, I've been trying to get my friends to see *The Day the Earth Stood Still* with me, but they don't seem to think that seeing a black and white early 1950's film is the best way to spend the night. Nice avatar/nick. ;-)
[/offtopic]

Ah, okay klytu now we're getting somewhere. I was able to get xmame to run, but only in the terminal. Seems the rom files were in:

/usr/share/games/xmame/roms/DATA/roms

rather than simply in: /usr/share/games/xmame/roms/

Now, if the .zip files are actually the ROMS, then what do the .bat files do? Can I/Should I delete them?

I fired up kxmame and updated the ROM path, but I still can't get that to work, though.

Thanks a lot for your help.

---

### Post by Linux BASHer on 2006-09-03
Update: xmame doesn't seem to remember where the ROMs are at startup. I need to tell it each time. Perhaps this has something to do with it not being able to find it's config file? How would I go about fixing this?

---

### Post by klytu on 2006-09-03
> **Linux BASHer said:**
> Update: xmame doesn't seem to remember where the ROMs are at startup. I need to tell it each time. Perhaps this has something to do with it not being able to find it's config file? How would I go about fixing this?

OK. You'll need to find your xmamerc file. You can try the locate command again:

```
locate xmamerc
``` 

Mine is at /etc/xmame/xmamerc. Once you find it you can edit it with your favorite text editor. gedit is fine for gnome; kate is OK for KDE. Just do:

```
gedit /etc/xmame/xmamerc
```

And then look for the line containing "rompath" under the "Data files/directories". Update that line with the directory containing your roms and save the file. Now when you run xmame from the command line it will find your roms and you'll no longer need to use the -rp option unless you put roms somewhere else.

---

### Post by klytu on 2006-09-03
> [offtopic]
BTW, I've been trying to get my friends to see The Day the Earth Stood Still with me, but they don't seem to think that seeing a black and white early 1950's film is the best way to spend the night. Nice avatar/nick.
[/offtopic]

Ah, okay klytu now we're getting somewhere. I was able to get xmame to run, but only in the terminal. Seems the rom files were in:

/usr/share/games/xmame/roms/DATA/roms

rather than simply in: /usr/share/games/xmame/roms/

Now, if the .zip files are actually the ROMS, then what do the .bat files do? Can I/Should I delete them?

I fired up kxmame and updated the ROM path, but I still can't get that to work, though.

Thanks a lot for your help.

Glad you caught the reference to *The Day the Earth Stood Still*:) 

I have no idea what you mean about the .bat files. I only have maybe a dozen or so ROMS that I use and I got them all as .zip files. I would guess that the .bat files are for Windows or DOS; it is probably OK to delete them if you only use Linux, but there should be no harm leaving them there.

What happens with kxmame when save the correct ROM path and try an Audit?

---

### Post by Linux BASHer on 2006-09-03
Thanks klytu. That seems to have fixed xmame in the terminal, though I think there are still some oddities left, but I'm not too concerned with those at the moment. Still can't get it to run via kxmame, though. It still isn't finding the ROMs.

---

### Post by klytu on 2006-09-03
> **Linux BASHer said:**
> Thanks klytu. That seems to have fixed xmame in the terminal, though I think there are still some oddities left, but I'm not too concerned with those at the moment. Still can't get it to run via kxmame, though. It still isn't finding the ROMs.

You might have missed my last reply. I had some network problems at this end and at first the same message posted twice. I edited the second one and it hit after your response.

---

### Post by Linux BASHer on 2006-09-03
> **klytu said:**
> Glad you caught the reference to *The Day the Earth Stood Still*:)

Of course. It's classic TV sci-fi.

> **klytu said:**
> I have no idea what you mean about the .bat files. I only have maybe a dozen or so ROMS that I use and I got them all as .zip files. I would guess that the .bat files are for Windows or DOS; it is probably OK to delete them if you only use Linux, but there should be no harm leaving them there.

Ah, okay. No need for them, then. No Windoze here. Just Linux and Macs.

> **klytu said:**
> What happens with kxmame when save the correct ROM path and try an Audit?

Nothing. It doesn't get any of the ROMs. I don't get it. It was working so well before and then poof-- something must have changed-- and my MAME troubles ensued. Guess it would have been too easy otherwise.

> **klytu said:**
> You might have missed my last reply. I had some network problems at this end and at first the same message posted twice. I edited the second one and it hit after your response.

I only saw your double post at first. Might not have been only on your end, though. The forums are horrendously SLOW. Hopefully the keepers will have them running back at full speed soon.

---

### Post by klytu on 2006-09-03
> **Linux BASHer said:**
> Hello. I'm trying to get MAME to run in Dapper Drake. I spent some time unable to play my ROMs due to a permissions/path issue. I downlaoded GXMame and KXmame and am using them as front ends (haven't decided which I like better yet).

Once the problems were resolved, though, I was able to play all of them, and I spent a while testing/playing them out.Then, I decided to switch the screen resolution to 640x480 to better play the games (full screen, without scaling). After this, all the ROMs listed in "Available games" disappeared. I switched back to my regular screen res., quit xmame, rebooted, re-checked permissions and paths, audited all games, refreshed, rebuilt the ROM list... But nothing has been able to get xmame to display my ROMs.

It's disappointing that I was able to play all of the ROMs perfectly, but in one moment that changed and I haven't been able to figure out how to get it back. What is going on? Does anybody have any clue?

I read your original post above again. How did you change the screen resolution and then switch back to your regular screen resolution? Maybe I am using a different version of xmame than you are, because when I run kxmame I don't have the option to change the resolution to a specific setting (like 640x480, in your example). My options under Rendering are fullscreen (which I leave checked), double buffering (which I leave clear), auto resolution (which I leave checked), and keep aspect ratio (which I leave checked). The version of xmame I am running is xmame  (sdl) version 1.01.

---

### Post by Linux BASHer on 2006-09-03
> **klytu said:**
> I read your original post above again. How did you change the screen resolution and then switch back to your regular screen resolution? Maybe I am using a different version of xmame than you are, because when I run kxmame I don't have the option to change the resolution to a specific setting (like 640x480, in your example). My options under Rendering are fullscreen (which I leave checked), double buffering (which I leave clear), auto resolution (which I leave checked), and keep aspect ratio (which I leave checked). The version of xmame I am running is xmame  (sdl) version 1.01.

Yes, we're probably using the same verisons. I just changed it via the Screen Resolutions control panel in GNOME. Nothing exotic or even related to xmame itself.

---

### Post by Linux BASHer on 2006-09-10
I pointed it to the ROM path again and that has fixed the problem. Seems a trailing "/" was missing. Still odd, though, as I had browsed and pointed it to the proper folder multiple times prior. Oh, well.

I am happy now. :)
 	
Thanks a lot for your help, croak77 and klytu.

---

### Post by jet2230 on 2007-04-19
> **Linux BASHer said:**
> I pointed it to the ROM path again and that has fixed the problem. Seems a trailing "/" was missing. Still odd, though, as I had browsed and pointed it to the proper folder multiple times prior. Oh, well.

I am happy now. :)
 	
Thanks a lot for your help, croak77 and klytu.

im having probs with that as well in edgy. gxmame just does not display the roms i have and it does have the correct rom path.  is there a fix for this?

---

