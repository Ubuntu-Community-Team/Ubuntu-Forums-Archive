---
title: "newb to ubuntu"
date: 2006-12-17
forum: Gaming &amp; Leisure
---

### Post by SigmaX6 on 2006-12-17
hey sorry if this is the wrong forum but it is gaming related. im sorta losdt when peeps start talking about wine and cedega(emulators??). I dont really game but i do love a good starcraft or diablo 2. i have windows versions of both..i installed wine from add/remove programs but wine didnt show up in any applications directory? please help a newb out lol

---

### Post by wounded on 2006-12-17
Well Wine doesnt have a graphical interface (It's technically not an emulator either). I know D2 will run with wine as I have in the past set it up and it ran great but I don't recall any special things I had to do.

So to run something with wine you need to open a terminal (In gnome I think it's under Accessories in the Applications menu but I use KDE so I'm not sure if it is still in that spot) and then run "wine /path/to/install.exe" obviously change the path to where the setup program is on your D2 CD. Swap CDs normally and it should hopefully work. Do the same thing to install the expansion. Again, I don't know about the newest Ubuntu, but in Kde a "wine" menu appeared in my kmenu but you jight have to add it to the applications menu seperately.

Hope this helps a bit.

---

### Post by raul_ on 2006-12-17
Do you have a windows partition where the games are installed?

---

### Post by SigmaX6 on 2006-12-17
no i do not have any games installed. i was trying to get ubuntu to work with ntfs, but i remember a article a while back stating without some genius coding ntfs based partitions dont work. thnks for the replys, didnt know it was code based

---

### Post by SigmaX6 on 2006-12-17
sigma@sigma:~$ wine /home/sigma/Desktop/Starcraft/starcraft.reg
wine: creating configuration directory '/home/sigma/.wine'...
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
Failed to open the service control manager.
fixme:ole:ITypeInfo_fnRelease destroy child objects
wine: '/home/sigma/.wine' created successfully.
wine: could not load L"Z:\\home\\sigma\\Desktop\\Starcraft\\starcraft.reg": Bad EXE format for 
sigma@sigma:~$ /home/sigma/Desktop/Starcraft/starcraft.exe
bash: /home/sigma/Desktop/Starcraft/starcraft.exe: Permission denied
sigma@sigma:~$ 


im still alittle lost maybe someone could let me know what im doing wrong? If you notice at the top i tried adding a reg file to the "registry" so the game knows where to look for various files and the path for the cdrom](*,)

---

### Post by raul_ on 2006-12-18
You don't need to add the registry file. Just do
```


wine <installation .exe file path>


```

and you should be good to go

---

