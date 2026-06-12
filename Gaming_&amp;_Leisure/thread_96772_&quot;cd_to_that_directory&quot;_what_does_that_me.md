---
title: "&quot;cd to that directory&quot; what does that mean? (Mozcontrol install)"
date: 2005-11-29
forum: Gaming &amp; Leisure
---

### Post by s monty on 2005-11-29
I have tried various things, I have tried going to ~/.wine/drive_c/Program files/mozcontrol than double clicking the .dll but i just get a can't be displayed error, and also the regsvr32.dll isn't there(or w/e its called).

---

### Post by sethmahoney on 2005-11-29
[QUOTE=s monty]I have tried various things, I have tried going to ~/.wine/drive_c/Program files/mozcontrol than double clicking the .dll but i just get a can't be displayed error, and also the regsvr32.dll isn't there(or w/e its called).[/QUOTE]

I'm not sure if this answers your question, but "cd to that directory" means that you should open up a terminal and type cd followed by a space followed by the name of the directory you are changing to.

---

### Post by markmark on 2005-11-29
Assuming you're trying to get mozcontrol going to run steam:

I'm also guessing you have managed to download the mozcontrol.tgz file and have extracted it in to ~/.wine/drive_c/Program files/mozcontrol using fileroller or something.

Now open up a command line and type:
```
cd ~/.wine/drive_c/Program\ files/mozcontrol
```
That will change you into that directory. If you do a directory list it should look something like this:
```
mark:mozcontrol$ ls
chrome      js3250.dll        mozz.dll     plds4.dll     softokn3.dll
components  LICENSE           msvcp60.dll  plugins       ssl3.dll
defaults    mozcontrol.tgz    nspr4.dll    res           update_mozctl
gkgfx.dll   mozctl.dll        nss3.dll     revision      xpcom_compat.dll
greprefs    mozctlx.dll       nssckbi.dll  smime3.dll    xpcom_core.dll
ipc         mozilla-ipcd.exe  plc4.dll     softokn3.chk  xpcom.dll

```
Now you need to type:
```
wine regsvr32 mozctlx.dll
```
And that causes wine to register the mozctlx dll.

---

