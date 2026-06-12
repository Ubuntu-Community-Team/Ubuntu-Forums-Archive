---
title: "Installed apps not showing in the menus"
date: 2005-12-26
forum: General Help
---

### Post by rasmusbp on 2005-12-26
Hi,

I've been trying to install Wine through synaptic, including the "wine tools" which should provide a GUI for Wine. But after installation has finished, apparantly without problems, I can't find wine in any of the menus. 

I've experienced this problem with other programs that I've been trying to install. 

Can someone please help?

Many thanks,

Rasmus
Copenhagen, Denmark

---

### Post by Sutekh on 2005-12-26
Try
```
killall gnome-panel
```
to refresh things

---

### Post by 23meg on 2005-12-26
Also, some programs you install may not add themselves to the menu; you can add them manually using Applications / System Tools / Applications Menu Editor.

---

### Post by irv on 2005-12-26
Wine is one of those programs you don't run by itself. You need to run wine followed by the .exe file you want to run. So you won't want to run it off the menu.

---

### Post by GQed76 on 2005-12-27
Then why is there a GUI for it?  I have the same question.  How do you use the gui aspect of wine

---

### Post by kaamos on 2005-12-27
You can graphically start a file in wine by clicking on the file in winebrowser. To start this app, just type "winebrowser" in a terminal. You can also of course create a menu entry for this with the menu editor.

---

### Post by rasmusbp on 2005-12-27
Thanks everyone. 

When I put "winebrowser" in a (root) console, I get this, and nothing happens:
 
> 
root@ubuntu:/home/rasmus# winebrowser
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Usage: winebrowser URL
root@ubuntu:/home/rasmus#


---

### Post by kaamos on 2005-12-27
ok, the correct app is "winefile" not browser. Sorry about that.

Also, you shouldn't run wine as root.

---

### Post by rasmusbp on 2005-12-27
winefile works, thanks. 

i can't open any programs on my winXP partition using winefile, though. nothing happens when I click the .exe file, and this stuff happens in the console: 

> Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) Z:\media\hda1\Program Files\Mindjet\MindManager 6\MindManager.exe
        0000000f    0
        0000000e    0
        0000000d    0
        0000000c    0
        0000000b    0 <==
00000008
        00000009    0
WineDbg terminated on pid 0xa

Do you have any idea what's going on, and how I can fix it?

Thanks!

---

