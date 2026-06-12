---
title: "Wine: running the same game twice!!!"
date: 2007-05-07
forum: Gaming &amp; Leisure
---

### Post by Sugi on 2007-05-07
I was wondering if it's possible to run the same game twice through wine or any other program??  
I have try:
 - just opening it twice.  didn't worked.
 - opening it twice, one with iso mounted and one with cd mounted

theories:
 - installed twice, but two different dirs. same mount (or different mounts)
 - open with wine and open with crosscrover (or something like that,  maybe different dirs, too.  even different mounts)
 - open with wine, and then in a virtual box just run it through xp or vista or something.

I was wondering if anyone has try any of my theories.  Any of them worked?  I have only tryed doing these dual boxings (i've only try running multiple copies of the same game with diablo 2 LOD.  i haven't tryed anything else yet.)

I've done some research on this topic, and have found nothing.  Hopefully my research was incomplete and theres information out there on this topic.

let me known if anyone gets any out come of this crazy test.

---

### Post by Sugi on 2007-05-08
Bamp.  I've tryed this, and i don't think it's working for me.  >.<

---

### Post by hikaricore on 2007-05-08
For most applications (even in wine) this should be possible, be aware however that CPU, GPU, and memory intense applications will probably run very slowly unless you have the hardware to handle such applications.

---

### Post by Sugi on 2007-05-08
how would i get this to work though???  some games say that the game is already open.  would i have to have two directories for each game i want to do this with?

---

### Post by calgarystevens on 2007-05-08
One thing I do is: after I get a game working the way I like (Steam/CSZero for example) I go to my Home folder, then go to 'view' and 'show hidden files' on the menus. Then I look for the folder called .wine (notice the dot-hidden folder) and I rename it to .wineczero so it is now a separate entity. Then you need to change your shortcut to the program (CS Zero or whatever) to look like this: env WINEPREFIX="/home/dad/.wineczero" wine "C:\Valve\Steam\steam.exe" -applaunch 80

The important part is the WINEPREFIX part, it now knows to start the program from that new folder we made. Then, to install your next game/program first you go to the command line and run winecfg and set up the new wine directory, then install like normal and run like normal. You can do this again, for example I have Hoyle Card Games in it's own dir too, it looks like this: env WINEPREFIX="/home/dad/.winehoyle" wine "C:\Program Files\Encore\Hoyle Card Games 2007\HoyleCardGames2007.exe".  Also if you want to fiddle with the sound settings or regedit.exe or anything for a wine directory you've changed you can simply run from the command line this: env WINEPREFIX="/home/dad/.winehoyle" winecfg  or env WINEPREFIX="/home/dad/.winehoyle" wine regedit.exe

I hope this helps, it will allow you to have many different wine configs going, and should let you run the same game 2, 3 or many times from their own virutal installs.

Edit: Be aware though, that any game that claims the video card (or uses OSS sound drivers) will probably never run twice! It needs full and exclusive access to the video screen, the same goes for say, a game and a dvd playing for example.

---

### Post by Sugi on 2007-05-08
let me know if im incorrect or anything.  for me to run two games, i should do this following command line
env WINEPREFIX="/home/funsack/.diabloii-dir**1**" wine "C:\Program Files/Diablo II-dir**1**" -applaunch 80
then to run the second one i would do this,
env WINEPREFIX="/home/funsack/.diabloii-dir**2**" wine "C:\Program Files/Diablo II-dir**2**" -applaunch 80

I would have to creat two directories, and creat those folders called "*/home/funsack/.diabloii-dir**1*** and */home/funsack/.diabloii-dir**2***"

In these ".diabloii directories" are there mounts images or something in the folder.  I guess i just don't understand what you put in there for yourself to need boot from that and then run from this folder "C:\Program Files/Diablo II-dir2".  Im kinda confused.

Oh by the way, whats this "-applaunch 80"  and can i still add "-w" at the end.  like so, 
 "II-dir**2**" -applaunch 80 -w"

Thanks for the information.

---

### Post by calgarystevens on 2007-05-09
Ah, OK, I see what's confusing you. Mine was just an example using the launcher for Condition Zero under Steam. It has nothing to do with Diablo 2. For your situation you would need to install Diablo 2 in wine, get it working perfectly (by itself). Then go and copy your wine directory so you'd have one dir called .wine and another called .wine2

