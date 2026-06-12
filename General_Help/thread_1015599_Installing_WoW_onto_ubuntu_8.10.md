---
title: "Installing WoW onto ubuntu 8.10"
date: 2008-12-19
forum: General Help
---

### Post by Firedrake445 on 2008-12-19
I am trying to install wow to ubuntu after getting rid of the  windows parrtiton ( i had dual booted in the past so i could confirm that ubuntu would work. so far i got the installer off the disk along with the rest of the files on the disk and have put them on my hard drive. when i try to run the installer through wine i get a message that reads: "No installer data could be found."

when i run it through terminal( after the "wine Installer.exe" command)
i get a message that reads:

firedrake445@firedrake445-laptop:~/Desktop/wow$ winfixme:richedit:IRichEditOle_fnGetClientSite stub 0x14d32a8

and then another line that reads: fixme:ole:OleCreateStaticFromData (not shown), stub!

what can i do to get wow back on my system.

I have had wow on this computer before but i erased it when i got rid of the windows partition. I have the full game on a desktop computer if i can somehow copy the folders over to my ubuntu computer ( i dont have a flash drive larger than 4 GB). also is it possible to get a copy of windows onto another partition so i can re install the file to my hard drive using windows.

Please help i can not live without world of warcraft.

---

### Post by jerome1232 on 2008-12-19
If you have your install cd's you can just install it like you would on Windows. Pop open the cd and double click the setup.exe (or install.exe whatever it is)

---

### Post by Nakor BlueRider on 2008-12-19
There's a lot of info on wowwiki if you want to check it out.  It has a few methods you can try.

[http://www.wowwiki.com/Wine_(software)](http://www.wowwiki.com/Wine_(software))

---

### Post by Firedrake445 on 2008-12-19
> **jerome1232 said:**
> If you have your install cd's you can just install it like you would on Windows. Pop open the cd and double click the setup.exe (or install.exe whatever it is)

that does not work i get a feed back message from the software that reads: No installer file found

---

### Post by jerome1232 on 2008-12-19
Well I've installed about everyway you can, If you go to blizzards siteand login to your account management they have an installation tool you can download which will torrent the game data to your computer and install it (very big download though so only an option if you have fast internet)

If the Windows computer is on the same network as your computer you can just setup file sharing on the xp computer and transfer the files over the network to the ubuntu computer. You will need to install samba and probably smbfs on the ubuntu computer

```
sudo apt-get install samba smbfs
```

---

### Post by mfr1003 on 2009-03-26
Ugh!

I've had it up to here with this installation!

So I got the original game installed.  Now as the game is patching itself, I'm trying to install BC.  I've gotten that installer to FINALLY recognize that WOW original is installed, but when I scroll down on the EULA, the "Agree" button refuses to be clickable.  I've read that this is a bug, but no one talks about how to fix this installing BC- just WOTLK.  So here's what I've tried

CDs - It starts working then I get an error message as I replace the first disc with the second.  It complained that installer tome 2 was inaccessible to an unknown error (error 2 as the dialogue box so imaginably titled it).

Blizz's installer-  Again, I can't click the "Accept" button.

I read on someone's page to try IE4Linux-  I know what your thinking, so I've put that on hold because frankly I don't understand the directions.  I went to unbuntu to avoid steaming piles of crap like IE.  Go figure.

I don't have a DVD for it...I'd love to try, but I hear that gives even more troubles.

Can anyone tell me what I'm doing wrong?  I have dist 8.10 Ibex, and I'm on a HP dv8000x media center edition laptop.  I did the graphics rendering command, and I got back a "Yes," so I know it's not my Nvidia card.   anyone?

---

### Post by jerome1232 on 2009-03-27
To work around that bug with the eula update to the latest beta version of wine.

You can get that here

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

