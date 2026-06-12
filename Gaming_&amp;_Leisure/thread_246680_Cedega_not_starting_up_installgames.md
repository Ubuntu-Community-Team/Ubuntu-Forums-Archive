---
title: "Cedega not starting up install/games"
date: 2006-08-29
forum: Gaming &amp; Leisure
---

### Post by g00fy on 2006-08-29
Hi,


I just reinstalled my comp (Dapper), but kept my /home directory (drive).
Before I could install games and play them with Cedega.

Now, however, I seems not be able nor to install, nor to play them at all...


When I press the 'install' button, I click on browse, point to the installation file (EVE_3900.exe in my case), and hit 'continue'.

Nothing happens, but in the console when I do this:
```
comp@comp-desktop:~$ ps ax | grep wine
27321 ?        S      0:00 /bin/sh /home/comp/.cedega/.winex_ver/winex-5.2.5/bin/winex3 --monitor-cdrom-eject --debugmsg -all -use-dos-cwd /home/SORTED/Inside/Games -- /home/SORTED/Inside/Games/EVE_3900.exe
27332 ?        Sl     0:00 /home/comp/.cedega/.winex_ver/winex-5.2.5/winex/bin/wine --monitor-cdrom-eject --debugmsg -all -use-dos-cwd /home/SORTED/Inside/Games -- /home/SORTED/Inside/Games/EVE_3900.exe
27335 ?        Ss     0:00 /home/comp/.cedega/.winex_ver/winex-5.2.5/winex/bin/wineserver
27337 ?        S      0:00 /home/comp/.cedega/.winex_ver/winex-5.2.5/winex/bin/wineserver
27340 pts/0    R+     0:00 grep wine
```


So it seems to have started installing. I tried other versions of Cedega, but no luck (the version it worked for me earlier was 5.2.1, but no such luck either).

I ofcourse have my previous EVE installation still lying around (as I kept my /home-dir), so when I click the 'play' button, it just doesn't do anything. But it seems doing something because if I do a grep again, I get about the same results...

Running cedega from the commandline doesn't help, and doesn't show any errors...


What could be the issue here? I'm pretty sure it's something obvious I missed in Ubuntu, but I don't know what... 


Greetz

---

### Post by mlind on 2006-08-30
Try to start a installed game with **-debugmsg +warn**.
What's the ouput of command **groups** ?

---

### Post by g00fy on 2006-08-31
```
/bin/sh /home/comp/.cedega/.winex_ver/winex-5.2.5/bin/winex3 --debugmsg -all -- "C:/Program Files/CCP/EVE/eve.exe" > ouput.txt 2>&1
```

After a lot of fiddling with configuration files (which I don't like as I thought Cedega does it's thing by itselves).

What I did in fact is modify the called winex3 to modify some default environmental variables... Maybe I will just remove every trace of Cedega from my machine and reinstall it. And then use the normal way to use environmental variables. Because now I know it works at least that way.

Games/Install's does not load up yet, but what I get now is different:
When I add +warn to the command line:
```
/home/comp/.cedega/.winex_ver/winex-5.2.5//winex/bin/wine: cannot find '+warn'
```

And when I run it without it:
```
wine: Unhandled exception, starting debugger...
```

When I run it with -debugmsg +warn it gives:
```
fixme:win32:PE_CreateModule Load Configuration directory ignored
wine: Unhandled exception, starting debugger...
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.
```

And then nothing happens (returns to command prompt).


'groups' output:
```
steven adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```

---

### Post by justin whitaker on 2006-09-01
EVE runs, but takes alot of tweaking. 

[http://transgaming.org/forum/viewtopic.php?t=6733](http://transgaming.org/forum/viewtopic.php?t=6733)

That thread has some insight into some setting that might work.

There is also a long thread on it here:

[http://transgaming.org/forum/viewtopic.php?t=84](http://transgaming.org/forum/viewtopic.php?t=84)

---

### Post by g00fy on 2006-09-01
Hi Justin,


Thanks for the threads, but there are both (as far as I can read) about EVE crashing at some point, freezing, and how to play it...

I just can't get it working at all... I saw somewhere else that people had the same problems after their upgrade to Dapper. And I think I remember it was before I did the upgrade I could still play EVE. Now it starts up (I see it in the output of 'ps'), but no window or nothing shows up.


[edit]

... Ok ... I don't know what I did, but I just uninstalled everything, moved everything out of the way (deleted /usr/lib/transgamin* and the .cedega, .cedegarc, .transgaming_global). Now I get the splash screen of EVE. And then a black screen with nothing on it... (ow, and the settings from the 1st post doesn't work here :().


Any help would be hugely appreciated!


Greetz

---

### Post by g00fy on 2006-09-02
Ok everyone...

I found it myself (the hard way ;)).

I started cedega with "-debugmsg +warn" from the command prompt. And first I thought all the 'fixme' I was getting were the real error. Then I saw some Dir-errors...

Long story short... Found out I needed to create a 'Fonts' directory under the windows-directory of the Cedega profile...

Gone black screen and hello space :D


Thanks to all here ;)

---

