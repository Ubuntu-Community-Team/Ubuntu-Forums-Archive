---
title: "Having problems with Doomsday"
date: 2006-11-05
forum: Gaming &amp; Leisure
---

### Post by Mooseus on 2006-11-05
Hello everyone,

I'm quite new to Linux and I'm having a few problems installing Hearts
of Iron: Doomsday. I'm using Ubuntu 6.10 and I downloaded and installed
wine (version 0.9.22) from the "add/remove" application. I followed the
instructions on how to install doomsday from the Wine Application DB:

[http://appdb.winehq.org/appview.php?iVersionId=5058](http://appdb.winehq.org/appview.php?iVersionId=5058)

The first time I tried to install it, I only did the part where you
open winecfg and set the winver to Windows 98. I then launched the
setup.exe. I managed to install at an average speed up until 23%. From
there it took half an hour to get to 24% and I had waited nearly 40
minutes on 24% but never saw it get past that, since I closed the
install myself. The installation doesn't freeze, it just installs all
the components very slowly.

Next time I tried to install it I followed the instruction to type the
command:
"WINEDLLOVERRIDES="ole32,oleaut32,rpcrt4=n" wine Setup.exe"

and I received this message:

err:module:import_dll Library ole32.dll (which is needed by
L"D:\\Doomsday\\Setup.exe") not found
err:module:import_dll Library OLEAUT32.dll (which is needed by
L"D:\\Doomsday\\Setup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for
L"D:\\Doomsday\\Setup.exe" failed, status c0000135

Could anyone please give any suggestions on how to tackle installing
Doomsday? I don't have winetools or DCOM98, do I require them? I also
don't have any drivers installed for my radeon 9800 pro, would that be
a problem?

---

### Post by hikaricore on 2006-11-06
One thing you may want to do is get the latest version of wine incase some previous issues may have been corrected, unless your instructions specify that you have to use version 0.9.22, the current version is 0.9.24 and can be downloaded in DEB form at the winehq.org website.

The error message is basicly saying that you don't have ole32.dll or OLEAUT32.dll, you may need to download these (google search should track them down) and put them in your fake windows system32 dir, which should be at: ~/.wine/drive_c/windows/system32

If you're installing from a cd you may find the install runs more quickly if you copy the entire thing to your hard drive first.

And a note on winetools, this is no longer as far as I know in production and for the most part is simply not needed anymore.

I don't know anything about this game specificly, just giving you a few things to look at :)

---

### Post by Mooseus on 2006-11-06
I checked out the files that are apparently missing by using winefile, but they are there. I also copied the contents of the cd onto my hardrive and it made a noticeable improvement - until it got to 23% where it slowed down again. The only other thing I haven't tried is getting the latest version of Wine. I also noticed that where it goes really slow (at 23%), is when it's installing alot of bmp files.

---

