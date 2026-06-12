---
title: "Steam wont open"
date: 2014-02-02
forum: Gaming &amp; Leisure
---

### Post by cubegames123 on 2014-02-02
Hi I have Steam and when i updated Ubuntu 13.10 and now when I open Steam nothing happens, I cat find anything on Google either, this is what i got when i did typed "steam" in terminal 

```
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
steam: ../../../../src/loader/loader.c:114: asserted_dlsym: Assertion `result' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-02-02 18:49:47] Startup - updater built Nov 25 2013 18:07:05
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140202184947_1.dmp
/home/kyle/.local/share/Steam/steam.sh: line 755: 24987 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat ‘/home/kyle/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/kyle/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-23f59cca-4a62-405b-b449-6e0162140202
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/kyle/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
steam: ../../../../src/loader/loader.c:114: asserted_dlsym: Assertion `result' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-02-02 18:49:48] Startup - updater built Nov 25 2013 18:07:05
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140202184948_1.dmp
/home/kyle/.local/share/Steam/steam.sh: line 755: 25116 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-644a3dd2-1ea3-4ac3-892c-ae2bc2140202
```


I hope you can help me, Thanks

---

### Post by Kirboosy on 2014-02-03
Welcome to the forums!

Lets try clearing out your cache.

```
rm -Rf ~/.steam/steam/appcache
```

Hope that helps!
~Caboose

PS. Please use the CODE tags when marking your code. They can be found by clicking the **#** in the editor.

---

### Post by cubegames123 on 2014-02-03
nope i  uninstalled steam and wiped the folders when i installed it again this is what i got when  i pressed the start steam button

```
You are missing the following 32-bit libraries, and Steam may not run: libc.so.6
```[SIZE=1][FONT=arial][COLOR=#FFFFFF]

[/COLOR][/FONT][/SIZE]

---

### Post by BoogeyOfTheMan on 2014-02-03
Have you tried installing those libraries? I recall having a similar issue when I first installed steam. In fact I think it was that exact library. A little google-fu helped me find the answers.

Sorry I cant seem to find the lniks right now, I've been dealing with my own steam issues and have hit up so many different threads that I cannot recall which ones helped me with the issue you are having.

---

### Post by cubegames123 on 2014-02-03
well if u can find a link terminal cmd can u give me it also this happened when i updated ubuntu

---

### Post by BoogeyOfTheMan on 2014-02-03
I cant for the life of me find that thread anymore, its been a few months since I had to use it. But in looking, I'm recalling that I had to install ia32-libs, and when I couldn't find those, I believe I installed whatever package it said replaced ia32-libs. Sorry I cant be of more help, my google-fu is very weak today.

---

### Post by Kirboosy on 2014-02-04
I'm not entirely sure which one will fix your problem but people are reporting the following commands seem to fix their issue.
```
sudo dpkg --add-architecture i386
```
```
sudo apt-get install libc6 ia32-libs 
```

Sources
[You are missing the following libraries...]("http://steamcommunity.com/app/221410/discussions/0/864960354155782104/#c864960354200592520")
[Missing the following libraries Ask Ubuntu]("http://askubuntu.com/questions/387628/you-are-missing-the-following-32-bit-libraries-and-steam-may-not-run-libc-so")

~Caboose

---

### Post by Willyweasel on 2014-02-04
ia32-libs is no longer available in 13.10, try this instead.

```
sudo apt-get install libc6 libc6:i386
```

---

### Post by cubegames123 on 2014-02-04
nope didnt work :(

---

### Post by Kirboosy on 2014-02-05
Did it install packages or did it not find anything? Did the error change at all?

---

### Post by cubegames123 on 2014-02-05
same errror

---

### Post by Kirboosy on 2014-02-06
Have you looked at the contents of the following file?

```
gksudo gedit /etc/ld.so.conf.d/steam.conf
```

Are there any lines that contain the following?
```
/usr/lib32 
/usr/lib/i386-linux-gnu/mesa 
```
~Caboose

---

### Post by cubegames123 on 2014-02-09
everything is the same

---

### Post by dannyboy79 on 2014-02-09
> **Caboose885 said:**
> I'm not entirely sure which one will fix your problem but people are reporting the following commands seem to fix their issue.
```
sudo dpkg --add-architecture i386
```
```
sudo apt-get install libc6 ia32-libs 
```

Sources
[You are missing the following libraries...]("http://steamcommunity.com/app/221410/discussions/0/864960354155782104/#c864960354200592520")
[Missing the following libraries Ask Ubuntu]("http://askubuntu.com/questions/387628/you-are-missing-the-following-32-bit-libraries-and-steam-may-not-run-libc-so")

~Caboose
ia32-libs isn't in 13.10 and tells you to install 
```
lib32z1 lib32ncurses5 lib32bz2-1.0
```

---

### Post by ppjdee on 2014-02-10
i was able to install the 32bit libs and get steam running with the amd beta driver but i was getting the indirect rendering issue. steam runs fine with the default ubuntu drivers but using the amd drivers is a pain.
guess ill have to wait until they release a newer driver version.

edit: yay now i cant launch steam...
```

Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Couldn't dlopen libudev.so.1 or libudev.so.0, driver detection may be broken.
steam: ../../../../src/loader/loader.c:129: asserted_dlsym: Assertion `result' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-02-11 01:15:56] Startup - updater built Nov 25 2013 18:07:05
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140211011556_1.dmp
/home/jordan/.local/share/Steam/steam.sh: line 755:  5985 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat &#8216;/home/jordan/.steam/registry.vdf&#8217;: No such file or directory
Installing bootstrap /home/jordan/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/jordan/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Couldn't dlopen libudev.so.1 or libudev.so.0, driver detection may be broken.
steam: ../../../../src/loader/loader.c:129: asserted_dlsym: Assertion `result' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2014-02-11 01:15:57] Startup - updater built Nov 25 2013 18:07:05
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140211011557_1.dmp
/home/jordan/.local/share/Steam/steam.sh: line 755:  6104 Aborted                 (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-22417d24-ce6e-47b4-a957-ea3252140210
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-9993e8b5-32d0-48fd-929d-2f6be2140210
```

--edit: I chose 3.11.15 generic recovery mode then booted into the os with default graphics driver. I was able to install steam that way and it seems to work, even when I boot normally into ubuntu. :/ 
Though Im still getting an error message about libc.so.6 missing. Im guessing its graphics driver related? Maybe someone who is better at this can figure it out lol.

---

### Post by dannyboy79 on 2014-02-11
basically thefglrx driver install didn't create the proper 32bit library symlinks for you. in order for steam to work with the fglrx driver the 32bit libraries need to be symlinked correctly. how did you install the fglrx driver OR didn't you?

if you're using the default radeon driver within ubuntu and steam still isn't starting, please post back the terminal output again from trying to run steam from a terminal. Also, if you're installing and uninstalling various graphics issues than you may be creating the problem as the fglrx driver installer does a poor job of cleaning up after itself.

---

### Post by ppjdee on 2014-02-11
I installed fglrx beta drivers via this [wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide"). Right off Steam wouldnt install, but with the default drivers it worked beautifully. The output from my previous post is with [updated radeon drivers]("http://www.phoronix.com/scan.php?page=news_item&px=MTQyNDE") and [Oibaf's updated driver PPA.]("https://launchpad.net/~oibaf/+archive/graphics-drivers/")

Im planning on reinstalling fglrx beta drivers again, ill post a output later. Oh and after each graphics driver swap i reinstalled the os so shouldnt be anything left to make it wonky.

---

