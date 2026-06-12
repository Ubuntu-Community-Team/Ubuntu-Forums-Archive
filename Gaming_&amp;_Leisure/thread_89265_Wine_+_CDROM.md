---
title: "Wine + CDROM"
date: 2005-11-12
forum: Gaming &amp; Leisure
---

### Post by Uzari on 2005-11-12
I finally after a little work got Wine running on my comp, and got a game to install properly so far(WC3)

Now I was wondering, how do you set up the CDROM drive so that the game can read it? I tried adding [Drive D] into the config file with all the things I think it needs... and it still cant detect it. 
```
[Drive D] 1131768580
"Device"="/media/cdrom0"
"Filesystem"="winnt"
"Label"="CD-ROM"
"Path"="/dev/hdc"
"Type"="cdrom"
```
It changed order and added the number after I ran wine once with it in there, but it still doesnt work. Im guessing I did something wrong?

---

### Post by cluelessnoob on 2005-11-15
I have the same problem with Ubuntu 5.10 and wine .9.1

It runs but will stop when it tries to read the CDROM.  

A lot of advice on the net says to edit the wine config file and linking the CDROM, but it no longer exists I think... :( 

[COLOR="Red"]" In the past, Wine used a special configuration file that could be found in ~/.wine/config. If you are still using a version of Wine that references this file (older than June, 2005) you should upgrade before doing anything else. All settings are now stored directly in the registry and accessed by Wine when it starts."[/COLOR]

My cd is set right in winecfg and the path is right /media/cdrom0 ->d: 

I know my wine works and can install form the CDROM, but I still can't run Frozen Throne... i'm thinking DLL or registry problem? I might try the no-cd crack.

---

### Post by Synt4x_3rr0r on 2005-11-15
[QUOTE=cluelessnoob]I might try the no-cd crack.[/QUOTE]

I always use the no-cd crack and it works flawlessly. Although that was not in WC3, but it should be the same.

---

### Post by GIBson3 on 2005-11-15
[QUOTE=Uzari]I finally after a little work got Wine running on my comp, and got a game to install properly so far(WC3)

Now I was wondering, how do you set up the CDROM drive so that the game can read it? I tried adding [Drive D] into the config file with all the things I think it needs... and it still cant detect it. 
```
[Drive D] 1131768580
"Device"="/media/cdrom0"
"Filesystem"="winnt"
"Label"="CD-ROM"
"Path"="/dev/hdc"
"Type"="cdrom"
```
It changed order and added the number after I ran wine once with it in there, but it still doesnt work. Im guessing I did something wrong?[/QUOTE]


All I did (Wine 0.9.1)
```

cd ~/.wine/dosdevices
ln -s /media/cdrom d:

```

Then fire up WC3 (in my case WC2 BNE)

---

### Post by cluelessnoob on 2005-11-16
Finally figured it out from a previous post by tonderai


[COLOR="Blue"]
I had this strange error with Homeworld and wine (ver. 0.9.1) where the game would install fine from the cdrom, but would refuse to detect it when run - giving a 'invalid or missing homeworld CD error'. I finally managed to correct it

1.) Run winecfg and click 'autodetect' on the 'drives' tab, making sure your cdrom drive is listed.

2.) Run regedit and go to HKEY_LOCAL_MACHINE/Software/Wine/Drives. Set the 'data' field for D: (or whatever drive letter your CD drive is set to in winecfg) to 'cdrom' instead of 'hd'.

Homeworld now recognises the cd and runs![/COLOR]
[COLOR="Black"] 
I also had a problem with it crashing at start up but I moved my movies folder and installed the Nvida drivers.... hope this helps!

[/COLOR]]

---

