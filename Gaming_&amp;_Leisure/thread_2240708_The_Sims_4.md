---
title: "The Sims 4"
date: 2014-08-21
forum: Gaming &amp; Leisure
---

### Post by suppur5 on 2014-08-21
The sims 3 was a lovely game to play through wine, and it worked very well. The sims 4 is coming out in a few days and id rather not have to keep windows to play it. I attempted to run The Create a Sim demo but sadly it requires Microsoft visual c++ 2013. Which does not run on wine :(. So this most likely means the sims 4 full game will have the same issue. So I wanted to see if anyone would be up for maybe helping to get visual 2013 running on wine? I'm not the most experianced developer so i can't do a whole lot myself but I hope someone is up for the task :)

---

### Post by lah7 on 2014-08-23
I too would like to see The Sims 4 working in Wine. Even better if it was natively ported to Linux... but knowing EA, that won't happen in a long time. :(

As there will be a Mac version of the game, I will suspect the game will need to be compatible with Wine somehow (The Sims 3 Mac version itself is a Wine wrapper apparently)

For experimentation, I have attached a .reg file ([ATTACH]255762[/ATTACH]) containing the registry keys that the vcredist_x86.exe installer would have imported anyway (from a Windows 7 32-bit virtual machine).
This might be useful to see what DLLs/files are missing and if it's possible to 'manually' install them, but I'm no expert in this field.

**As far as Origin is concerned:** Downloading is a breeze if you patch a file first (see WineHQ [http://appdb.winehq.org/objectManager.php?sClass=version&iId=26175](http://appdb.winehq.org/objectManager.php?sClass=version&iId=26175))

I managed to 'bypass' installation by killing the installer processes prematurely a few times before it had time to return an error code, which brings a "Play" button instead of a "Install" button.
However, upon launching, Origin will return this error:
> Invalid license. Reason code = Missing DLL: [msvcp120.dll] Error: 0x7E.

From observing the registry file, these DLLs are "shared" and **might** be required:
msvcr120.dll; msvcp120.dll; vccorlib120.dll; vcamp120.dll; vcomp120.dll; mfc120.dll; mfc120u.dll; mfcm120.dll; mfcm120u.dll; mfc120cht.dll; mfc120chs.dll; mfc120enu.dll; mfc120deu.dll; mfc120esn.dll; mfc120fra.dll; mfc120ita.dll; mfc120jpn.dll; mfc120kor.dll; mfc120rus.dll

That's all I know so far. Another user has managed to get a bit further to the demo just crashing, according to these WineHQ test results: (queued at this time of writing)
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=30762&iTestingId=85789](https://appdb.winehq.org/objectManager.php?sClass=version&iId=30762&iTestingId=85789)

**Edit:** Did some more experimenting. I manually copied the DLLs (and imported the .reg file) to the Wine's system32 folder and got the "Application Error" message (caused by a page fault error) with Wine 1.7.24. Sadly, I cannot retrieve any more details about why it crashes as the dialog is stuck on "Loading detailed information, please wait..."

---

### Post by suppur5 on 2014-08-23
Well thankfully we're actually getting somewhere, if we're lucky maybe we can get this all worked out by the time the sims 4 is released :D I may end up buying windows 8 to dual boot if we can't get it wroking in linux. hopefully i don't have to do that though lol.

---

### Post by lah7 on 2014-11-07
For anyone else coming across this thread, you can in fact, run The Sims 4 (specifically version 1.0.797.20) under Wine, but with a patched version.

suppur5's thread over at the WineHQ Forums has a solution:
[https://forum.winehq.org/viewtopic.php?f=2&t=23318#p97193](https://forum.winehq.org/viewtopic.php?f=2&t=23318#p97193)

Wine Entry:
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=31195](https://appdb.winehq.org/objectManager.php?sClass=version&iId=31195)

Here's a quote of a tester's instructions: (as patched versions of wine shouldn't really be reported to WineHQ AppDB)
> [COLOR=#000000]1) Install wine-compholio (patched wine distribution to allow vcrun2013 installation)
[/COLOR]1a) Go [https://github.com/wine-compholio/wine-staging](https://github.com/wine-compholio/wine-staging)
1b) Click "download zip"
1c) Unpack
1d) Open  DEVELOPER.md in text editor
1e) Follow the instructions in 'Instructions' chapter.
1f) Update you PATH environment variable with path to installed binaries ("export PATH=/usr/local/bin:${PATH}" in my case)
If you are afraid of installing third-part wine distribution system-wide (I, personally, am), you can compile it without root permissions, and install it to custom prefix under special "compromised" user for gaming.

