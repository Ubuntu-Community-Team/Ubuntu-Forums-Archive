---
title: "Wine can't fine .dll files -- case sensitivity problem?"
date: 2006-01-29
forum: Desktop Environments
---

### Post by UphillSkier on 2006-01-29
Hi, 

I am trying to get wine to run quicken for windows from my win98 partition. 
When I cd to /media/Program Files/quickenw  and do
```
wine qw.exe 
```

I get a whole pile of error messages like 

```
\\Program Files\\quickenw\\QDAPP.dll") not found
err:module:import_dll Library QDAPP.dll (which is needed by L"Z:\\media\\hda1\\Program Files\\quickenw\\QDAPPUI.dll") not found
err:module:import_dll Library QDAPPUI.dll (which is needed by L"Z:\\media\\hda1\\Program Files\\quickenw\\qw.exe") not found
err:module:import_dll Library Q_encutl.dll (which is needed by L"Z:\\media\\hda1\\Program Files\\quickenw\\qw.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\hda1\\Program Files\\quickenw\\qw.exe" failed, status c0000135

```

Note the upper case filename and lower case extension.  Now these files generally exist in the quickenw directory

```
andy@grumpy:/media/hda1/Program Files/quickenw$ ls -lF qd*
-rwxr-xr-x  1 root root  36864 2002-01-10 11:35 qdapp.dll*
-rwxr-xr-x  1 root root  24576 2002-01-10 11:35 qdappui.dll*
-rwxr-xr-x  1 root root 180224 2002-01-10 11:35 qdbbase.dll*
-rwxr-xr-x  1 root root 491520 2002-01-10 11:35 qdb.dll*

```

but wine can't find them.  I wonder if the file system is being case sensitive when it should not be.   Here is what mount tells me.

```
andy@grumpy:/media/hda1/Program Files/quickenw$ mount
<snip>
/dev/hda1 on /media/hda1 type vfat (rw)

```

I mounted /dev/hda1 with
```

root@grumpy:~# mount -t vfat -o user,rw,exec,nosuid,nodev,fmask=0000,dmask=0000 /dev/hda1 /media/hda1

```

and got the same problems as when I mounted it with
```
root@grumpy:~# mount /dev/hda1 /media/hda1 

```

It seems to me that there is a screw-up with case sensitivity but I don't know how to fix it. Can anyone help me figure out what is going on?

BTW I am running wine 0.9.6 from deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/

Thanks very much
Andy

---

### Post by UphillSkier on 2006-01-29
I found the solution!  I needed to map the windows C:\ drive onto the root of my windows partition using winecfg.  I just did

```
winecfg
```

and selected the "Drives"  tab.  I discovered that C:\ was mapped onto my root partition( /).  I clicked on "C:\"  and then entered /media/hda1 into the path box and clicked "apply".  Then I launched quicken from a terminal with no problem.  

```
cd /media/hda1/Program Files/quickenw
wine qw.exe
```

Quicken appears to work.  I am impressed.:-D

---

### Post by dcstar on 2006-01-29
[QUOTE=UphillSkier]
.......
Quicken appears to work.  I am impressed.:-D[/QUOTE]
You may find the sound in Quicken doesn't, I had to do a wine Quicken setup install to my default wine "C:" drive, and then run Quicken from that location (using the data file on my other drive).

Sound and Internet both worked, only printing crashes my Quicken.......

---

### Post by UphillSkier on 2006-01-30
[QUOTE=dcstar]You may find the sound in Quicken doesn't, I had to do a wine Quicken setup install to my default wine "C:" drive, and then run Quicken from that location (using the data file on my other drive).

Sound and Internet both worked, only printing crashes my Quicken.......[/QUOTE]

Thanks, David

I will check it out.

---

