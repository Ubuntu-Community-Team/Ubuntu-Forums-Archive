---
title: "Steam Will Not Open"
date: 2014-06-19
forum: Gaming &amp; Leisure
---

### Post by acts1-8b on 2014-06-19
I downloaded the .deb from : [http://repo.steampowered.com/steam/pool/steam/s/steam/steam-launcher_1.0.0.48_all.deb](http://repo.steampowered.com/steam/pool/steam/s/steam/steam-launcher_1.0.0.48_all.deb) and installed it with [COLOR=#333333]gdebi. It now shows up on my program list. But when Iclick on it nothing happens. I tried running 'steam' in the termnal and I got: 


```


[/COLOR]Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Gen6+ requires Kernel 3.6 or later.
steam: ../../../../../src/mesa/main/context.c:1501: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-06-19 22:53:17] Startup - updater built Jun 16 2014 11:16:02
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140619225317_1.dmp
/home/poopface/.local/share/Steam/steam.sh: line 755: 23176 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/poopface/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/poopface/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/poopface/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Gen6+ requires Kernel 3.6 or later.
steam: ../../../../../src/mesa/main/context.c:1501: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-06-19 22:53:20] Startup - updater built Jun 16 2014 11:16:02
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140619225320_1.dmp
/home/poopface/.local/share/Steam/steam.sh: line 755: 23347 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-7de4f726-797f-4d26-b167-0e9432140619
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-4a49013c-27fa-4661-a82c-31bf02140619


[COLOR=#333333]

```
(yes, I sent my username as poopface, I was in a dumb mood) 


Anyone know whats up? [/COLOR]

---

### Post by acts1-8b on 2014-06-20
Never mind, Im gonna use playonlinux

EDIT: Thats not working. same issues persists, help anyway?

---

### Post by Peter_Solver on 2014-06-21
Try to delete the .steam/steam/appcache directory from the terminal. If it works, do this when you open Steam.[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]

---

### Post by thnewguy on 2014-06-21
I have the same problem. Steam updated itself yesterday and now no longer starts. I suspect the update broke something. I tried to re-download the installer from the Steam website, but got an access denied error on the installer. Seems Steam is having all sorts of problems this week.

the directory Peter_Solver mentioned in the above post does not exist on my machine.

---

### Post by Peter_Solver on 2014-06-21
^ Did you make sure that your Ubuntu is updated? You can also do this alternatively, install Steam from the software center of Ubuntu or download the Steam installer again.

---

### Post by -Marco on 2014-06-22
To me it even opens, says there are problems connecting, even though I have one of the best connections in Italy. 
On the website the download give error 403 and all download via terminal .. I think for the summer sales servers are bursting.
**In a nutshell, download it via terminal with this line code:**
```
sudo apt-get install steam
```

---

### Post by thnewguy on 2014-06-22
I removed Steam and then re-installed it from Ubuntu's Software Centre. Steam still crashes at start-up with the error shown above.

---

### Post by -Marco on 2014-06-23
> **thnewguy said:**
> I removed Steam and then re-installed it from Ubuntu's Software Centre. Steam still crashes at start-up with the error shown above.
Follow my step, it's simple no?

---

### Post by thnewguy on 2014-06-23
I did follow your steps,it is simple, but does not work. There was no change, Steam still doesn't run.

---

### Post by thnewguy on 2014-06-26
For some reason Steam started working for me today, about a week after it initially stopped. I'm assuming the latest series of updates fixed the problem. I had to sign into my Steam account and re-start Steam once, but everything appears to be functioning now.

---

