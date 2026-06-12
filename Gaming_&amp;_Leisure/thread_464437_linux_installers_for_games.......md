---
title: "linux installers for games......"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by techno-mole on 2007-06-04
hello.
ok my question is that is there an installer for x2 the threat (i have the windows version) something along the lines of the loki installers maybe ? or is there a way to install the windows version on ubuntu ? like you can with never winter nights ?
and if a way exists could someone point me in the right direction please :D
cheers

---

### Post by murlosad on 2007-06-04
According to [WineHq.org]("http://appdb.winehq.org/appview.php?iAppId=3213") you can install it with wine or probably cedage. This is what you would use for never winter nights I believe. Wine works great for most windows games, there are lots of threads around here for help. I personally use wine to run Warcraft 3, Warcraft 2, and occasionally Starcraft. All work as well or better than they do in windows.

If you need to install wine you can use Synaptic, or if you have Easy ubuntu or Automatix they should do it for you also. Or you can install it my favorite way by opening a terminal and typing 'sudo apt-get install wine' :)

once you have wine installed run 'winecfg' either from your menu (I believe it will be under 'System Tools') or again from a terminal. You just want to double check and make sure it maps your drives correctly and you probably want to change the windows version to WinXP.

This next part works best from a terminal window (Applications >> Accessories >> gnome-terminal)
Browse to your cdrom (or where ever you are installing the game from) e.g. /media/cdrom by typing 'cd /media/cdrom' in your terminal.  Then to launch the installer you just type 'wine' and the name of the executable, e.g. 'wine install.exe' or 'wine setup.exe'.

Sorry if this was a bit simplistic, but I don't know your level of linux experience and want to make sure I gave you enough information.

Hope this helps.

---

### Post by Josey on 2007-06-04
[http://liflg.org/?catid=6](http://liflg.org/?catid=6)

---

### Post by techno-mole on 2007-06-05
you can install never winter nights with out using wine, theres details on the bioware website, all you need is the discs, same principle as doom3 and others.
cheers for the link, but there isnt a loki installer for x2, i checked first.
cheers for the help, i shall do some more google searches.
cheers

---

### Post by techno-mole on 2007-06-05
i forgot to mention that im looking for an installer along the lines of the loki installers and such like because wine and cedega dont run on my system, ive tried installing both of them several times and neither will run, cedega wont install anything, it gets so far and thn just stops, and wine locks my system up totally and the only way i can get out is to press the reset button on the pc case because nothing else works.
never mind though, where theres a will theres a way :D
cheers again.

---

### Post by cogadh on 2007-06-05
X2 can't run natively in Linux like NWN can, it requires Microsoft DirectX libraries while NWN does not. You will have to use Wine, Cedega or CrossOver to run it. 

If Wine is locking up your system, then chances are you have a Wine configuration problem. The most common config issue is usually drive detection, run "winecfg" and check the "Drives" tab. I don't use Cedega or CrossOver myself, so I can't comment on them.

---

### Post by techno-mole on 2007-06-06
i cant run anything with wine, ever since i switched over to linux ive been trying to install wine, i couldnt get it to work on edgy and i still cant get it to work now im on fiesty.
ive started many threads regarding wine and why it wont run on my system, and ive come to the conclusion that theres something on my system it doesnt like, dont know what though.
i cant run any command to do with wine as they all have the same effect, basically they all lock the system and i have to restart.
my best bet for running games is to try and get cedega to work properly or maybe try cross over, wine just wont have it, ive spent about a week so far trying to research why wine wont work for me and im still at a total loss with it.
cheers though.

---

### Post by cogadh on 2007-06-10
Sorry for not responding sooner (went away for a while).

When you try running Wine, is there any output in the terminal? You should see a bunch of "FIXME" messages and other nonsense. Also, post your system specs, maybe someone will see something that Wine is reacting to.

In all honesty, I have never known Wine to not work. The applications I have been trying to run through Wine might not work, but Wine itself has always worked.

---

### Post by techno-mole on 2007-06-12
no, no output at all in terminal when i try and run wine, its a strange one, many people have said that it should run and like ive said in many posts/threads no the subject it just wont have it, ive tried installing it through auto matix/apt-get/ and from source and all the other ways of installing it and all to the same end, the system lock i mentioned, and no one seems to know why it wont run and it seems im the only person that has this specific problem with it.
i have tried cedega and it will install, but i cant actually get a game to install properly, that is to say that i can start the install process and it will go so far and then stop, and the game wont install.
it wouldnt have anything to do with they way i have my system setup would it ? i have 2 sata drives, one with ubuntu on and this one is set to boot first, and the other has xp on it, i wondered if because of the xp drive whether wine/cedega are some how registering the files that they would set up and therefore not working or crashing ?
cheers

---

### Post by cogadh on 2007-06-12
No, that shouldn't be an issue. Wine won't even be aware of your pre-existing Windows installation, since Wine no longer requires a Windows install to be present. Besides, plenty of us, myself included, have a system that is set up like yours (dual boot Windows/Ubuntu) and we don't have any problems.

One question; do you have a 64-bit processor and if so, are you using the 64-bit version of Ubuntu? The reason I ask is Wine does have known problems running on 64-bit systems but will usually work fine if you switch to the 32-bit version of Ubuntu.

---

### Post by techno-mole on 2007-06-13
i do have a 64 bit cpu, but im running the 32 bit version of ubuntu, i have tried the 64 bit version but it caused issues with getting things to run properly as there seems to be more support for 32 bit systems than there is for 64 bit (which is the same under windows, i have a 64 bit version of xp, but the support in terms of drivers etc is diabolical, its better with linux though)
cheers

---

