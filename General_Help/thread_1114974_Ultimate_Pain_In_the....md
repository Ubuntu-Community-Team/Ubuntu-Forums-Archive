---
title: "Ultimate Pain In the..."
date: 2009-04-03
forum: General Help
---

### Post by LawC on 2009-04-03
Hello Ubuntu friends:
   I'm in the prosses of converting a friend over to Ubuntu. All is well except that she requires Ultimate Bet, which is of course windows only. I have it sorta running - it's quite slow, and the window has rendering issues that I'm still trying and hoping to sort out.
   I'd love some help with that too, but I'm posting today to see if someone could help me put an icon on her desktop to shut down wineserver. With only 512 megs of ram, once you run Ultimate bet and shut down, the computer is real slow. I went to system monitor and found "wineserver" hogging a few hundred megs of ram - so I killed it. She's not skilled enough to repeat those steps, so I'd like help creating some sorta terminal program to kill "winserver" and place an Icon to it on the desktop so she can click it when she's done with ultimate bet.

Wish me luck with this Ultimate pain thing. If I can't get it running half decent I'll be forced to re-install that other OS.

---

### Post by paradigm2 on 2009-04-03
> **LawC said:**
> Hello Ubuntu friends:
   I'm in the prosses of converting a friend over to Ubuntu. All is well except that she requires Ultimate Bet, which is of course windows only. I have it sorta running - it's quite slow, and the window has rendering issues that I'm still trying and hoping to sort out.
   I'd love some help with that too, but I'm posting today to see if someone could help me put an icon on her desktop to shut down wineserver. With only 512 megs of ram, once you run Ultimate bet and shut down, the computer is real slow. I went to system monitor and found "wineserver" hogging a few hundred megs of ram - so I killed it. She's not skilled enough to repeat those steps, so I'd like help creating some sorta terminal program to kill "winserver" and place an Icon to it on the desktop so she can click it when she's done with ultimate bet.

Wish me luck with this Ultimate pain thing. If I can't get it running half decent I'll be forced to re-install that other OS.

I would think that you could use a shell script (with a shortcut on the desktop) to do this.  Also it might be easier for her if you just make it one script that starts the program and then when she exits will automatically clean up.  So she just clicks once and that's it.  Just like windows.

Soemthing essentially like:

1. Start application in wine.
2. on exit, kill wineserver.

I'm not very good with scripts or familiar with scripting the wine startup so I will leave the specifics to someone else.  Perhaps there is also a config option in wine? Good luck.

---

### Post by LawC on 2009-04-03
> 
Soemthing essentially like:

1. Start application in wine.
2. on exit, kill wineserver.

I'm not very good with scripts or familiar with scripting the wine startup so I will leave the specifics to someone else. Perhaps there is also a config option in wine? Good luck.


Yeah, that's exactly what I'd like to do. Right now I'm working with the terminal and system monitor and trying to search and destroy everything that gets run by ultimate bet. I'm using pkill but it cant kill wineserver. It will kill "aphh.exe" "explorer.exe" and others. All that remains is to find more powerful kill for wineserver and then pack all the kills into one batch or shell script of some sort and place an icon on the desk. I have no idea how to make such a file.  I'm also begining to wonder if I've overlooked a setting in wine somewhere. I find it hard to believe software could be so stupid as to leave everything running in memory when you quit. ...Allthough it is windows stuff...so...!

More help please! I'm only at her house on Fridays. For now I'll just tell her to press Ctrl-Alt-Backspace to restart after running Ultimate Upset!

---

### Post by 3Miro on 2009-04-03
Shortcuts can exec commands, such as: killall -9 wineserver, however, it would probably have to be a separate shortcut.

You can also show her System -> Admin -> System Monitor ans reach for wineserver

---

### Post by albinootje on 2009-04-03
> **LawC said:**
>  I'd love some help with that too, but I'm posting today to see if someone could help me put an icon on her desktop to shut down wineserver. With only 512 megs of ram, once you run Ultimate bet and shut down, the computer is real slow.
RAM is pretty cheap nowadays, and I think I would prefer using MS-Windows inside VirtualBox to have some more memory-hogging control over it.
I think it's cool that a VirtualBox guest VM can be completely shut down right away with one mouse-click :)

---

### Post by LawC on 2009-04-03
> 
You can also show her System -> Admin -> System Monitor ans reach for wineserver


Yes, most users would be ok with that. She looked at me kinda cross-eyed when I began to tell her how. I think I lost her at "system monitor."

> 
Shortcuts can exec commands, such as: killall -9 wineserver, however, it would probably have to be a separate shortcut


That's almost working for me. I created an Application in Terminal and entered in the killall. Problem is that I need to kill several others first. There's aphh.exe, explorer.exe iexplorer.exe mainclient.exe and wineserver. It seems if I close ultimatebet it takes forever, but it closes. If I kill wineserver, I usually find explorer.exe and some of the others turned to zombies. I think I have to kill them in order...

> 
RAM is pretty cheap nowadays, and I think I would prefer using MS-Windows inside VirtualBox to have some more memory-hogging control over it.
I think it's cool that a VirtualBox guest VM can be completely shut down right away with one mouse-click

I doubt shell spring for more ram. She just wants facebook, msn messenger and Ultimate upset (Bet).

So far Ctrl-Alt-Backspace to restart looks like the best for her.

I'm pretty much outta time for this friday. I'd love to see if someone has a good solution that I can try for her next friday. At least I feel good knowing she's stuck with ubuntu for one more week.

Thanks for all your help today!

---

### Post by albinootje on 2009-04-03
> **LawC said:**
>  I doubt shell spring for more ram. She just wants facebook, msn messenger and Ultimate upset (Bet).

So far Ctrl-Alt-Backspace to restart looks like the best for her.

Shutting down VirtualBox is easier and much more elegant in comparison.

At work I'm trying to migrate a few desktops from MS-Windows to Linux, at with using Wine there was already an out of memory problem once.
With VirtualBox I've never seen a problem like that.
I do admit that Wine can be better integrated in the Ubuntu desktop than VirtualBox.

Good luck.

---

### Post by LawC on 2009-04-03
> 
Shutting down VirtualBox is easier and much more elegant in comparison.


Hummn, Can I get VirtualBox easily from synaptic package manager. I did type it in and I remember seeing a bunch of other related packages. It smelled like a headache to me... Perhaps I'll have to check up on it later.

Thanks for the tip: "albinootje"

---

