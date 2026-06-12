---
title: "Cedega 5.1 on Dapper"
date: 2006-02-17
forum: Gaming &amp; Leisure
---

### Post by alvinblank on 2006-02-17
I'm getting this error with Cedega 5.1 small and 5.1 engine when starting ANY windows program.
/home/mwe/.cedega/.winex_ver/winex-5.1/bin/winex3: line 374: 8037 Killed $SHELL -c "$RUNWINE $FULL_COMMAND_LINE"

When I attempt to run /home/mwe/.cedega/.winex_ver/winex-5.1/bin/winex3, the following is produced. It appears several files are missing completely from the install package:

mwe@4400p:~$ /home/mwe/.cedega/.winex_ver/winex-5.1/bin/winex3
/home/mwe/.cedega/.winex_ver/winex-5.1/bin/winex3: line 143: /usr/lib/transgaming_cedega//winex/bin/pthreads_stack_test: No such file or directory
/home/mwe/.cedega/.winex_ver/winex-5.1/bin/winex3: line 144: [: -gt: unary operator expected
Updating TransGaming config and registry info
WARNING: Your old config file has been moved to config.old. Any modifications you made to this file
will have to be replaced.
mv: cannot stat `/home/mwe/.transgaming/config': No such file or directory
/home/mwe/.cedega/.winex_ver/winex-5.1/bin/winex3: line 272: /usr/lib/transgaming_cedega//.transgaming/config: No such file or directory
cp: cannot stat `/usr/lib/transgaming_cedega//.transgaming/dyndata.reg': No such file or directory
/home/mwe/.cedega/.winex_ver/winex-5.1/bin/winex3: line 278: /usr/lib/transgaming_cedega//update.reg: No such file or directory
cp: target `/home/mwe/.transgaming/c_drive/windows/' is not a directory: No such file or directory
ln: creating symbolic link `/home/mwe/.transgaming/c_drive/windows/system32/regsvr32' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32': No such file or directory
ln: creating symbolic link `/home/mwe/.transgaming/c_drive/windows/system32/regsvr32.so' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32.so': No such file or directory
ln: creating symbolic link `/home/mwe/.transgaming/c_drive/windows/system32/regsvr32.exe' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32': No such file or directory
ln: creating symbolic link `/home/mwe/.transgaming/c_drive/windows/system32/regsvr32.exe.so' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32.so': No such file or directory
ln: creating symbolic link `/home/mwe/.transgaming/c_drive/windows/system32/wcmd.exe' to `/usr/lib/transgaming_cedega//winex/bin/wcmd': No such file or directory
ln: creating symbolic link `/home/mwe/.transgaming/c_drive/windows/system32/wcmd.exe.so' to `/usr/lib/transgaming_cedega//winex/bin/wcmd.so': No such file or directory
ln: creating symbolic link `/home/mwe/.transgaming/c_drive/windows/system32/winebrowserlink' to `/usr/lib/transgaming_cedega//winex/bin/winebrowserlink': No such file or directory
ln: creating symbolic link `/home/mwe/.transgaming/c_drive/windows/system32/winebrowserlink.so' to `/usr/lib/transgaming_cedega//winex/bin/winebrowserlink.so': No such file or directory
cp: cannot stat `/usr/lib/transgaming_cedega//.transgaming/tg_config_version': No such file or directory
cat: /home/mwe/.transgaming_global/Fonts/tg_font_version: No such file or directory
/home/mwe/.cedega/.winex_ver/winex-5.1/bin/winex3: line 176: [: -lt: unary operator expected
Update complete
Registering Mozilla Control
/home/mwe/.transgaming_global/mozcontrol/update_mozctl: line 51: /home/mwe/.transgaming/c_drive/windows/system32/regsvr32: No such file or directory
usage: cedega [-use-pthreads <yes/no>] [[-]-winver <version>] [[-]-debugmsg <debug>] [[-]-version] [[-]-use-dos-cwd <dir>] [[-]monitor-cdrom-eject] <application> [application parameters]

---

### Post by alvinblank on 2006-02-18
From [http://transgaming.org/forum/viewtopic.php?t=5413](http://transgaming.org/forum/viewtopic.php?t=5413)

It seems to be a dapper issue?

---

### Post by QuickFire on 2006-02-18
Same error here unfortunatly :S
I'll try with 5.0 to see if it works

---

### Post by alvinblank on 2006-02-18
For me 5.0 still gives the same error. Not sure why, something in dapper messing up?

---

### Post by claes on 2006-02-19
For me the problem only apears when I use the 2.6.15-15 kernel if I use 2.6.15-14 there are no problem. Wine and crossover office dies the same way as cedega too.

There are som problems with high memory (I've heard not understood).

Claes

---

### Post by Sanderfox on 2006-02-19
I hope they find a fix for this, 'cause this is quite irritating...

---

### Post by jnthornh on 2006-02-19
Downgrading the kernel worked for me, however things are still not working perfectly.  Cedega seems to have an issue with my cd-rom drive - while it functions properly during install, games that need to access a disc when they run just fail without even spinning the drive up.  Has anybody seen this before?

---

### Post by claes on 2006-02-20
[QUOTE=Sanderfox]I hope they find a fix for this, 'cause this is quite irritating...[/QUOTE]

I've heard elsewhere that ubuntu wine people and ubuntu kernel people have been notified and that they are trying to fix the problem together. So hopefully we will see this problem solved before dapper goes stable.

Claes

---

### Post by Sanderfox on 2006-02-21
Any update yet ? :)

---

### Post by Sanderfox on 2006-02-22
The kernel update seems to have solved this one problem, but I get another error now:
```
warning: mmap failed on reservation of 80000000 (01000000)
warning: mmap failed on reservation of 90000000 (00a00000)
warning: mmap failed on reservation of 90000000
can't map memory? (server): Cannot allocate memory
wine: Unhandled exception, starting debugger...
```

so...

---

### Post by Sanderfox on 2006-02-27
*ping*

---

### Post by GQed76 on 2006-03-02
Is this still broken?

---

### Post by Sanderfox on 2006-03-03
Here I get memory allocation errors and the error that the .exe isn't valid. I'm using Wine now for the thing I wanted to use with cedega, but it still doesn't work as it should.

---

### Post by Mon on 2006-03-04
Anything else than the -14 kernel (-k7 to be exact) doesn't work for me. Today however i somehow broke my sound. Only thing i was toying with is XGL that shouldn't be responsible, i think...
Anyway what kernel do you guys use? Does the recent -17 kernel work for you?
I think i'll try to compile my own kernel and see how that works.

---

