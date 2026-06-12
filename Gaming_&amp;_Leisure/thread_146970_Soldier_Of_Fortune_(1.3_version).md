---
title: "Soldier Of Fortune (1.3 version)"
date: 2006-03-19
forum: Gaming &amp; Leisure
---

### Post by ninocass on 2006-03-19
Hi all, i had soldier of fortune running fine with wine but when i applied the 1.3 patch im getting this error

```

nino@laptop:~/.wine/drive_c/Program Files/Soldier of Fortune II - Double Helix$ wine SoF2MP.exe -w
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:keyboard:RegisterHotKey (0x20030,2,0x00000001,9): stub
fixme:keyboard:RegisterHotKey (0x20030,1,0x00000001,27): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.

```

has anyone sucessfully got SOF2 (1.3) to run under wine?

Thanks

Nino

---

### Post by ninocass on 2006-03-19
i had a hoke around and updated wine 

when i run single player i get:
```

nino@laptop:/media/storage/Programs/sof$ wine SoF2.exe
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:keyboard:RegisterHotKey ((nil),0,0x00000001,9): stub
fixme:keyboard:RegisterHotKey ((nil),1,0x00000001,27): stub
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {5959df60-2911-11d1-b049-0020af30269a}, hres is 0x80040154
fixme:keyboard:UnregisterHotKey ((nil),0): stub
fixme:keyboard:UnregisterHotKey ((nil),1): stub

```

Single player **WORKS** fully but when i run MP im now getting:

```

nino@laptop:/media/storage/Programs/sof$ wine SoF2MP.exe
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fdfca10)->((nil),00000008)
fixme:wininet:InternetGetConnectedState always returning LAN connection.

```

Multiplayer is not working :(

any ideas?

thanks

---

### Post by tribaal on 2006-05-30
Same problem.

Did you find a fix for that? I really feel left out, all my friends are playing together and I can't make it work under linux... :(

Cheers

- trib'

---

### Post by wolfiii on 2006-05-30
With cedega sof2 just runs fine.

---

### Post by tribaal on 2006-05-31
This doesn't really answer my concern.

- trib'

---

### Post by deathbyswiftwind on 2006-05-31
Mine works just fine with the installer from loki. The multiplayer I cant change the resolution but other than that everything runs great

---

### Post by tribaal on 2006-05-31
Thanks mate, I'll try the loki installer. Never heard of them before.

Is it just that? An installer that... makes the game work? :)

Cheers.

- trib'

---

### Post by deathbyswiftwind on 2006-05-31
Hey man here is the page you need [http://www.liflg.org/]("http://www.liflg.org/?catid=7") Loki was some great guys. They were the ones who had ported quake 3 way back in the day. Anyways yes it is an installer. It adds its own scripts into the game and uses the packs from your cds to make a fully functional game. Works great! Check out the site the whole way they got a pretty good amount of games.

---

### Post by tribaal on 2006-05-31
I got the link by googleing, but thanks again for pointing this site out to me, it's really  a great ressource for many games!
It's like automatix for games :)

Thanks again :)

- trib'

---

