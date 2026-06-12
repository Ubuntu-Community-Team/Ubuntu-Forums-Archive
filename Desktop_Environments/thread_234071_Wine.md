---
title: "Wine"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Harr!s on 2006-08-10
Having just installed Wine, and trying to configure it using: 

```
winecfg
```

I get the following error message: 

```
root@ubuntu:~# winecfg
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:import_dll Library comdlg32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Loading library shell32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000135 
```

I was wondering if anyone could help me out with this?

---

### Post by billyfoxtrot on 2006-08-10
How did you go about installing it?

---

### Post by Harr!s on 2006-08-10
> **billyfoxtrot said:**
> How did you go about installing it?

The first thing I did was add the wine repostory via Synpatic Pack Manager so that I could get the most recent updated version.

```
 System-> Administration -> Synpatic Package Manager -> Settings -> Repositories -> Add -> Custom 

deb http://wine.sourceforge.net/apt binary/
```

Then I updated:

```
sudo apt-get update 
```

Then I installed 

```
sudo apt-get install wine 
```

---

### Post by James_M on 2006-08-10
I would have just left it alone.  I installed wine on this box I'm on right now and no "sudo apt-getting" for me.  WINE works just fine and all I used was synaptic.  haven't got a clue what's wrong, but I think you broke it with apt-get install.

---

### Post by billyfoxtrot on 2006-08-12
I installed it through Automatix, and that worked just fine for me.  I would try uninstalling it and then reinstalling it using a different method.

---

### Post by jason.b.c on 2006-08-12
I get this error message..

> jason@Hp-Vectra-VL:~$ wine cfg
wine: could not load L"c:\\windows\\system32\\cfg.exe": Module not found
jason@Hp-Vectra-VL:~$



Does it mean anything..???


And where do i locate the stuff that i've installed for use with wine..???   Where's wine installed in ubuntu...???  I can't find it...!

---

### Post by metalzelot on 2006-08-12
If you're searching for the wine libs you can find them at:
/usr/local/lib/wine

the commands are placed at /usr/local/bin

The windows directory is on your homefolder. There you can find all the registry data, the emulated Windows File System and so also the installed Programs

~/.wine

---

### Post by amila_aina on 2006-08-12
I installed wine from the Ubuntu DVD package wine_0.9.9-0ubuntu2_i386.deb.But when im trying to run it, it gives following error message.
"cannot open display
Failed to initialize the window"

any help to solve this ...............

---

### Post by orb9220 on 2006-08-12
"ason@Hp-Vectra-VL:~$ wine cfg
wine: could not load L"c:\\windows\\system32\\cfg.exe": Module not found
jason@Hp-Vectra-VL:~$

you run the config with :
winecfg
or hit alt-F2 and enter:
winecfg

---

### Post by frio on 2006-08-12
I just installed wine so I could run Real Player and login to my NFL FieldPass account (a whole 'nother issue). However, whenever I try to do anything with wine, including ```
wine --help
``` all I get is:
```
wine: creating configuration directory '/home/john/.wine'...
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
*** glibc detected *** free(): invalid next size (fast): 0x7c02b448 ***
wine: Unhandled exception (thread 0009), starting debugger...
``` 
Any ideas?:-k  I have never used wine so I have no idea how to configure it.

Thanks in advance...
Frio

---

### Post by RajivNair on 2006-08-12
whenever ur trying to run winecfg try to do that as a root user,i too faced the same problem untill i did "sudo winecfg",i hope it works for u.

---

### Post by frio on 2006-08-12
[RajivNair]("http://www.ubuntuforums.org/member.php?u=72223"), I should have included some more details in my first post. I have tried that and I get the same result. Also, for what it's worth, i installed Wine from Synaptic Package Manager.

---

### Post by scotty2hott2k on 2006-08-12
you are using the wrong repo.

For Ubuntu Dapper (6.06):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

is the repo for ubuntu users to use (its the official wine ubuntu repo, as soon as a news version is released its in there within minutes/hours)

---

### Post by frio on 2006-08-12
Will this one work for Breezy 5.10, which is what i am still using?

---

### Post by frio on 2006-08-12
Looks like I just have use:
```
deb http://wine.budgetdedicated.com/apt breezy main
```for my version.
Going to follow this...
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

I'll post the results after the game :wink:

---

### Post by jason.b.c on 2006-08-12
> **metalzelot said:**
> If you're searching for the wine libs you can find them at:
/usr/local/lib/wine

the commands are placed at /usr/local/bin

The windows directory is on your homefolder. There you can find all the registry data, the emulated Windows File System and so also the installed Programs

~/.wine

So is that where my windows stuff get's installed to...???   The **.exe's**....

---

### Post by jason.b.c on 2006-08-12
*bump*

---

### Post by frio on 2006-08-14
Well... when I run the install for RealPlayer, everything seems to go OK until RealPlayer attemps to actually start. The splash screen for RealPlayer opens and that's it. It hangs...
 
Still looking for an answer, I'll post if I find one. Any help or ideas sure would be appreciated.

---

### Post by allwitchesdance on 2006-08-14
I have tried using just about every version of wine out there, and every time i get a message:
```
thing@thing:~$ wine
wine: creating configuration directory '/home/elephant/.wine'...
wine: Unhandled page fault on read access to 0x7eac2000 at address 0xb7fecacd (thread 0009), starting debugger...
err:seh:EXC_DefaultHandling Unhandled exception code c0000005 flags 0 addr 0xb7fecacd
wine: wineprefixcreate failed while creating '/home/elephant/.wine'.
thing@thing:~$ wineserver: could not save registry branch to /home/elephant/.wine-shC8z1/system.reg : No such file or directory
wineserver: could not save registry branch to /home/elephant/.wine-shC8z1/user.reg : No such file or directory

```

how do i fix this?

---

