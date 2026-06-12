---
title: "Wine problem"
date: 2007-10-23
forum: Desktop Environments
---

### Post by ellis rowell on 2007-10-23
I was using v7.04 and could run two programs under Wine. I then upgraded to v7.10 and every time I try to use those programs (or even the Notepad, which it installed) the computer freezes and I have to switch of and boot up again. Anyone had this problem?

---

### Post by TeaSwigger on 2007-10-23
I haven't upgraded yet, so I can't offer any comment in that respect, sorry. But I can suggest some normal easy steps you might want to exhaust first.

What is the current version of WINE on your computer? Is it from the Gutsy repos? Point being to determine if there is a newer version or one specific to Gutsy, and if so to try it.

In a terminal, run wineprefixcreate. It'll be busy for a minute then say it's done. Then run winecfg. Check the configuration. When all that's set, try it.

To avoid the restart, you should be able to kill all WINE processes with a command: wineserver -k

Of course there's always doing a complete uninstall (purge) and reinstall of WINE and apps and see if it'll run then.

Luck :)

---

### Post by ellis rowell on 2007-10-24
I have tried complete removal and re-install. Complete removal does not remove the CCleaner which is installed and any attempt to use Wine results in a complete freeze (nothing works).

Another problem seems to be with Kontact. It displays the calendar OK but although it says there are 51 contacts it will not display them. Evolution displays them but does not display the calendar events.

---

### Post by TeaSwigger on 2007-10-24
huh how do ya like that. Well as I've never used them I can't comment as to the kontact / Evolution issue beyond suggesting that if one can do such a thing, export your data from each, then remove their config folders / files in your home directory. Upon starting the apps again, they should create new user configs; import your data and try 'em then.

On a similar note, by what method did you remove WINE? By 'sudo apt-get remove --purge wine'? And did you ensure all files including the .wine folder in your home directory were completely deleted? There could also be more left. From their home site [http://www.winehq.org/](http://www.winehq.org/)

> How do I uninstall Wine? How do I wipe the virtual Windows installation?
You can remove your virtual Windows installation and start from scratch by eliminating (or renaming) the hidden .wine directory in your home folder, such as with rm -rf ~/.wine 
If you want to remove Wine entirely after you installed it with your distribution's package manager, you can generally uninstall in the same way. Note, however, that uninstalling Wine will not eliminate the virtual Windows installation - to do that you must follow the instructions above. 
Since Wine is beta software, periodically we may update the default configuration generated when you first use Wine. Sometimes users have success getting an application to work by wiping (or moving) their ~/.wine folder, rerunning winecfg with the new Wine version, and reinstalling the application.

Otherwise stuff could be left over to mess up a WINE reinstall.

---

### Post by TeaSwigger on 2007-10-24
Hm, another tidbit from their site:

> If you are getting a complete deadlock and are unable to even use your mouse after running Wine, it's probably not a specific problem with the Wine software. Wine is a user-level process, and shouldn't be able to completely hang the operating system under any circumstances. Instead, Wine is likely exposing a deeper problem with the system, such as a defective hardware driver. 

There's also note that using Beryl/XGL/Compiz can interact badly with WINE.

EDIT: and finally, further word from wine-wiki.org:

> Computer Frozen
This is not likely the fault of wine read on to learn why: 
S. Richie [May 2007]: a few reports from users complaining about Wine deadlocking their system - keyboard unresponsive, with no solution but to restart the entire computer.[..] Wine is a user-level process, it shouldn't be able to cause a hardlock under any circumstances, right? 
S. Dossinger:Correct. The operating system must prevent user level apps from locking the system. So hard crashes are by definition NOT wine's bug. I think its not the kernel that crashes, rather the X server that fails to process new input. Often sshing in works, then you can kill the Wine process keeping the X server hostage or the X server itself and your system works again. That doesn't help the average user of course. 
M. Meissner: It is likely ATI or NVIDIA. But yes, a broken graphics driver can cause user apps to deadlock the machine.[Wine devel May 2007] 
D. Timoshkov [bug 9636 Sept 07]: Wine or any other user level applications should not be able to crash X server. This is an X server bug. D. Kegel [then recommended to]: check to see if you have an out of date proprietary graphics driver (nvidia or ati). They're the likely culprit. Also try 'glxgears' as a test app, it is as likely as wine to be able to crash a misconfigured X.

Therefore, suggest looking into your graphics card and related.

---