Then you can try your mad experiment by starting Diablo2 the usual way, probly: wine "c:/program files/diabloii/diablo2.exe" or whatever and then env WINEPREFIX="/home/yourname/.wine2" wine "c:/program files/diabloii/diablo2.exe" for the second one. Good luck, I highly doubt two will start at once, but you never know. Why on earth are you trying to do that anyways? Just out of curiousity...

---

### Post by God Of Atheism on 2007-05-09
In reply to the question why someone would want to run Diablo II twice, I can think of the following options:
1. Self rushing
2. Muling

However, I think that neither works for cattle.net, unless you happen to have two (or more) cd keys. For single player, it only makes sense for self rushing, since for muling you're better off using Atma.

In addition, if I understand the explanation correctly, you can only get the two (or more instances) as described in the instructions above running, if you run the game in a window, otherwise it will demand exclusive access to the graphics card.

Also, I want to add that my experience with running two different programs simultaneously using wine were not very good. The programs in question were Diablo II Lod and Atma. But I used the exact same settings for each, not a separate copy with other wine settings. Shouldn't one running copy of the Wineserver be able to deal with multiple programs accessing it? Many programs do demand exclusivity in the sense of not allowing a second copy of the same program to run, however, different programs should not give a problem, but do in my experience.

---

### Post by Sugi on 2007-05-09
should i copy the whole .wine folder to a dir called '.wine2" everything from diablo 2 to other programs i installed into .wine??

if this works, then im gonna do the same thing for other games.  within diablo 2, one account hosts and the other joins.  trading between accounts, muling and serving like possibilities.

I also wanna do the same thing in lineage.  running multiple accounts from one computer.

this is pretty much for the internet use.  it would also work in lan games.

---

### Post by Sugi on 2007-05-11
> However, I think that neither works for cattle.net, unless you happen to have two (or more) cd keys. For single player, it only makes sense for self rushing, since for muling you're better off using Atma.

Whats atma?  I went to the website, but it just confused me >.<

---

### Post by smutch on 2007-05-11
I currently have diablo 2 LOD running twice on my computer. Unfortunately this computer isn't a Ubuntu box but I don't see any reason why it shouldn't work so I'll describe what I did. (I'm really just a ubuntu noob so don't slam into me too hard)

First I added a new user called diablo then I logged in as diablo and installed the game using one set of cdkeys. Once it was running fine I then logged in as myself and did the following in a xterm:

-> chmod 666 /dev/hda  
   This allows any user to access the cdrom. Without this the diablo user won't find the cdrom
-> chmod 666 /dev/nvidiactl 
   Video replay or something like that.. not sure but without this the inter-act movies will make diablo crash. I still get diablo freezing on me so there must be something else I have to setup but it's beyond me at the moment. I do believe it has to do with openGL or so my friend the linux guru has theorized.
-> su - diablo
   Logs in as diablo user in user diablo's environment
--> cd .wine/drive_c/Program\ Files/Diablo\ II/
--> wine "Diablo II.exe" --display :0 -- -w
   This tells wine to display the video on the screen of the user logged into the 1st xsession and the -- -w makes diablo run windowed. You might need to a xhost localhost to allow anyone on your box display on the X Server. I don't have to for some reason even though my access control in enabled.

I then installed DII using another set of cdkeys and got it working. I run this one full screen since for some reason when diablo is run windowed everything appears a heck of a lot darker.

Maybe someone with more knowledge can explain this better than I can. I tried different ways including setting the wineprefix but for some reason never got that to work. Every time I went to run it I'd get a you need to install Diablo II before you can install LOD. I'm not sure why but whatever. I've self rushed about 10 characters through to the first quest in act 5. I don't have the equipment to rush hell yet.

---

### Post by Caseyjp on 2007-05-11
How I run two copies /accounts of EVE via wine:

install game, and then copy the /drive_c/Progarm Files/CCP/* to /ccp2 (also in the same wine directory under program files.

Create 2 launchers.

Command in 1st launcher: wine explorer.exe /desktop=1,1280x800 /home/casey/.wine/drive_c/Program Files/CCP/EVE/eve.exe

Command in the 2nd launcher: wine explorer.exe /desktop=2,1280x800 /home/casey/.wine/drive_c/Program Files/CCP2/EVE/eve.exe


These two launchers run start EVE in a 1280x800 desktop window (the game thinks its fullscreen which keeps frame rate high.)

See my "cube" link in the signature for the result.

---

