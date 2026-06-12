---
title: "CSS with DirectX 8.0 only?"
date: 2005-12-16
forum: Gaming &amp; Leisure
---

### Post by ubu-for on 2005-12-16
First of all ...

... my hardware:
Abit KN8 SLI
AMD64 4000+
OCZ DIMM 1 GB DDR-400 Platinum EL
NVIDIA 6600 GT, PCIe, 256 MB
Samsung SP2504C, SATA II

... my software:
Ubuntu 5.10, 32bit
nvidia-glx 1.07667
kernel 2.6.12-9-k7
wine 0.9.3
winetools (Windows Version: Windows ME)
CSS (56 FPS)

Does anybody know, why CSS shows only DirectX 8.0 as hardware mode and DirectX 9.0 as software mode?

The problem is that the game looks like DirectX 8.0, too. Maybe it's only because of the video settings? My CSS standard-setting: texturedetails = low

But everytime I've changed the video settings, CSS crashes! Does anybody know how to modify my "config.cfg" for medium or high texturedetails?

THX for your HELP!

---

### Post by Des33 on 2005-12-16
56fps.. ur lucky..

I have a AMD 3200+
NVIDIA 6600 GT
1gb ram..

and the things runs like shit... 5-10fps.. lol

---

### Post by ubu-for on 2005-12-16
[QUOTE=Des33]56fps.. ur lucky..[/QUOTE]

But still to slow for 1024x768 and low details (screenshot)! :(

CSS will look awful, but try this!
[http://www.ingame.de/filebase/index.php?action=file&cid=227&fid=2705](http://www.ingame.de/filebase/index.php?action=file&cid=227&fid=2705)

Copy this file to:
"Steam\Steamapps\#ACCOUNTNAME#\Counter-Strike Source\cstrike\cfg\"

Edit: "valve.rc" and add:
exec tweaks.cfg

Remove for "valve.rc" the right to be modified.

Now you should get more FPS! (56->131)

---

### Post by Rizado on 2006-05-16
[QUOTE=ubu-for]But still to slow for 1024x768 and low details (screenshot)! :(

CSS will look awful, but try this!
[http://www.ingame.de/filebase/index.php?action=file&cid=227&fid=2705](http://www.ingame.de/filebase/index.php?action=file&cid=227&fid=2705)

Copy this file to:
"Steam\Steamapps\#ACCOUNTNAME#\Counter-Strike Source\cstrike\cfg\"

Edit: "valve.rc" and add:
exec tweaks.cfg

Remove for "valve.rc" the right to be modified.

Now you should get more FPS! (56->131)[/QUOTE]I tried it, the fps is alittle better, but everything is blue [img]http://ubuntuforums.org/images/liteblue/icons/icon11.gif[/img]
Also many options don't work if sv_cheats is on. It isn't on most servers.

---

### Post by krak on 2006-06-10
hey. i have follow that how to [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

ERROR MESSAGE IN ATTATCHMETN
i have radeon 9600pro drivers installed and working

---

