---
title: "Noob Question"
date: 2007-07-01
forum: Gaming &amp; Leisure
---

### Post by toasty_ghosty on 2007-07-01
I have Steam Installed. I want to run it with Wine. How do I start it.

I thought I typed in this:

6. When the installer finishes open up a terminal and do the following to launch steam:

cd /home/USER/.wine/drive_c/Program Files/Steam
WINEDEBUG="fixme-all" wine steam.exe

But When I type just the first line in, I get nothing. This is what I actually type in:

theking@OptimusPrimeTheSecond:~$ cd /home/theking/.wine/drive_c/Program Files/Steam/

Any help.

---

### Post by toasty_ghosty on 2007-07-01
Any ideas? I've looked around the forum and in other places and I cant seem to find anywhere that actually tells me how to launch it. I have steam installed and everything, I just need to know how to launch it using wine. I cant seem to get it to work.

---

### Post by yuvlevental on 2007-07-01
you only changed the directory. run the next line

---

### Post by dfreer on 2007-07-01
Also, in terminal you have to escape whitespaces.
so this command:
```
cd /home/theking/.wine/drive_c/Program Files/Steam/
```
should look like this:
```
cd /home/theking/.wine/drive_c/Program**\** Files/Steam/
```
It should change your prompt to look something like this if done correctly:
```
theking@OptimusPrimeTheSecond:/home/theking/.wine/drive_c/Program Files/Steam/$
```

EDIT: Also, you should be able to launch steam by:
Applications > Wine > Steam > Steam

Double-clicking the Steam shortcut on your desktop

typing:
```
wine ~/.wine/drive_c/Program\ Files/Steam/steam.exe
```

---

### Post by Sammi on 2007-07-01
> **dfreer said:**
> Also, in terminal you have to escape whitespaces.
so this command:
```
cd /home/theking/.wine/drive_c/Program Files/Steam/
```should look like this:
```
cd /home/theking/.wine/drive_c/Program**\** Files/Steam/
```
That could also be done like this: 
```
cd "/home/theking/.wine/drive_c/Program Files/Steam/"
```

---

### Post by toasty_ghosty on 2007-07-01
Alright. I had Steam running and everything but then I needed to shut my pc down and I did. But when I went to start Steam again today I get this in console:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

and Steam pops up saying:

Steam.exe (main exception): Cannot open blob archive file: CMultiFieldBlob(mem-mapped file): Failed to open exisitingfile, Win32 Error 5 "Access denied"


Any help?

---

### Post by toasty_ghosty on 2007-07-04
Thanks everyone! As of right now I am doing fine. Now lets get CS:Source up...

---

### Post by toasty_ghosty on 2007-07-04
One last question...what does this mean:

fixme:advapi:GetFileSecurityW (L"C:\\windows\\temp\\GLF698.tmp") : returns fake SECURITY_DESCRIPTOR

?

---

### Post by dfreer on 2007-07-04
> **toasty_ghosty said:**
> One last question...what does this mean:

fixme:advapi:GetFileSecurityW (L"C:\\windows\\temp\\GLF698.tmp") : returns fake SECURITY_DESCRIPTOR

?

If it doesn't affect gameplay, probably just some wine debugging output. If it is slowing down the game, you could run wine with the debugging off, lemme find the command really quick.
```
WINEDEBUG="-all" wine **Steam.exe**
```
Edit appropriately so that Steam.exe points to where steam is installed.

---