2) Download and install:
2a) Microsoft Visual C++ 2010 Redistributable Package ([http://www.microsoft.com/en-us/download/details.aspx?id=5555](http://www.microsoft.com/en-us/download/details.aspx?id=5555))
2b) Visual C++ Redistributable for Visual Studio 2012 Update 4 ([http://www.microsoft.com/en-us/download/details.aspx?id=30679](http://www.microsoft.com/en-us/download/details.aspx?id=30679))
2c) Visual C++ Redistributable Packages for Visual Studio 2013 ([http://www.microsoft.com/en-us/download/details.aspx?id=40784](http://www.microsoft.com/en-us/download/details.aspx?id=40784))

3) Override following DLLs to native in winecfg:
3a) atl100, atl110, atl120
3b) msvcp100, msvcp110, msvcp120
3c) msvcr100, msvcr110, msvcr120
3d) vcomp100, vcomp110, vcomp120 [COLOR=#000000]I'm not sure all these overrides are necessary, just followed the instruction above.[/COLOR]

Once Microsoft Visual C++ Redistributable 2013 installs under stock Wine, this process would no longer be necessary.

---

### Post by devdlp on 2015-01-07
Im sorry to reply to an old thread but ive installed comphilo but from there im lost i would really love to get sims 4 to work pleasse help me

---

### Post by lah7 on 2015-01-08
> **devdlp said:**
> i would really love to get sims 4 to work pleasse help me
Wine has changed since this thread started. It should be possible to install and play The Sims 4 through vanilla Wine now (at least with 1.7.33), [providing you install the latest development version of Wine]("https://www.winehq.org/download/ubuntu") for your system. These winetricks may be essential: vc2005, vc2008, vc2010, vc2012 and vc6. For me, it works "okay" at about 10~20 fps on the highest settings (with an Nvidia graphics card and the proprietary drivers)

A summary of commands for the terminal:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.7
```

---

### Post by devdlp on 2015-01-08
I was able to get all the vcruns to work besides vcrun2013. I downloaded it from the website and tried to install but it shows error 0x80070005 - access denied. I looked the error up it says i dont have the premission. so i tried sudo su in the terminal to get root access but that failed do you know another way to install vcrun2013?

---

### Post by Juha_Kimmo on 2015-01-09
I had excactly the same result in installing it. Install progress (re)creates package cache folder without any decent permissions (just d---------). I don't have access to the install log file, I'll try to attach it later on. Without the 2013 version of the VC++ redistributable SIMS install fails.

1. update:
I have Wine version 1.7.33 from WineHQ, however it seems that the Winetricks version which comes with it could be too old and does not include the vcrun2012 & vcrun2013 installs. I'll check this in the evening and report back.

---

### Post by lah7 on 2015-01-09
Juha_Kimmo is right about winetricks being outdated. (PS. Welcome to the forums!)

The latest script is hosted here: [http://winetricks.googlecode.com/svn/trunk/src/winetricks](http://winetricks.googlecode.com/svn/trunk/src/winetricks)

To update it manually from a terminal point of view:
```
wget http://winetricks.googlecode.com/svn/trunk/src/winetricks
chmod +x winetricks
**sudo** mv winetricks /usr/bin/
```

@devdlp - You should **never** run Wine as root! It only messes up the permissions in your wine prefix and isn't the equivilant as an administrator in Windows. It's quite dangerous. [http://wiki.winehq.org/FAQ#run_as_root](http://wiki.winehq.org/FAQ#run_as_root)

---

### Post by devdlp on 2015-01-09
Dude your a life savior seriously.. That allowed me to install vcrun2012, and 2013.. Now im trying to install the game ill post you back

still having trouble

I responded to the wrong post. But now the game wont even download ive tried reinstalling the game to no success. Its stuck at 0%. Any pointers or a quick fix?

---

### Post by lah7 on 2015-01-09
I'm aware there is a bug with Origin running under Wine: It causes Origin to "hang" downloads or transfer at an extremely slow speed.

@devdlp specifically, earlier in this thread you mentioned you ran Wine as root (using sudo) -- You could potentially of had broken your own user permissions mixed with root's in the process. The easiest thing here would be to erase the entire wineprefix and start again.

For the 0% bug, try following the patch provided on the WineHQ page for Origin near the bottom (with blue borders): [https://appdb.winehq.org/objectManager.php?sClass=version&iId=26175](https://appdb.winehq.org/objectManager.php?sClass=version&iId=26175)

---

### Post by devdlp on 2015-01-09
Yess! Its downloading... Very slowly buts downloading hope it works thanx again.

---

### Post by Juha_Kimmo on 2015-01-09
> **lah7 said:**
> Juha_Kimmo is right about winetricks being outdated. (PS. Welcome to the forums!)

The latest script is hosted here: [http://winetricks.googlecode.com/svn/trunk/src/winetricks](http://winetricks.googlecode.com/svn/trunk/src/winetricks)

To update it manually from a terminal point of view:
```
wget http://winetricks.googlecode.com/svn/trunk/src/winetricks
chmod +x winetricks
**sudo** mv winetricks /usr/bin/
```

@devdlp - You should **never** run Wine as root! It only messes up the permissions in your wine prefix and isn't the equivilant as an administrator in Windows. It's quite dangerous. [http://wiki.winehq.org/FAQ#run_as_root](http://wiki.winehq.org/FAQ#run_as_root)

Updated the winetricks script, the vcrun2012 installs now ok, but the vcrun2013 fails with sha1sum mismatch. Tried couple times, no success. Any idea why? And thanks lah7 ;-)

Update: I just ran sha1sum against downloaded file from MS, its' checksum differs from the file checksum in winetricks

winetricks [COLOR=#000000]18f81495bc5e6b293c69c28b0ac088a96debbab2
newly downloaded file [/COLOR]df7f0a73bfa077e483e51bfb97f5e2eceedfb6a3

Kids are now sleeping (with the pc ;-)), so I'll try tomorrow morning if this is the solution to the problem. issue 464 in [https://code.google.com/p/winetricks/issues/detail?id=464](https://code.google.com/p/winetricks/issues/detail?id=464) describes the same symptoms.

---

### Post by devdlp on 2015-01-09
Unfortunely it shows vcrun2013 does not match can not download:mad: Show:Checksum for /home/deven/.cache/winetricks/vcrun2013/vcredist_x86.exe did not match, retrying download
and, sha1sum mismatch! Rename /home/deven/.cache/winetricks/vcrun2013/vcredist_x86.exe and try again.

---

### Post by lah7 on 2015-01-09
I just realised it happens on my end too. The checksum of the downloaded file from Microsoft's servers (I get [COLOR=#000080][FONT=courier new]df7f0a73bfa077e483e51bfb97f5e2eceedfb6a3[/FONT][/COLOR] by typing[FONT=courier new]** sha1sum ~/.cache/winetricks/vcrun2013/vcredist_x86.exe**[/FONT] ) is not the same as the script (winetricks) is expecting ([COLOR=#000080][FONT=courier new]18f81495bc5e6b293c69c28b0ac088a96debbab2[/FONT][/COLOR][COLOR=#000000] on line [/COLOR][COLOR=#000080][FONT=courier new]7322[/FONT][/COLOR][COLOR=#000000]). It could be because Microsoft changed the file on their server since this was checksumed and the maintainers behind winetricks haven't been informed of this yet.[/COLOR]

[COLOR=#000000]Fear not, it's only a precaution (and a very good way to check downloads) in case the download indeed was faulty. You can just change that line in the script with the correct hash using the text editor as root, or this command will do that automagically:
[/COLOR]```
**sudo** find /usr/bin/winetricks -type f -exec sed -i 's/[COLOR=#b22222]18f81495bc5e6b293c69c28b0ac088a96debbab2[/COLOR]/[COLOR=#006400]df7f0a73bfa077e483e51bfb97f5e2eceedfb6a3[/COLOR]/g' {} \;
```
[COLOR=#808080](This command scans the file for the old checksum and replaces it with the one I got)[/COLOR][COLOR=#000000]

It'll now extract the DLLs for VC2013 when you run Winetricks again. Hopefully now you're closer to getting The Sims 4 working.

I should point out that Origin may hang at the last minute, in which case, kill EAProxyInstaller.exe (since it hangs when installing VC2013 normally)[/COLOR]

---

### Post by Juha_Kimmo on 2015-01-09
Could you try to run sha1sum from the vcredist_x86.exe you downloaded and edit the winetricks script accordingly (replace the original checksum with the new one)? + clean up the .cache. I have no access right now to the wined machine in the kids room.

---

### Post by devdlp on 2015-01-09
okay i have to redownload and install now it says i have vcrun2013 installed now in winetricks ill reply with an update btw sorry for being a noob but how do i [COLOR=#000000]kill EAProxyInstaller.exe?[/COLOR]

I dont wanna give up but now its claiming that i dont have the updated version of Origin now Origin wont open idk what to do this is blowing meee:mad::(:-#:-#:-#
I deleted the Origin file to reinstall it fresh but the sims 4 disk wont open the setup.exe file now its like i took two steps back man

---

### Post by Juha_Kimmo on 2015-01-15
> **lah7 said:**
> I just realised it happens on my end too. The checksum of the downloaded file from Microsoft's servers (I get [COLOR=#000080][FONT=courier new]df7f0a73bfa077e483e51bfb97f5e2eceedfb6a3[/FONT][/COLOR] by typing[FONT=courier new]** sha1sum ~/.cache/winetricks/vcrun2013/vcredist_x86.exe**[/FONT] ) is not the same as the script (winetricks) is expecting ([COLOR=#000080][FONT=courier new]18f81495bc5e6b293c69c28b0ac088a96debbab2[/FONT][/COLOR][COLOR=#000000] on line [/COLOR][COLOR=#000080][FONT=courier new]7322[/FONT][/COLOR][COLOR=#000000]). It could be because Microsoft changed the file on their server since this was checksumed and the maintainers behind winetricks haven't been informed of this yet.[/COLOR]

[COLOR=#000000]Fear not, it's only a precaution (and a very good way to check downloads) in case the download indeed was faulty. You can just change that line in the script with the correct hash using the text editor as root, or this command will do that automagically:
[/COLOR]```
**sudo** find /usr/bin/winetricks -type f -exec sed -i 's/[COLOR=#b22222]18f81495bc5e6b293c69c28b0ac088a96debbab2[/COLOR]/[COLOR=#006400]df7f0a73bfa077e483e51bfb97f5e2eceedfb6a3[/COLOR]/g' {} \;
```
[COLOR=#808080](This command scans the file for the old checksum and replaces it with the one I got)[/COLOR][COLOR=#000000]

It'll now extract the DLLs for VC2013 when you run Winetricks again. Hopefully now you're closer to getting The Sims 4 working.

I should point out that Origin may hang at the last minute, in which case, kill EAProxyInstaller.exe (since it hangs when installing VC2013 normally)[/COLOR]

Hmm, I edited the winetricks script and then the "winetricks vcrun2013" succeeded. However the Sims 4 install failed in the end to the same error about missing/unsuccessful installation of VC++ component. In the Wineconfig all VC redisributable versions show in the "winetricks dlls list" command. I guess I'm missing some crucial config/dll/??

Any ideas?

---

### Post by lah7 on 2015-01-15
> **Juha_Kimmo said:**
> Hmm, I edited the winetricks script and then the "winetricks vcrun2013" succeeded. However the Sims 4 install failed in the end to the same error about missing/unsuccessful installation of VC++ component. In the Wineconfig all VC redisributable versions show in the "winetricks dlls list" command. I guess I'm missing some crucial config/dll/??

Any ideas?
It's very likely that Origin is attempting to install VC 2013 normally, which is no doubt going to fail in Wine as of now. Winetricks worked around this by manually extracted the required DLLs for VC2013 programs to work.

Instead, when it starts to install, catch the vcredist_x86.exe process in Wine's Task Manager and kill it (and possibly EAProxyInstaller.exe too), eventually Origin is fooled to thinking it's installed.

---

### Post by Juha_Kimmo on 2015-01-15
Ok. I'll try that in the evening. Thanks!

---

### Post by Juha_Kimmo on 2015-01-15
> **lah7 said:**
> It's very likely that Origin is attempting to install VC 2013 normally, which is no doubt going to fail in Wine as of now. Winetricks worked around this by manually extracted the required DLLs for VC2013 programs to work.

Instead, when it starts to install, catch the vcredist_x86.exe process in Wine's Task Manager and kill it (and possibly EAProxyInstaller.exe too), eventually Origin is fooled to thinking it's installed.

Wow! Killing the vcredist_x86.exe process in the Wine task manager (command "wine taskmgr") did the job. Origin seemingly stalls to the 100% but it gives despite that an option to play. Thanks a lot! My daughter is now a very happy person :-)

---

### Post by Juha_Kimmo on 2015-01-16
This might be a bit offtopic, but next start of the game initiated Origin to download (& reinstall) Sims. And the process failed naturally to the same error since there was nobody waiting to kill vcredist_x86.exe in the end of the download&install. Do you have any better ideas than uninstall and reinstall with Origin download? I did the install from DVD set, and it seems that the Origin forces the download.

---

### Post by greg69 on 2015-01-25
Bear in mind, This IS EA we're talking about. They don't like their community.
Also, The fact that Sims 4 was a big disappointment. Sorry if I'm late.

---

### Post by Juha_Kimmo on 2015-01-27
Yep, this is totally frustrating. It seems that after the mandatory update from net installing it fails somehow. Most likely the problem is with the VC++ redistributable. The game is not playable after downloading & installing a total of 9GB update.. I wonder if anybody has succeeded to get the Sims 4 working on Wine. And just now the update download from EA doesn't even start.

I'd like to keep my home Windows-free ;-)

---

### Post by gjb1002 on 2015-02-01
Hi all,

Fairly new to this whole thing with Wine etc, but have promised my daughter to try and get Sims 4 to work. I've had all of the issues in this thread and followed all the instructions here, latest winetricks, hacked the SHA1 to make vcrun2013 work, applied "Heiko's patch" to get Origin to download the demo, killed the vcredist_x86.exe during the install (otherwise it complains about the 2013 thing). Many thanks to everyone who made it possible to get this far...

Now I can press Play on the demo, which results in a dialog saying that "TS4CAS.exe" has encountered a serious problem and needs to close. Clicking "Details" just says "please wait" and never shows anything. Googling this found some people who fixed it by rebooting, but that didn't help me.

Have others on this thread tried to run the free demo under Wine before buying the game? I'm a bit reluctant to buy the game without having established that I can run the free demo first...

Grateful for any help.

---

### Post by Juha_Kimmo on 2015-02-03
Well, finally I did manage to get Sims 4 playable. I updated Wine to 1.7.34, then the download/install with Origin did gave the vcredist_x86 error in the end. Then I killed the EAProxyInstaller.exe. After that the Origin had clean orange Play on the Sims :-)

 My daughter bought the Sims 4 DVD set, I didn't try with demo version at all. She had a great trust on me...

gjb1002, hope this helps

UPDATE: EA pushed mandatory update for Sims 4 and this time the vcredist_x86 failure (install progress is too quick for me ;-)  prevents the game from starting up. It seems that the version 1.7.34 is still the latest in the repos. I'd like to keep up with the mainstream Wine, not with the wine-staging, so I'll have to wait the update. Do you have any idea when the 1.7.35 hits the repos?

---

### Post by emre-akkaya-06 on 2015-05-26
I test it. And Succes. I explained in a simple way. [this link]("http://www.emreakkaya.org/linux-the-sims-4-yuklemek-wine-on-ubuntu/")

---

### Post by brian62 on 2015-05-26
I've actually found that it runs great on Ubuntu via Crossover using the Sims 3 bottle.

[https://www.youtube.com/watch?v=UwR-jpLUhR0](https://www.youtube.com/watch?v=UwR-jpLUhR0)

---

### Post by Hoang_Viet on 2015-05-27
> **brian62 said:**
> I've actually found that it runs great on Ubuntu via Crossover using the Sims 3 bottle.

[https://www.youtube.com/watch?v=UwR-jpLUhR0](https://www.youtube.com/watch?v=UwR-jpLUhR0)

oh, thank you very much for sharing

---

### Post by michi-skalda on 2015-06-23
Hi guys, i managed to get Sims 4 working (including the Get to Work Addon).
My problem is now, that i only get 15-20 FPS, doesnt matter if i play on low or ultra settings... It's playable but on Windows i get >100 fps. (I have a GTX560Ti)
I tried disabling GLSL, but that brought about 2-3 fps. I used latest NVIDIA 253 driver.

Pls tell me if this is normal or is there a fix? :)

---

