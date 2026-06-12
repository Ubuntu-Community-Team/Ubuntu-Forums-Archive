---
title: "virus in Linux"
date: 2006-03-14
forum: Desktop Environments
---

### Post by txm0523 on 2006-03-14
I have installed Aegis Virus scan from the Ubuntu Synaptic Manager and then updated the definitions. I then scanned my laptop. Aegis says that this file //usr/lib/win32/vp31vfw.dll is infected with W32/Magistr.a@mm virus. When I clicked on that file to delete it, my assumption was that it was removed. When I scanned again, it flashed that the particular file in question is still infected.

I then downloaded BDC ( BitDefender for Linux ) and ran it from the konsole. It says I have no virus. I also downloaded and ran F-Prot virus scan for Linux and ran that from the konsole and it too says I don't have a virus. But, Aegis says I do. Since my laptop duals boots ( Win XP and Kubuntu 5.1 ) I then ran a virus scan and spyware scan in Windows and it too says there is no virus.

Can anyone explain to me why this is happening and what I can do about it ?  Is it just a fluke with Aegis Virus Scan ?  Do I really have that virus in Linux ?  Any help would be greatly appreciated.

Thanks

---

### Post by Zelut on 2006-03-14
I had that same issue.  My findings were that Aegis was too sensitive, so I moved to a different scanner.  Different scanners can find false-positives depending on the values they have set.

I'm sure you're fine (everyone I talked to found the same file when using Aegis, and I'm sure its wrong).  Nothing else has found anything for me either.

I'd stick with one of the others that you're comfortable with.

---

### Post by KingBahamut on 2006-03-14
Well right off Id be not really worried about Magistr.a on a linux machine. Almost purely a windows virus. 

However, if really concenred about the use of Aegis, try ClamAV, its a lot less touchy about files and so forth. I pretty much use aegis for a scan of file shares that windows machines access as their shared folders. Because as we all know, you cannot be TOO TOUCHY about virus detection. 
=)

---

### Post by curuxz on 2006-03-14
If its scanning a windows drive, it may be that you dont have write access for your user to that partition. Hence it trying to change/delete it but failing. Check to see if you can delete things manualy without having to use sudo.

---

