---
title: "Switch Terminal Server Client"
date: 2008-01-29
forum: Desktop Environments
---

### Post by Maarten78 on 2008-01-29
Hello,

I have a problem with switching between Terminal Server Client in Full Screen and Gnome desktop of Ubuntu 7.1!! 
I tried already with CTRL + ALT + Enter, that didnt work
I tried CTRL + Alt + LEFT/RIGHT, That didnt work as well, I tried many other combinations, but i never got the right  one.

Somebody help? :confused::confused:

Greetz,
Maarten
( a starter on Unbuntu)

---

### Post by Maarten78 on 2008-01-29
Any body?? :( :confused: :confused:

---

### Post by Abripl on 2008-02-13
None of those work for me either. I use UltraVNC on the windows server PC which has a "Kill all clients" option. Not very elegant but it works.

---

### Post by nineowls on 2008-04-09
Maarten,
I to have similar issue
With connection with Terminal Server Client via RDPv5 to Windows 2003 server on Active Directory domain 
Ubuntu or Terminal Server Client will not permit shift back to Ubuntu from full screened Windows (Ubuntu 7.10)
I got impatient and held down the Ctrl+Alt+Enter and observed terminal client minimize and be restored rapidly over and over and over.
I held down  Ctrl+Alt+Enter and added some other keys (left right arrow)
One of them broke through the Terminal Server cycle and switched me to my 3rd workspace in ubuntu
Not a great answer but best I can do at the moment

20080502: i switched to Gnome-RDP and switched to using Envy to manage graphics and resolution; Seems to have fixed it for me...

---

### Post by rpokane on 2008-04-29
Same problem here with 8.0.4 connecting to XPSP2.
nineowls suggestion works...but it ain't pretty!
As per the other topics on this issue, I do have "Desktop Effects - Compiz Setup" checked under Add/Remove Applications, but I do not see where to make the change.

From [http://ubuntuforums.org/archive/index.php/t-595384.html](http://ubuntuforums.org/archive/index.php/t-595384.html) :
1. The <Advanced Desktop Effects Settings (ccsm)> tool to configure your compiz settings have to be installed.
2. Start this tool under SYSTEM -> PREFERENCES
3. Under the category UTILITY -> WORKAROUNDS you have to deactivate the <Legacy Fullscreen Support> which makes Wine and legacy applications fullscreen properly.

Nor do I know how to change to metacity...yet :)

---

