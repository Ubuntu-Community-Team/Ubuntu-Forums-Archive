---
title: "Steam/WINE on Dapper"
date: 2006-10-20
forum: Gaming &amp; Leisure
---

### Post by Sklasko on 2006-10-20
Well, I managed to get Steam installed and updated, but now when I try to launch it with a launcher a made on the panel I get an error saying

```
Fatal Error: Could not load module 'bin/vgui2.dll'
```

So I opened terminal and moved to the Steam directory and proceeded to "wine steam.exe" and the small green box as usual pops up for about a split second and then this is what I get in the terminal after that:

```
sklasko@CL65-U:~$ cd "/home/sklasko/.wine/drive_c/Program Files/Steam"
sklasko@CL65-U:~/.wine/drive_c/Program Files/Steam$ wine steam.exe
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:dbghelp:EnumerateLoadedModules If this happens, bump the number in mod

```

After which, it sits there and then my CPU and RAM meters almost top off at 100% and doesn't make any progress. :mad: 

Thanks for any help in advance, if you need to know anything else, just ask. :)

---

### Post by pay on 2006-10-20
Try making a launcher like this ```
sudo nano /usr/bin/steam
```Then add this text ```
#!/bin/sh
# edit the next path
pushd /your/steam/directory
WINEDEBUG="fixme-all" wine Steam.exe
popd

```Ctrl+X then enter to save ```
chmod 755 /usr/bin/steam
```to make it executable then start steam ```
steam
```then you can change your launcher's command to "steam".

---

### Post by russianpirate on 2006-10-20
Does Steam (CSS) even work on latest wine?
I tried cedega 5.2.6 a few days ago and steam wouldnt work.. so I'll keep windows 2000 forever cause cedega and steam will always update and I dont want to have to wait to play CSS.

---

### Post by Sklasko on 2006-10-20
Thanks **pay** I'll try that right now, I'll report back in a little bit.

---

### Post by Sklasko on 2006-10-20
Sorry for the double post but, quick update. I followed all the steps and this is the result:

```
sklasko@CL65-U:~$ steam
~/.wine/drive_c/Program Files/Steam ~
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
wine: Call from 0x7fc2e770 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting
Shutting down. . .
300client callback thread error

```

After which WINE makes a popup error saying:

```
Steam.exe (main exception): Win32 StructuredException at
7C81B127: Attempt to read from virtual address 0 without
appropriate permissions
```

---

### Post by pay on 2006-10-20
I'm starting to agree with russianpirate, maybe 0.9.23 doesn't work with steam. I remember 0.9.22 worked with steam though...Are you on amd64 or i386?

---

### Post by Sklasko on 2006-10-21
i386. I think I might try to reinstall WINE and attempt to reinstall Steam again though.

---

### Post by pay on 2006-10-21
If you want to find out what installation you have run ```
uname -a
```32bit is i386,i486,i586,i686, 64bit would be amd64, x86_64, ia64.

---

### Post by Sklasko on 2006-10-21
Oh, well I feel stupid, I ran that command out of curiosity. It's i686.

---

