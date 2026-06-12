---
title: "cant get wine to work right!"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Digitallysick on 2005-10-15
adam@ubuntu:/media/windows/Program Files/Winamp$ wine winamp.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system" is not accessible.
Warning: could not find DOS drive for current working directory '/media/windows/Program Files/Winamp', starting in the Windows directory.
wine: cannot open (null)
adam@ubuntu:/media/windows/Program Files/Winamp$

---

### Post by aysiu on 2005-10-15
Have you tried using it graphically instead of via the command line? Navigate via Konqueror to the folder where winamp.exe is and then just click on it. Wine should try to launch it.

Also, have you thought of just using XMMS? It's very much like Winamp, and it's native to Linux.

---

### Post by MetalMusicAddict on 2005-10-15
This is the same problem Im having [HERE]("http://www.ubuntuforums.org/showthread.php?t=76537"). Its a problem with defining the drives.

---

### Post by xbaez on 2005-10-15
Hey you should Google for "Frank's corner"
There is a link to "Sidenet", a shell script that will install you Internet Explorer, Windows Media Player and such, better than winetools

So install sidenet, and you'll have Internet Explorer working in no time

Then, you can install lot of software

---

### Post by Digitallysick on 2005-10-17
for some reason when i installed wine through adept it didnt work right, i did a apt-get install wine and that took care of it

---

### Post by cowlip on 2005-10-17
The last compatible version of wine with winetools is here [http://ubuntuforums.org/showthread.php?t=4657&page=2&highlight=wine](http://ubuntuforums.org/showthread.php?t=4657&page=2&highlight=wine) so I don't know if that helps..

---

### Post by meastp on 2005-10-18
Try to delete your ~/.wine folder, and run wine.

---

### Post by manicka on 2005-10-18
[QUOTE=MetalMusicAddict]This is the same problem Im having [HERE]("http://www.ubuntuforums.org/showthread.php?t=76537"). Its a problem with defining the drives.[/QUOTE]

alt-f2 winecfg 

and get it to autodetect the drives in the Drives tab

---

