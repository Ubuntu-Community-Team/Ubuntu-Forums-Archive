---
title: "Runes of Magic"
date: 2016-01-09
forum: Gaming &amp; Leisure
---

### Post by heroquestelf on 2016-01-09
I was informed today that Runes of Magic ran very well in Wine, so, having an account, I decided to install it. It got all the way to the update stage and froze, and I can't get it past that stage.

The documentation on the Wine page that talks about installing RoM ( [https://appdb.winehq.org/objectManager.php?sClass=version&iId=16051](https://appdb.winehq.org/objectManager.php?sClass=version&iId=16051) ) has it listed as "Gold", but it contains the following documentation... and while I know how to do all this in Windows, I haven't a clue how to do it in Ubuntu. Could someone please translate this for me?

> Install Wine (tested with 1.5.1 32 bits Debian sid)& winetricks (for Debian sid 32bits need to patch wineserver patch from /usr/lib32/wine-unstale to /usr/lib/wine-unstable or make sln)
Install .net 2.0 or mono
Install DirectX 9
Install corefonts
vc2005, 2008, 2010 (Have 3 installed for cross compile, no idea what one is working)
All IE family (needed by updater/launcher), what one is working, I don't know because have all installed

Install the game (tested with slim installer), with shortcut created on desktop
Edit shortcut ... end of command shall looking like: 
                          Runes of Magic.exe" -game -opengl
Call regedit and now be careful because error of typo & ....


--------------------------------------------------------------

Add the following to HKEY_CURRENT_USER\Software\Wine\Direct3D (create if it doesnt exist)

Add New String
Name = Multisampling
Data = enabled

Add New String
Name = UseGLSL
Data = disabled[TABLE="width: 100%"]
[TR="class: howto"]
[TD][/TD]
[/TR]
[TR="class: notetitle"]
[TD][/TD]
[/TR]
[/TABLE]
 

Note: I have Wine 1.6.2 with Winetricks, and I know how to change the RegEdit key. I just have no clue how to install .net 2.0 or any of the others.

---

### Post by MikeCyber on 2016-01-10
Very easy, fire up winetricks, click default wineprefix - install a windows dll - now you scroll down and select all you need

---

### Post by heroquestelf on 2016-01-10
Will it matter that Runes of Magic is not installed in the default location? 

For example, RoM is installed in Home/PlayOnLinux's virtual drives/RunesOfMagic

---

### Post by MikeCyber on 2016-01-10
Yes, you can tell wine/winetricks to use other prefix but I haven't tried. Playonlinux is easier for having multiple versions aside.
[http://askubuntu.com/questions/184674/how-do-i-tell-winetricks-to-work-with-a-different-prefix](http://askubuntu.com/questions/184674/how-do-i-tell-winetricks-to-work-with-a-different-prefix)

---

### Post by Thunder_Beaver on 2016-01-15
This looks like a good game. Reminds me of World of Warcraft slightly. Have you been able to play it smoothly, yet @heroquestelf?

---

### Post by heroquestelf on 2016-01-15
It's a lot like WoW. The only real bad thing about it in my opinion is that the crafting system is sub-par. Other than that, I've really enjoyed it.

And no. I spend 80% of my time on my Windows 10 desktop anyway, so I decided that it wasn't worth the headache. If I ever get to the point where I need to spend some time away from home I may try again to re-install it, but for the time being I put it on the back-burner.

---

### Post by Shane_Mundee on 2016-01-15
Wow, ok yeah, i've been looking for a game like WoW, at least until the Legions expansion arrives. I tried to play Rift, but it wasn't up to par with WoW even though it's a good game. 

What do you guys think ?

---

