---
title: "VMWare Gaming"
date: 2008-11-09
forum: Gaming &amp; Leisure
---

### Post by Drezard on 2008-11-09
I want to swap completely over to linux (as I have just been hit with yet another browser attack on windows) but, I still wana play the odd game of Battlefield 2, Halo and the likes. I have a fast enough machine (Quad core, 4Gb Ram, 8800GTX) im wondering whether I can play these games in a VMWare with XP installed in it? Cause then I would be mostly free of windows! (Yay!). 

Daniel

---

### Post by phillik747 on 2008-11-09
I could be wrong but I wouldn't think that VMWare would be able to handle the graphics required for games like Battlefield 2.  Your best bet would be to look into Wine.

Check this out:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438")

---

### Post by scheuri on 2008-11-10
3d-Gaming is NOT possible with virtualisation (that includes VMware, Virtualbox and the stuff).

As long as the virtualisation software (you know, the stuff that "emulates" the drivers and the hardware within the virtual OS) is not able to directly address the real hardware, there will be no real 3D-gaming within virtualisation.

Well, that is at least what I know, that might be very well wrong.
However, fact is...no, will not work at this time (and very likely not very soon in the future).

Cheers
scheuri

---

### Post by dreamer84 on 2008-11-10
I had the darwinia-demo run under virtualbox, though very slow... but I read they want to implement 3d support. someday. anyway...
If your machine is fast enough, you could try [Transgaming's SwiftShader]("http://www.transgaming.com/products/swiftshader/"), which completely emulates a shader 3.0 card. On your CPU, so don't consider this to be a solution for newer games. And the demo has a nasty watermark... But try it, I'd like to know whether it runs fast enough on a newer PC (which I currently don't have...)
Or you could just try wine, cadega or crossover games instead of a fully overloaded emulator...

---

### Post by xeriouxi on 2008-11-10
I believe VMware Fusion has experimental support for DirectX 9.0 graphics but no shader support. Obviously this will rule out a lot of newer games that depend on shader support, but it's a step forward at least! =)

---

### Post by OnePost on 2008-11-18
Just registered for this one and only post:
Goto [http://www.vmware.com/support/pubs/ws_pubs.html](http://www.vmware.com/support/pubs/ws_pubs.html) , download the "Workstation User's Manual", follow the instructions on page 165 ff. to install DX9 and be happy if all your DX9 games are running now.
Latest Workstation tools version 6.5 required.

\\:D/

---

### Post by Panties on 2010-04-05
VMware 7, is able to handle 3D. Although I still believe that its an experimenting stage, but I play World Of Warcraft in it, by far, its fine.
 
Im using Geforce 295.... I tested Cedega, Wine and VMware.. Cedega/Wine works fine, really!
IMHO, I prefer VMWARE....

Thats just me...

---

### Post by xDonny on 2010-04-08
I have played Counter Strike: Source on Cedega for awhile and it works just fine for me. I've never played Battlefield but I know it's a first person shooter.
 I have an HP Pavilion DV6800 with a NVidia GeForce 7150M / nForce 630M integrated video card and it works fine on this piece, So the specs of your computer should be plenty to play Battlefield.
 [http://www.cedega.com/gamesdb/games/view.html?game_id=3618](http://www.cedega.com/gamesdb/games/view.html?game_id=3618) You're in luck! Battlefield 2 seems to work fine on Cedega. Although you have to pay for the full version I would say it's money still spent if you're a gamer like myself. 
Hope this helped!

---

