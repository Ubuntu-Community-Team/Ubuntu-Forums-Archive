---
title: "Wine not working"
date: 2006-07-05
forum: Desktop Environments
---

### Post by strigare on 2006-07-05
When trying to install Warcraft 3 it throws me this error.
```
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\strigare\\Desktop"'.
err:shell:SHGetFileInfoW pidl is null!
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ strigare\\Desktop"'.

strigare@strigare-desktop:/media/cdrecorder$ wineserver: could not save registry  branch to /home/strigare/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/strigare/.wine/userdef.reg :  Permission denied
wineserver: could not save registry branch to /home/strigare/.wine/user.reg : Pe rmission denied



```

When I do winecfg and try to save it throws me this one
```
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
strigare@strigare-desktop:/media/cdrecorder$ wineserver: could not save registry branch to /home/strigare/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/strigare/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/strigare/.wine/user.reg : Permission denied

```

Could anyone help me?

---

### Post by quedigg on 2006-07-05
Hello ,
 1st : run wine as a root,open the terminal and type ```
sudo wine blablah.exe
```
 you will get prompt for the root password
 2nd: wine provide a virual drive,i think z:/, this drive resides linux directory structure,chose a directory ,then GO!!

regards,
quedigg

---

### Post by topgi on 2006-07-05
DON"T RUN WINE AS ROOT !!!!

The instruction on how to set-up worldcraft are in the ApplicationDB of WINE website. [www.winehq.org](www.winehq.org)

DON'T RUN WINE AS ROOT.

---

### Post by strigare on 2006-07-05
[QUOTE=topgi]DON"T RUN WINE AS ROOT !!!!

The instruction on how to set-up worldcraft are in the ApplicationDB of WINE website. [www.winehq.org](www.winehq.org)

DON'T RUN WINE AS ROOT.[/QUOTE]

Why shouldn't I do it?

I used the how-to in [www.winehq.org](www.winehq.org) but it didn't work, I've tried almost everything and it hasn't worked.

---

### Post by quedigg on 2006-07-05
yep, i think that's better ,here[http://appdb.winehq.org/appview.php?versionId=1177]("http://appdb.winehq.org/appview.php?versionId=1177")

---

### Post by topgi on 2006-07-06
There has been many regression on Wine. Maybe it will work if you install an older version of WINE, like 0.9.5. You can find it in the Wine web.

---

