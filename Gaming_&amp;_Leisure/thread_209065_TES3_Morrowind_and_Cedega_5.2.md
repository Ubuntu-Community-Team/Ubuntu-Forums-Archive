---
title: "TES3: Morrowind and Cedega 5.2"
date: 2006-07-04
forum: Gaming &amp; Leisure
---

### Post by Iarwain ben-adar on 2006-07-04
Hi all,

I recently got my Kubuntu 6.06 cd's delivered, and it was a bless to install and set it up.
No problems with audio, nor with internet, nor even with gfx drivers...

Just 1 small "problem": 

I installed The Elder Scrolls: Morrowind on my pc (specs are down below)
The game played just great, and me feeling lucky, i wanted to download some mods and play with them enabled...

That's when the problem began: with the mods loaded, the game experienced (sp?) some "lag" (or so to say)

It seems that the game pauses (sp?), or starts loading, whenever a sound must be played...

My system is completely fine (or so i think it is) but anyways:
AMD 3200+ (2.0Ghz but only recognized as 1Ghz),
1Gb RAM,
Nvidia 6600 256Mb
couple of hdd's


So, does anyone know some bit to help me?
Sincere thanks,


Iarwain

---

### Post by Iarwain ben-adar on 2006-07-05
If it can help, i enabled Cedega's fps HUD,
and now i see that my frames are really low :(
They're about 10-20 outdoors, and 100-120 indoors -_-


Iarwain

---

### Post by Iarwain ben-adar on 2006-07-06
My previous post was secretly disguised as a bump...
Didn't notice eh? =)


Iarwain

---

### Post by Miguel on 2006-07-06
Mmm... according to my Morrowind (in windows) experience, 100-120 fps indoors should be able to give you 30 or 40 fps outdoors. Anyway... are you using a no-cd patch? If not, do. I've heard some people had trouble with the cd check. If you do, try going back to the original exe. Other things to do are uncheck your mods and see if it works again OK. Then you could also attempt to see if this is caused by a mod.

However, I must confess I haven't tried to run Morrowind in Linux. I'm not paying for cedega.

---

### Post by Iarwain ben-adar on 2006-07-06
Hi Miguel,
thanks for the reply

I downloaded a no-cd patch, but i must execute it (and i have no Wine)
and with Cedega i get this:
```
iarwain@iarwain-desktop:~/.cedega/Morrowind/c_drive/Program Files/Bethesda Softworks/Morrowind$ cedega Crack120722.exe
/home/iarwain/.gtk_qt_engine_rc:355: Unable to locate image file in pixmap_path: "32x32/actions/configur2/actions/configure.png"
Warning: unprotecting the first 64KB of memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
 THE ELDER SCROLLS 3:MORROWIND V1.2.0722 NOCD Crack by FBSA in 2002

       (For the 3907584 bytes MORROWIND.EXE - 07/22/2066)




File access error!

```


Iarwain

---

### Post by Miguel on 2006-07-06
A quick question: Do you have any of the expansions? In that case, your executable version should be 1.4.* (I think) for Tribunal only or 1.6 for Bloodmoon (with or without tribunal). Maybe it's worth a check.

BTW: If you hae them, it's worth to install the expansions due to bugfixes and the added sorting of the journal. However, you might want to deactivate Tribunal for your first few levels (telling why is a spoiler).

---

### Post by Iarwain ben-adar on 2006-07-06
I have them both (and i know the spoiler :D. Thx though for not telling)

Should i install them now? And then try another no-cd?

How does it happen that i have a File Access Error?


Iarwain

---

### Post by Miguel on 2006-07-06
OK, for the expansions, I'd say to install them both. But then, the relevant no CD patch should be another.

And for the file access, I've read some guys solved some trouble by giving their files write permissions to user, group, and other. Based on this, I'd attemt to chmod a+w Morrowind.exe (I think it was).

But maybe (and just maybe) you could try first to uncheck the mods to see if your performance goes back to normal levels. Oh! And before I quit, I also suffer from bad FPS (windows, though) nearby the Dren plantation (between Vivec and Suran) and in snowy Solshteim (sp?), though it's not as bad as in Dren plantation.

BTW: I'm sending you a PM

---

### Post by Iarwain ben-adar on 2006-07-06
Well,
i'm trying to install both expansions, but just a little stupid problem...
HOW?
I insert my disk, but how do i tell cedega that it is an expansion?
How do i install it? :$


Iarwain

---

### Post by Miguel on 2006-07-06
You should try to install the expansion normally, that is, double-clicking (or via CLI) setup.exe. It should be able to locate the "original" install via the fake registry entries that Cedega makes. Else... I have no idea. Sorry.

---

### Post by Iarwain ben-adar on 2006-07-06
Doesn't work that good :(

With clicking it doesn't start installing,
and via cli:
```
iarwain@iarwain-desktop:/media/cdrom$ cedega AutoRunTribunal.exe
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2979, in ?
    gddb_file = detected[0]
TypeError: unsubscriptable object
iarwain@iarwain-desktop:/media/cdrom$ cedega Setup.exe
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2979, in ?
    gddb_file = detected[0]
TypeError: unsubscriptable object

```


Iarwain

---

### Post by Perfect Storm on 2006-07-06
Tried with this loki installer(wine): [http://liflg.org/?catid=7&gameid=38](http://liflg.org/?catid=7&gameid=38)
The intro might be very laggy just hit <esc> continuesly until you get to thte option screen. After that it works perfectly.

---

### Post by Iarwain ben-adar on 2006-07-06
Might give it a shot,
but i'm on dial-up :(

meh, just going to let it download :D


Iarwain

---

### Post by Iarwain ben-adar on 2006-07-06
Now,
all is downloaded and such:

But when i execute the .run file, i get this error:
```
iarwain@iarwain-desktop:~$ ./morrowind_1.2.0722-english.run
Verifying archive integrity... All good.
Uncompressing Morrowind 1.2.0722-english Installer.......................................................................
/home/iarwain/.setup13674: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```


Iarwain

---

### Post by Perfect Storm on 2006-07-06
```
sudo apt-get install libgtk1.2
```

---

### Post by Iarwain ben-adar on 2006-07-06
I'm happy :D

It's installing atm (or so i think: the progress bar isn't moving, but it has'nt moved for any progress bar in whatsoever app)

I'll keep in touch :D

EDIT: it's moving, 't was just "Running Script" =)

Iarwain

---

### Post by Iarwain ben-adar on 2006-07-06
Meh,
It's installed and such, no errors there.

Just when i try to start the game, (via console)
i get this:
```
iarwain@iarwain-desktop:~/morrowind$ ./morrowind
iarwain@iarwain-desktop:~/morrowind$ Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2979, in ?
    gddb_file = detected[0]
TypeError: unsubscriptable object

```

EDIT: nevermind about that error (got it solved by changing the original Cedega install path to the loki install path)

Game plays (FINE!)

Now, one last little request... (it's not that a problem that big, but quite annoying)

When i click "Data Files" in the MW launcher, all i see are boxes ticked.
Normally you'd see the text next to it, but i do not. Even un-ticking is not possible (it still shows ticked)

I'm gonna upload an image, but it will take a while (stupid dial-up)

EDIT2: here it is 
[[IMG]http://img178.imageshack.us/img178/683/mw0ay.th.png[/IMG]](http://img178.imageshack.us/my.php?image=mw0ay.png)


Iarwain

---

### Post by Miguel on 2006-07-07
> **Iarwain ben-adar said:**
> Meh,
Now, one last little request... (it's not that a problem that big, but quite annoying)

When i click "Data Files" in the MW launcher, all i see are boxes ticked.
Normally you'd see the text next to it, but i do not. Even un-ticking is not possible (it still shows ticked)


Glad to see you up and running! I never thought about the Loki installer. About the mods, I think you can also add or remove them via Morrowind.ini. At the end of the file there should be a list of mods loaded in a certain order. Just delete the ones you want. If you add more mods, just remember to add them in the last position.

---

### Post by Iarwain ben-adar on 2006-07-07
Hi Miguel,
i'm happy too :D

About the .ini
Can i disable Tribunal?
The only reference i found is this:
```

[Archives]
Archive 0=Tribunal.bsa
Archive 1=Bloodmoon.bsa

<snip>

[Game Files]
GameFile0=Morrowind.esm
GameFile1=Tribunal.esm
GameFile2=Bloodmoon.esm
```


Iarwain

---

### Post by Miguel on 2006-07-07
OK, deleting the lines referencing tribunal.bsa and tribunal.esm and then changing the remaining numbers so that they stay in order should do the trick. If you are experiencing troubles, tell me and I'll fire up Morrowind from Windows, activate only Bloodmoon and send you the corresponding files.

On the expansions (I think free from spoilers):

 To access the island of Solshteim (sp?) you must either "swim"  or take a boat (this isn't a spoiler, since everybody tells you) from Khuul, far far far away from the village you start (Seyda Neen). So the regular game will remain identical to the original unless you want to access Bloodmoon things.

You can go to mournhold after certain event happen (the spoilers I mentioned). In one of the versions, I don't remember if it was Xbox or PC, this wouldn't happen until your character was level 6. After that, the decision of going to mournhold is entirely yours, and is separate from the main Morrowind, so the main quest is still "untainted".

One final word of advice. The way magicka works in TES3, if you want to play a pure mage (the toughest) your race should be either Breton or High Elf, and the sign either the apprentice or the atronach. 

So have lots of fun and good luck with your first character!

---

### Post by Iarwain ben-adar on 2006-07-08
Deleting the lines worked :D

Thanks for the info ;)

btw: i'm a sneaky dark elf :D


Iarwain

---

### Post by lenin69 on 2006-08-23
> **Iarwain ben-adar said:**
> Meh,
It's installed and such, no errors there.

Just when i try to start the game, (via console)
i get this:
```
iarwain@iarwain-desktop:~/morrowind$ ./morrowind
iarwain@iarwain-desktop:~/morrowind$ Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2979, in ?
    gddb_file = detected[0]
TypeError: unsubscriptable object

```

EDIT: nevermind about that error (got it solved by changing the original Cedega install path to the loki install path)

Game plays (FINE!)

Now, one last little request... (it's not that a problem that big, but quite annoying)

When i click "Data Files" in the MW launcher, all i see are boxes ticked.
Normally you'd see the text next to it, but i do not. Even un-ticking is not possible (it still shows ticked)

I'm gonna upload an image, but it will take a while (stupid dial-up)

EDIT2: here it is 
[[IMG]http://img178.imageshack.us/img178/683/mw0ay.th.png[/IMG]](http://img178.imageshack.us/my.php?image=mw0ay.png)


Iarwain


ok, but... who i change the original install path?

---

### Post by Iarwain ben-adar on 2006-08-23
Hi,
the path that cedega installed to (likely something like ~./cedega/Morrowind)
 => to the path where you installed the loki morrowind :D

You can change that by starting cedega, selecting Morrowind, then selecting Morrowind (the link) and then clicking the Proporties button :D


Iarwain

---

