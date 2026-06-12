---
title: "Football manager 2007"
date: 2006-10-18
forum: Gaming &amp; Leisure
---

### Post by i0h on 2006-10-18
Hi, i got hold of FM2007 and i want to play it :(
but i cant get it work in wine .. anyone succeed? or know how to get it to work..

>> wine Setup\ FM2007\ PC.exe

fixme:msvcrt:__dllonexit bad table
fixme:msvcrt:__dllonexit bad table
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored


this is what comes up when i try to install :/

thanks in advance!

---

### Post by i0h on 2006-10-20
no one knows?

just installed latest wine (Wine 0.9.23)

and no more of that error msg i typed down before..

now its the same in the window.. 

[http://www.llamah.se/fm2k7_failed.png](http://www.llamah.se/fm2k7_failed.png)  <--here is a screenschot :)

hope someone can help me

---

### Post by skinny on 2006-11-02
**EDIT**: To use with wine I suggest installing the latest wine (not necessarily the one from the repo's, try the winehq website) and then skipping to [post #30]("http://ubuntuforums.org/showpost.php?p=1755926&postcount=30") of this thread.

To install updates, instructions lurk in the second part of [post #79]("http://ubuntuforums.org/showpost.php?p=1994488&postcount=79").

----

Hi i0h, I have tried using Wine with previous versions of Football Manager and had problems.

Yesterday I found an alternative solution, in that Wine is not used, but Football Manager 2007 runs on my 6.06 Dapper. **However you will have to have copy of Windows available.**

I assume you have used Automatix2 to install many of the goodies for Ubuntu, so hopefully you will have VMware Player installed. You can use this to run a virtual machine of Windows, and then in turn install and run Football Manager 2007 on this virtual Windows.

To create a virtual machine you will most likely want to visit this excellent [link]("http://www.easyvmx.com") which simplifies the process. This website will create a small set of files which act as the base configuration for your virtual machine. Unpack the files and simply double click the .vmx file to start the virtual machine in VMware Player. It will then prompt you for a an installation disk, and you will then have to put your Windows disk in the CD-ROM drive.

Once Windows has installed, and everything is to your pleasing (aside from the fact Windows is being used :() you should be able to install Football Manager as normal into the virtual Windows.

I have only briefly tested this solution, but it appears to run ok. The ingame matches are a bit stop-start, sometimes the 2D pitch has a good frame rate, and other times it slows down to a pathetic 3 fps. It never appears to skip completely, so you will always be able to view what occurred after any slow 3fps periods.

I am running:
---Football Manager 2007
--Windows XP w/SP2
-VMware Player 1.0.1
Ubuntu 6.06 (64bit)

Not a great solution due to the presence of Windows ](*,) however it does mean you will be able to play Football Manager 2007 and not boot your whole computer to Windows.

Now go get Sherman Cardenas (16yr Bucaramanga AMRC) 8) 

hope this helps for now, until someone finds a better solution

$

---

### Post by zarathustra on 2006-11-05
I have managed to get FM07 running under Wine. I have compiled the latest version of Wine (0.9.24). Have you got the latest version of Java for Windows installed with Wine?

---

### Post by oblivion on 2006-11-08
> **zarathustra said:**
> I have managed to get FM07 running under Wine. I have compiled the latest version of Wine (0.9.24). Have you got the latest version of Java for Windows installed with Wine?

Did you have to do anything special to install java in wine?
I have tried with the latest and an older version, but i can't get it to work... :(

---

### Post by zarathustra on 2006-11-08
> **oblivion said:**
> Did you have to do anything special to install java in wine?
I have tried with the latest and an older version, but i can't get it to work... :(

I just used the offline installation download for Windows from the Java website, and ran it through Wine.

---

### Post by oblivion on 2006-11-08
Well, i just deleted my .wine and "c" folders and then the java installed on my first try :confused: . And it looks like FM is working too! :D I managed to create a manager in league one and save, so i'm gonna make a cup of coffee and try it a bit further.

---

### Post by zarathustra on 2006-11-08
The problem of match highlights going at a crawl seems to have disappeared, at least I found that.

---

### Post by cornish on 2006-11-09
I managed to get this game working last week using cedega and wine, but after a rebuild of my PC I cant get the cursor to work in wine and when I try cedega I get an error about creating a temporary folder does any one know how to resolve these issues?

---

### Post by cornish on 2006-11-09
Ignore Previous message got it to work in wine again by setting it too win98

---

### Post by skinny on 2006-11-09
Good Job zarathustra! :D

However, I'm still having a few problems with Wine & FM. I've installed latest Wine (0.9.24), and have installed Java for Wine as suggested.  Football Manager 2007 installed - although only using the -console switch for the setup, which was a new experience. However, now when I attempt to run fm.exe, the following errors occur.

```
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

```

Any ideas? :-? Tried a bit of googling, but to no joy.
$

---

### Post by zarathustra on 2006-11-09
> **skinny said:**
> Good Job zarathustra! :D

However, I'm still having a few problems with Wine & FM. I've installed latest Wine (0.9.24), and have installed Java for Wine as suggested.  Football Manager 2007 installed - although only using the -console switch for the setup, which was a new experience. However, now when I attempt to run fm.exe, the following errors occur.

```
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

```

Any ideas? :-? Tried a bit of googling, but to no joy.
$

This is a problem with Wine not emulating the copy protection software properly. The only way to get round it is to use a no-CD patch. There's questions of legality but as long as you own your own copy I don't think there's much of a problem.

---

### Post by scotty2hott2k on 2006-11-10
so have the slow 2d pitch issues been fixed? ie, can i watch a 2d match at a reasonable speed rather than the 2-3fps in the old football manager/ wine version.

---

### Post by zarathustra on 2006-11-10
> **scotty2hott2k said:**
> so have the slow 2d pitch issues been fixed? ie, can i watch a 2d match at a reasonable speed rather than the 2-3fps in the old football manager/ wine version.

I haven't had any problems with it, I've been able to see my teams thrashed at full speed!

---

### Post by scotty2hott2k on 2006-11-10
YAS!!!! finally, been waiting ages for fm to work properly in wine :D, will be chuffed to bits if the 2d pitch is working :D

---

### Post by scotty2hott2k on 2006-11-10
right 2d pitch works ACE, however can't see a cursor, which is pretty annoying :(

---

### Post by zarathustra on 2006-11-10
> **scotty2hott2k said:**
> right 2d pitch works ACE, however can't see a cursor, which is pretty annoying :(

Try setting it to Windows 98.

---

### Post by skinny on 2006-11-11
> **zarathustra said:**
> This is a problem with Wine not emulating the copy protection software properly. The only way to get round it is to use a no-CD patch. There's questions of legality but as long as you own your own copy I don't think there's much of a problem.

Copied the no-cd patch over fine, the game starts up and everything is peachy. Except I have no mouse pointer ](*,)
I could play the game like this, since most clickable places have either tooltips or highlight when the (invisible) mouse cursor is over them. I'd just be really slow compared to normal zipping around with a visible mouse cursor.
Just wondering if you encountered this problem (and if so how did you solve it?;) )
EDIT: Just saw your replies to this problem that had been posted earlier but hadn't been reloaded into my browser. Win98 fixed it beautifully cheers!!

```
fixme:cursor:create_cursor Currently no support for cursors with 32 bits per pixel
```

cheers loads for all your help so far!!:D 

$

---

### Post by scotty2hott2k on 2006-11-11
cheers guys, the setting to win98 mode works a treat :D, finally fm works in wine like it should, can finally ditch vmware.

---

### Post by Kernel Sanders on 2006-11-11
Does the FM2007 editor work fine too? I am also curious about what happens when a patch is released? Can it be applied ok?

John :)

---

### Post by Jongi on 2006-11-12
I get the [following error](http://img295.imageshack.us/img295/5490/fm2007kn0.png) when running the FM installer (Kubuntu Edgy).

I have done the following

```

# wine jre-1_5_0_09-windows-i586-p.exe
wine: creating configuration directory '/home/jongi-kubuntu32/.wine'...
Failed to open the service control manager.
fixme:ole:ITypeInfo_fnRelease destroy child objects
wine: '/home/jongi-kubuntu32/.wine' created successfully.
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
err:msi:msi_dialog_oncommand button click from nowhere 0x1b8bc0 67108864 0x10040
err:msi:msi_dialog_oncommand button click from nowhere 0x1b8bc0 67108864 0x10040
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
err:msi:deformat_environment Unknown environment variable L"ALLUSERSPROFILE"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveExistingProducts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishComponents"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishFeatures"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterTypeLibraries"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveODBC"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterClassInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterExtensionInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterProgIdInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterMIMEInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveShortcuts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveDuplicateFiles"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveFolders"
err:msi:ITERATE_DuplicateFiles Failed to copy file L"c:\\Program Files\\Common Files\\Java\\Update\\Base Images\\jre1.5.0.b64\\patch-jre1.5.0_09.b03\\RegUtils.dll" -> L"c:\\Program Files\\Java\\jre1.5.0_09\\bin\\", last error 3
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"InstallODBC"
err:msi:ITERATE_Actions Execution halted, action L"unzipother" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
fixme:reg:GetNativeSystemInfo (0x33df58) using GetSystemInfo()
# wine Setup\ FM2007\ PC.exe
```

---

### Post by klund on 2006-11-12
Have a problem installing FM, i installed java fine but when the FM install program has initaliazed Java i get this error.


[IMG]http://www.klund.se/temp/error.jpg[/IMG] 
Anyone had the same problem??

---

### Post by scotty2hott2k on 2006-11-12
no sorry, did you use the pc-setup.exe rather than autorun.exe?

as for the patch, you will be able to apply and use the new patch HOWEVER due to copy protection you will need to wait til a nocd for the new version is released.

---

### Post by Completenutter2 on 2006-11-12
> **klund said:**
> Have a problem installing FM, i installed java fine but when the FM install program has initialized Java i get this error.


[IMG]http://www.klund.se/temp/error.jpg[/IMG] 
Anyone had the same problem??

I get exactly the same thing, no idea how to fix it :(

---

### Post by klund on 2006-11-12
Would really like to know how to fix it.

---

### Post by klund on 2006-11-12
Got something here.
Set up to use WinXP -> "wine Setup\ FM2007\ PC.exe -console" and it installed 
copy a crack to fix the protection issue. Changed back to win98 emulation and i got it to load. Hope it works now. Thats the way i did it. Good luck everyone.

---

### Post by klund on 2006-11-12
works like a charm so far. set it to save every week in case it will crash. now i will not need windows anymore. to bad beryl is very unstable so i have to use ordinary gnome instead.

---

### Post by Jongi on 2006-11-13
Did you get the output below after it installed

```

Finalizing the Vital Product Data Registry. Please wait...

-------------------------------------------------------------------------------
Football Manager 2007 - InstallShield Wizard

The InstallShield Wizard has successfully installed Football Manager 2007.
Choose Finish to exit the wizard.

Press 3 to Finish or 5 to Redisplay [3] 3
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - (nil) 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10032 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10030 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - 0x10030 0x161278 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10022 - 0x10030 0x161278 ): semi-stub
err:ole:CoUninitialize Mismatched CoUninitialize
[jongi:~#] C:\>del "C:\windows\temp\5628931.tmp"
C:\windows\temp\5628931.tmp :File Not Found
C:\>if exist "C:\windows\temp\5628931.tmp" goto Repeat
C:\>del "C:\windows\temp\cln8b15.bat"
Sharing violation

```

---

### Post by Jongi on 2006-11-13
klund how did you install java?

---

### Post by Completenutter2 on 2006-11-14
Ok, so here's a quick guide as to how I got it installed:

Install [Wine]("http://www.winehq.org/site/download-deb")

Run winecfg:

```
winecfg
```

Select Windows XP as the operating system.

Download and install [Java]("http://jdl.sun.com/webapps/download/AutoDL?BundleId=10778")

Browse to downloaded file, and install with wine:

```
wine '/home/alex/Games/jre-1_5_0_09-windows-i586-p-s.exe'
```

Follow onscreen instructions until thats all done :)

Browse to FM2007 folder and run PC.exe with the console flag with wine:

```
wine Setup\ FM2007\ PC.exe -console
```

Follow the on-screen instructions, and hopefully everything should install nicely.

run winecfg again, switch to Windows 98. And run the game!

---

### Post by mholtman on 2006-11-14
I noticed in your mini-HOWTO that you did not mention getting a nocd crack. Is that accurate? If it actually recognizes the CD copy protection, that would be fantastic.

I'm going to give this a try this evening. The only wrinkle is that I'm installing the US version, WSM 2007. I'll post back to this thread if I run into any issues. Wish me luck. WSM is the only thing keeping a Windows install in my house. ;)

---

### Post by Completenutter2 on 2006-11-14
Ah yes, I didn't check that, I was in a rush to get to work this morning, and it was installing that I was having a problem with.

You will probably need a NO-CD, although if you own the game, I don't see this being a legal issue.

I'm at work atm, but I'll check when I get home.

---

### Post by mholtman on 2006-11-14
Ah. Good to know. If you run into an issue, I'd be interested in hearing the solution. I own the game, always have, which means I'll need a little nudge in the right direction on where to find the NOCD patch. Hopefully there is one for my version!

---

### Post by Completenutter2 on 2006-11-14
I had a quick look around, but I can't find one for WSM :( There are ones for FM2007 though, so perhaps you could just rename that file to WSM.exe or whatever yours is called.

---

### Post by mholtman on 2006-11-14
I actually found one for FM 2007. I used in in place of the one for WSM 2007 and it works just fine. 

I started the game up in Ubuntu and it seemed to work. I haven't actually started a season though.

---

### Post by Completenutter2 on 2006-11-14
Works fine for me, 2D matches are smooth enough to enjoy too :)

---

### Post by skovenborg on 2006-11-14
I tried Completenutter2's guide and installed Java and it looks like it installed succesfully. But when I try to run the FM2007 Setup it gives me the error message:
```
WARNING: cannot instantiate string resolver method com.installshield.util.LocalizedStringResolver: com.installshield.database.ISSqlException: File input/output error: C:\windows\temp\ismp004\4748104\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0 [ CREATE TABLE Event(Event VARCHAR(255) NOT NULL PRIMARY KEY,EventText VARCHAR(255) NOT NULL,ActionSequence_ INTEGER)] caused by: java.sql.SQLException: File input/output error: C:\windows\temp\ismp004\4748104\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0
File input/output error: C:\windows\temp\ismp004\3028282\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0 [ CREATE TABLE Event(Event VARCHAR(255) NOT NULL PRIMARY KEY,EventText VARCHAR(255) NOT NULL,ActionSequence_ INTEGER)] caused by: java.sql.SQLException: File input/output error: C:\windows\temp\ismp004\3028282\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0WARNING: could not delete temporary file C:\windows\temp\ismp004
WARNING: could not delete temporary file C:\windows\temp\ismp004\4039452
WARNING: could not delete temporary file C:\windows\temp\ismp004\6389555
WARNING: could not delete temporary file C:\windows\temp\ismp004\4748104
WARNING: could not delete temporary file C:\windows\temp\ismp004\9294796
WARNING: could not delete temporary file C:\windows\temp\ismp004\3028282
```

I use wine 0.9.22 (installed from the package system) but could that really be the problem? Or didn't the JRE install correctly (it was a little buggy but in the end it looked like it worked).

---

### Post by skovenborg on 2006-11-14
> I use wine 0.9.22 (installed from the package system) but could that really be the problem? Or didn't the JRE install correctly (it was a little buggy but in the end it looked like it worked).

I really have to do more research next time. I downloaded the newest version of Wine and both Java and Football manager installed properly (although there was some error-messages when I installed FM but at least it didn't crash).

The only problem is that I can't actually use the game. When I run get passed the initial screens with all the logos and stuff it just stops with a black screen with the little nifty ball in the corner grayed out.

This is the output from the console:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

fixme:dbghelp:EnumerateLoadedModules If this happens, bump the number in mod
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
err:seh:setup_exception stack overflow 40 bytes in thread 0018 eip 7bc2f359 esp 00240fd8 stack 0x241000-0x350000
```
The last one is probably just because I try to quit the program with CTRL-C.

---

### Post by skovenborg on 2006-11-14
> **skovenborg said:**
> The only problem is that I can't actually use the game. When I run get passed the initial screens with all the logos and stuff it just stops with a black screen with the little nifty ball in the corner grayed out.

Fixed this by running the FM2007 with the --cache_skin=0 parameter. Now everything works fine :-)

---

### Post by Jongi on 2006-11-15
Gah it's been working all the time. There was a DirectSound dialog box that was obscured by the screen changing resolution to 640x480. I pressed Enter and it loaded.

---

### Post by pompeyjohn on 2006-11-25
oh I am so close!

I have followed all the steps above

wine fm.exe generates 

```
libGL warning: 3D driver claims to not support visual 0x5b
```

WTF???

and then I get a popup box showing 

```
A debugger has been detected / Unload the debugger and try again
```

SWTF?!?!

hopefully one of you FM linux ninja's can help!

cheers

john

ps. get Jo and Falcao - they are goal machines :D

---

### Post by DanGahan on 2006-11-29
Followed the steps given by Completenutter2 and still getting the error message


[IMG]http://www.klund.se/temp/error.jpg[/IMG] 

Where did people who got this to work install java, am I correct in thinking it belongs in the program files directory.

Apart from that I cant see where I'm going wrong. XP is selected for the install, I am using Wine version 0.9.9 as downloaded from semantic package manager.

I do keep getting warning messages, which I am not hundred percent sure about :-

```
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

```

Any help would be great 

Dan



> **Completenutter2 said:**
> Ok, so here's a quick guide as to how I got it installed:

Install [Wine]("http://www.winehq.org/site/download-deb")

Run winecfg:

```
winecfg
```

Select Windows XP as the operating system.

Download and install [Java]("http://jdl.sun.com/webapps/download/AutoDL?BundleId=10778")

Browse to downloaded file, and install with wine:

```
wine '/home/alex/Games/jre-1_5_0_09-windows-i586-p-s.exe'
```

Follow onscreen instructions until thats all done :)

Browse to FM2007 folder and run PC.exe with the console flag with wine:

```
wine Setup\ FM2007\ PC.exe -console
```

Follow the on-screen instructions, and hopefully everything should install nicely.

run winecfg again, switch to Windows 98. And run the game!

---

### Post by skinny on 2006-11-30
> **DanGahan said:**
> ...I am using Wine version 0.9.9 as downloaded from semantic package manager.


You need a more up-to-date version of wine than 0.9.9. 
AFAIK most recent version of wine is 0.9.25, I use 0.9.24 and it works sweet. Not sure if this will solve all your problems but it should help. Let us know how you get on.

$

---

### Post by DanGahan on 2006-11-30
> **skinny said:**
> You need a more up-to-date version of wine than 0.9.9. 
AFAIK most recent version of wine is 0.9.25, I use 0.9.24 and it works sweet. Not sure if this will solve all your problems but it should help. Let us know how you get on.

$

Updated my version of wine to 0.9.26 but still getting the same error, any other suggestions?

Dan

---

### Post by skinny on 2006-11-30
> Where did people who got this to work install java, am I correct in thinking it belongs in the program files directory.

that is where I have installed it.

> Got something here.
Set up to use WinXP -> "wine Setup\ FM2007\ PC.exe -console" and it installed
copy a crack to fix the protection issue. Changed back to win98 emulation and i got it to load. Hope it works now. Thats the way i did it. Good luck everyone.

Have you tried this? Is your error message the exact same as klunds' a few pages back? Are you trying to install java using the -console switch?

$

---

### Post by DanGahan on 2006-11-30
My error is exactly the same, except with my directories instead of his

Am I correct in thinking -console just sends the messages to the console rather than displaying them in a window?

I am pretty sure my java has installed properly, i tried installing the jdk also, i ran the javac.exe command without specifying a file to compile and the correct error was displayed

maybe i'm being a total idiot somewhere, but I cant work it out!

Cheers in advance for any other suggestions

Dan

> **skinny said:**
> that is where I have installed it.



Have you tried this? Is your error message the exact same as klunds' a few pages back? Are you trying to install java using the -console switch?

$

---

### Post by skinny on 2006-12-01
The -console switch forces you to run the installation through a command line (in the terminal) rather than using a window. Most (all?) of us have had to install it this way, the GUI setup just seems to not want to work. The installation is basically the same as it would be with the GUI, except its just all text.
If you run "winecfg" does it say Windows XP in the combo box at the bottom of the Applications tab? If not set it so that it does. (Mind and change it back to Windows 98 after a succesful install and before running the game).
 [[IMG]http://img124.imagevenue.com/loc549/th_75221_Screenshot_skinny@skinny64skinful:_media_cdrom0_122_549lo.jpg[/IMG]](http://img124.imagevenue.com/img.php?image=75221_Screenshot_skinny@skinny64skinful:_media_cdrom0_122_549lo.jpg)

---

### Post by DanGahan on 2006-12-01
Yeah its set on XP

Using -console switches just brings up the same error but in the console

Starting to think it has to be something to with my Java install, will try removing that and reinstalling it


> **skinny said:**
> The -console switch forces you to run the installation through a command line (in the terminal) rather than using a window. Most (all?) of us have had to install it this way, the GUI setup just seems to not want to work. The installation is basically the same as it would be with the GUI, except its just all text.
If you run "winecfg" does it say Windows XP in the combo box at the bottom of the Applications tab? If not set it so that it does. (Mind and change it back to Windows 98 after a succesful install and before running the game).
 [[IMG]http://img124.imagevenue.com/loc549/th_75221_Screenshot_skinny@skinny64skinful:_media_cdrom0_122_549lo.jpg[/IMG]](http://img124.imagevenue.com/img.php?image=75221_Screenshot_skinny@skinny64skinful:_media_cdrom0_122_549lo.jpg)

---

### Post by eduarm76 on 2006-12-01
The 7.01 patch was released yesterday. So we might have to wait some days for a new no-cd patch.

Here is the [changelog]("http://www.sigames.com/static/changelist.txt")

---

### Post by Mohamad1979 on 2006-12-01
> **eduarm76 said:**
> The 7.01 patch was released yesterday. So we might have to wait some days for a new no-cd patch.

Here is the [changelog]("http://www.sigames.com/static/changelist.txt")

hi friend
i wonder for help
is the new no cd patch will be install from si or this is a crack
can u please describe 4 me this point

---

### Post by DanGahan on 2006-12-02
> **Mohamad1979 said:**
> hi friend
i wonder for help
is the new no cd patch will be install from si or this is a crack
can u please describe 4 me this point

It Would have to be a crack I imagaine, its the only way around the copy protection.

But as long as you actually own the game I don't really see this being an issue.

---

### Post by eduarm76 on 2006-12-03
has anyone been lucky with the 7.01 path, it doesn't seem to work

---

### Post by mholtman on 2006-12-07
Anyone found a no-cd for 7.01 that is available?

I've been happily running the 7.0 version on Ubuntu for 3 weeks now. It's awesome.

---

### Post by skinny on 2006-12-07
There is one available I believe, although I've not installed it yet, and I'm still debating if its really worth it.

[This]("http://www.fuk.co.uk/threads/fm2007_no_cd_crack_that_works_with_new_patch?from=0&comments_per_page=20") was the first result from a Googling "FM 2007 crack" but it appears that SI have left "bugs" in the game which double the transfer fee of anyone using a tampered exe. :mad:

as Our Graham says, the choice is yours...

---

### Post by anarchoal on 2006-12-07
It wouldn't install for me in WinXP mode, I had the same errors at DanGahan. Win2000 mode worked though.

---

### Post by Madhoax on 2006-12-09
Here's the solution to play Football Manager 2007, patched version 7.0.1 without the double transfer bug, and no training bug.

Solution to the problems:

- uninstall fm2007
- install again, DON'T OVERWRITE FM.EXE
- install patch, DON'T OVERWRITE FM.EXE
- download this: [http://gf.wiretarget.com/fm/poseden-fm07.rar](http://gf.wiretarget.com/fm/poseden-fm07.rar)
- use this iso file in deamon tools
- Download [Sd4Hide](http://www.dvhardware.net/modules.php?name=Downloads&d_op=getit&lid=60)
- start Sd4Hide
- start fm07


There ya go :D Now the transfer bug is gone, it's like a legitimate copy.

In another forum I received comments that the above explenation wasn't clear, so here's some more explenation:

Ok, I hope the following explanation is better:

The file posedon-fm07.rar contains a posedon-fm07.iso file. This is a file to fool the system. The system read the file as like the original fm07 cd. However to use this, you need a **original installation** of FM07. So don't overwrite the fm.exe file in any way. Otherwise this 'tool' won't work. If you overwrite the fm.exe file with a nocd patch, you will get version 7.2.1, this is the version WITH the double transfer prices. You want version 7.0.1, the good working (patched) version of fm07. 

So the first thing you need to do to use this is uninstall fm07 when you have used a nocd patch. You can do this by going to the configuration screen and then choose software -> delete (or something like this). Choose fm07 and uninstall it. The savegames plus edited databases will NOT be deleted. 

Then install a fresh installation of FM07, without replacing the fm.exe file. Use the patch, so fm version will be 7.0.1. (patch can be downloaded from sigames.com). 

Now unrar the posedon-fm07.iso file to any folder in the system (I unrarred it in my fm07 folder, for convience). Download the [Sd4Hide](http://www.dvhardware.net/modules.php?name=Downloads&d_op=getit&lid=60) tool and put this in the same folder as the .iso file. Use sd4hide when mounting the iso file. Otherwise you have a chance that you receive a blacklist registration from daemon tools (whatever the hell that is). 

Now mount the .iso file and enjoy your fm!

Great thing about this way of working is that it works on all patches, you never need to download a nocd patch cause you work with the 'original' cd.

> 
yea but after that then what because im getting the no cd error do you use the crack?


Don't use the crack

I tried some things with my FM07. **This doesn't seem to work when you don't use safedisc4hider (see above for link). If you don't have sd4hider enabled, you will get the no cd error!**

> 
Same as. I extract the original. then extract the 2nd and there is no ISO file in there. I have tried everything so far!

Think I'm having a blonde moment.


- You extract the posedon-fm.rar file
- This .rar files contains an .iso file
- Mount this posedon-fm07.iso file by using daemon tools

Required for this is a:
- original (fresh) installation of fm07 (patch 7.0.1 can be applied)
- Enabled sd4hide


> 
If you mean after install, when trying to run the game? Yes, you need the nocd patch.


If you use the nocd patch, you will get fm07 version 7.2.1. In this version the players don't train and transfer prices will double. 

So follow the above steps, don't replace the original fm07.exe!!! This is really important if you want fm07 version 7.0.1!

---

### Post by i0h on 2006-12-10
easiest way i found was to install FM07 on my girlfriends laptop (winxp)
and then just copy the whole dir to my wine dir and then run..

and yeah... wine setting Win98.. :)

damn big the thread become :D tobad i havent read it since the day after i posted ](*,)

---

### Post by coolbedog on 2006-12-11
Many Thanks,

I've got my fm 2007 running smoothly now! However I have noticed that none of the player pictures load up, even though I have selected the "show player pictures" box in the preferences box.

Has anybody else had this problem?

It's a small problem I know, but it's really doing my head in!](*,)

---

### Post by skinny on 2006-12-12
Do you definitely have the pictures for the players you are clicking on? Not that many of the players have pictures for their profiles in the original install, but there exist some excellent facepacks.

I believe I use the packs available in this [thread]("http://community.sigames.com/eve/forums/a/tpc/f/420106/m/8922096862"). You should also be able to find out how to install the facepack there too. :)

Although I can't verify now, I believe that players who start in the Championship or League 1 (in England) *do* have a picture in the original install. Try clicking on those players...is it just the silhouette that appears, or nothing at all?

$

---

### Post by Crazysah on 2006-12-14
I heard there was a working no cd crack on torrentleach.... can someone confirm?

---

### Post by DanGahan on 2006-12-15
> **anarchoal said:**
> It wouldn't install for me in WinXP mode, I had the same errors at DanGahan. Win2000 mode worked though.

The problem I had was with my Java install, the result of me not properly removing a previous install of wine before attempting to install the current version.

Running perfect now, gotta love this game

---

### Post by Kinty on 2006-12-15
Okey. I'm new to Linux. can smeone tell me how to install the NOCD crack? like. Step by step =D

The install did got smoothe, i also downloaded Norwegain so the game is on Norwegian. need help to place that in the right folder too ;)

---

### Post by Crazysah on 2006-12-16
So did anyone check out the torrentleach file?

[http://www.fuk.co.uk/threads/fm2007_no_cd_...nts_per_page=20](http://www.fuk.co.uk/threads/fm2007_no_cd_crack_that_works_with_new_patch?from=20&comments_per_page=20)

The person who posted is chopper. He says there is one available on torrent leach?

Can anyone confirm this?

---

### Post by skinny on 2006-12-17
**@Crazysah:** Not able to get into Torrentleech, not a member. Send me an invite and I'll check ;)
Alternatively, have you tried the last file listed at the link below?

**@Kinty:** Have you downloaded the replacement exe? Step by step instructions:
1. Rename your current (original) fm.exe file, located in the Football Manager 2007 directory (just as a backup)
2. [Download]("http://www.gameburnworld.com/gp/gamefixes/footballmanager2007.shtml") a new fm.exe (I think you want the first file filesize 4.87Mb)
3. Place the new fm.exe in the Football Manager 2007 folder.

:D Run FM as normal...

The above link has some other interesting files but I've yet to try any of them.  I'll try to check them out later this week and report back, unless someone else is desperate to get their FM patched to 7.0.1 and checks them first....

As for the Norwegian translation files....erm I dunno. It must say either in the manual or on the si forums - I tried looking but I just get sidetracked horribly....(he says over an hour later). Best of luck!

$

---

### Post by Mezmerized on 2006-12-19
> **pompeyjohn said:**
> oh I am so close!

I have followed all the steps above

wine fm.exe generates 

```
libGL warning: 3D driver claims to not support visual 0x5b
```

WTF???

and then I get a popup box showing 

```
A debugger has been detected / Unload the debugger and try again
```

SWTF?!?!

hopefully one of you FM linux ninja's can help!

cheers

john

ps. get Jo and Falcao - they are goal machines :D

Same error here... Please can someone help with 2 errors? I can't play :( 

Other question (a stupid question probably) where are my files located to replace de fm.exe for the crack :-# 

Thanks

---

### Post by skinny on 2006-12-20
> **Mezmerized said:**
> Same error here... Please can someone help with 2 errors? I can't play :( 

Other question (a stupid question probably) where are my files located to replace de fm.exe for the crack :-# 

Thanks

Not sure about the first error...sorry!
Second error: If you replace the fm.exe with the crack it shouldn't occur anymore.
You can find where it is installed on your system by searching for fm.exe (add a search button to a gnome panel if you're using gnome, and then use that it will serve you well :))
or
have a poke about your home folder. do you have a .wine folder there? If it contains a drive_c folder (or similar), then you should be able to navigate to FM directory if you can recall where on your (wine) C drive you installed it. If you can't find the .wine folder make sure that you are showing hidden files and folders (its in the View menu on Nautilus, or you can just press Ctrl-H). Of course you may not need to do this, it may be that a c folder is just sitting in your home directory, it all depends on which version of Wine and how you set it up.

Hope this helps,
$

---

### Post by martibs on 2006-12-21
This is what I get when I try to install. After showing the loading box, it gives this error:

```
$wine Setup\ FM2007\ PC.exe -console
WARNING: cannot instantiate string resolver method com.installshield.util.LocalizedStringResolver: com.installshield.database.ISSqlException: File input/output error: C:\windows\temp\ismp001\4323393\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0 [ CREATE TABLE Event(Event VARCHAR(255) NOT NULL PRIMARY KEY,EventText VARCHAR(255) NOT NULL,ActionSequence_ INTEGER)] caused by: java.sql.SQLException: File input/output error: C:\windows\temp\ismp001\4323393\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0
File input/output error: C:\windows\temp\ismp001\8607310\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0 [ CREATE TABLE Event(Event VARCHAR(255) NOT NULL PRIMARY KEY,EventText VARCHAR(255) NOT NULL,ActionSequence_ INTEGER)] caused by: java.sql.SQLException: File input/output error: C:\windows\temp\ismp001\8607310\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0WARNING: could not delete temporary file C:\windows\temp\ismp001
WARNING: could not delete temporary file C:\windows\temp\ismp001\858191
WARNING: could not delete temporary file C:\windows\temp\ismp001\6475608
WARNING: could not delete temporary file C:\windows\temp\ismp001\4323393
WARNING: could not delete temporary file C:\windows\temp\ismp001\5566987
WARNING: could not delete temporary file C:\windows\temp\ismp001\8607310
```

I guess it's got something to do with my java install? Anyone know what I need to do to fix this?

---

### Post by Mezmerized on 2006-12-21
Thanks **skinny** :-D 

@ **martibs**:
I have this problem too but after install the java windows offline installation solve the problem .

---

### Post by kokezz on 2006-12-21
players pictures are not showing, what should i do?

---

### Post by skinny on 2006-12-21
@Mezmerized: Glad to have helped :)

@kokezz: have you seen [post #59]("http://ubuntuforums.org/showpost.php?p=1875655&postcount=59")? Try clicking on a few (England) Championship players - do their pictures show?

PS Should have news on updates + new crack tonight..

$

---

### Post by skinny on 2006-12-22
:-# crack available at the link below will allow you to play the updated (v7.0.1) version of the game. Just checked it's ok, and couldn't see any suspicious transfer financial goings on. Did a deal for a player for £5m and it turned up in the expenses at £5m so don't think that its suffering the double transfer deliberate bug.

Of course, I'm still going to carry on my old career on my main PC with no updates, because my [COLOR="Purple"]Fiorentina[/COLOR] are cruising. 8)

Installing the update is pretty simple, once you've downloaded the hefty 80mb download just run it with wine, and then again copy over the fm.exe with the one you [download]("http://www.gameburnworld.com/dl/dl.php?file=FootballManager2007v7.0.1ProperWorkingNoCDFixedexeEng.rar").

Please note I have not played more than a week (in the game) on the new updated version so any bugs that crop up after then, well, sorry! But I'm sure it'll be fine...;) 

$

---

### Post by fm07 on 2006-12-22
Hi, my mate bought FM07 recently and he gave couple of his mates copies. Well it worked for most of them, but when I try and install part 1 of the game the instalation just goes on and on for ages. I tried to install it( I left it for 1 day!) but it doesnt work. Please help guys or else I'll have to play Championship Manager instead. The only reason I don't buy a new game is because now I'm not sure if it will work! :(:(

---

### Post by mermi on 2006-12-24
> **fm07 said:**
> Hi, my mate bought FM07 recently and he gave couple of his mates copies. Well it worked for most of them, but when I try and install part 1 of the game the instalation just goes on and on for ages. I tried to install it( I left it for 1 day!) but it doesnt work. Please help guys or else I'll have to play Championship Manager instead. The only reason I don't buy a new game is because now I'm not sure if it will work! :(:(

I bought FM07 but couldn't play it because of that weird java instalator:evil:  And using a shity cdrom I scratched my cd on the edge so now I can only install the game (on windows) but can't play it because constantly getting massage "insert proper cd"](*,)  So I had to find other solution to play it on ubuntu. The solution was to download a ripped FM07 (of course you can copy FM directory after installing it on windows) and wait for a working crack for version 7.0.1. With all this now I can play FM using wine:-D 

So this is a final solution for all ubuntu users with oryginal Fm of course:)
1. If you have other computer with windows install FM on it. (if not, go to 3.)
2. Copy instalation directory from windows to your computer with ubuntu (f.e. .wine/drive_c/)
3. Or find somewhere ripped version of FM2007 and copy it to .wine/drive_c/
4. Download official patch 7.0.1
5. Install the patch using wine
6. Download a crack, that **skinny** gave link to.
7. After replacing original fm.exe with the cracked one you can play FM2007 using wine :KS

---

### Post by XxFM GODxX on 2006-12-30
Yeh i have a no-cd crack with no double tranfers ;)

---

### Post by zarathustra on 2006-12-30
> **Mezmerized said:**
> Same error here... Please can someone help with 2 errors? I can't play :( 

Other question (a stupid question probably) where are my files located to replace de fm.exe for the crack :-# 

Thanks

I've found the debugger error usually occurs if you're emulating the wrong version of Windows.

---

### Post by lanre on 2007-01-03
:-d

---

### Post by smiggs on 2007-01-03
> **mermi said:**
> 
So this is a final solution for all ubuntu users with oryginal Fm of course:)
1. If you have other computer with windows install FM on it. (if not, go to 3.)
2. Copy instalation directory from windows to your computer with ubuntu (f.e. .wine/drive_c/)
3. Or find somewhere ripped version of FM2007 and copy it to .wine/drive_c/


The java installation **does work** you just need to install java for windows using the offline installer in Windows 2000 mode.

> 7. After replacing original fm.exe with the cracked one you can play FM2007 using wine

I have found to see the cursor you need to run fm in Windows 98 mode. I don't think FM would be much fun without a cursor! :mrgreen:

---

### Post by attercop on 2007-01-09
> **mermi said:**
> I bought FM07 but couldn't play it because of that weird java instalator:evil:  And using a shity cdrom I scratched my cd on the edge so now I can only install the game (on windows) but can't play it because constantly getting massage "insert proper cd"](*,)  So I had to find other solution to play it on ubuntu. The solution was to download a ripped FM07 (of course you can copy FM directory after installing it on windows) and wait for a working crack for version 7.0.1. With all this now I can play FM using wine:-D 

So this is a final solution for all ubuntu users with oryginal Fm of course:)
1. If you have other computer with windows install FM on it. (if not, go to 3.)
2. Copy instalation directory from windows to your computer with ubuntu (f.e. .wine/drive_c/)
3. Or find somewhere ripped version of FM2007 and copy it to .wine/drive_c/
4. Download official patch 7.0.1
5. Install the patch using wine
6. Download a crack, that **skinny** gave link to.
7. After replacing original fm.exe with the cracked one you can play FM2007 using wine :KS

I'm using wine 0.9.28 on my Kubuntu 6.06 and i installed the latest java using the offline exe. That appeared to install ok.

Then i successfully installed fm2007 as i would in windows, with the java installation wizard that worked fine.

Then i got the unload debugger message which i got rid of using the crack posted on this thread. However when i started fm.exe up in wine all i got was a black screen and a system beep, though the fm cursor was on screen and working.

Now i'm following the quoted method above. I've copied the fm directory from windows, and i've got the official patch. However when i try to install the patch with wine i get the following error.

```
andy@kubuntu:~$ wine fm2007_patch_7.0.1.exe
err:module:map_image Could not map section _winzip_, file probably truncated
err:module:map_image Could not map section _winzip_, file probably truncated
wine: could not load L"Z:\\home\\andy\\fm2007_patch_7.0.1.exe": Bad EXE format for
```

Could anyone offer some advice?

---

### Post by skinny on 2007-01-10
> all i got was a black screen and a system beep, though the fm cursor was on screen and working.
Have you tried pressing Enter? Perhaps you're experiencing the same as Jongi was? see post 40...

> ```
andy@kubuntu:~$ wine fm2007_patch_7.0.1.exe
err:module:map_image Could not map section _winzip_, file probably truncated err:module:map_image Could not map section _winzip_, file probably truncated wine: could not load L"Z:\\home\\andy\\fm2007_patch_7.0.1.exe": Bad EXE format for
```

I assume you are trying to install the update?

To install the update:
1. Download the official 80Mb update from sigames.net (IIRC the file is called 463.exe).
2. In a terminal ```
wine 463.exe
```
3. Download the crack (link to it a few posts back) 8-[
4. Backup the fm.exe in your FM directory and copy the downloaded crack to your FM directory.

$

---

### Post by attercop on 2007-01-10
> **skinny said:**
> Have you tried pressing Enter? Perhaps you're experiencing the same as Jongi was? see post 40...



I assume you are trying to install the update?

To install the update:
1. Download the official 80Mb update from sigames.net (IIRC the file is called 463.exe).
2. In a terminal ```
wine 463.exe
```
3. Download the crack (link to it a few posts back) 8-[
4. Backup the fm.exe in your FM directory and copy the downloaded crack to your FM directory.

$

I know about the crack already, and downloaded it some time ago. But i can't get the patch to go on.

Typing "wine patch_name.exe" was the first thing i did and i get the win-zip error. I still get this error whether it's called 463.exe or whatever.

I'm pretty close now, i just need to get the patch working and i'm sure i'll be playing it soon.

---

### Post by skinny on 2007-01-10
Ok, I was merely checking that you were definitely trying the correct file.

A quick google shows that ["Any Self-Extracting EXE files will run with no special config nor copying of DLL files."]("http://appdb.winehq.org/appview.php?iAppId=1104"). All I can suggest at present is perhaps your update is corrupt and to download the update from si again? This would fit with the last line of your error (and the 2nd and 3rd lines now that I read it again):
```
wine: could not load L"Z:\\home\\andy\\fm2007_patch_7.0.1.exe": Bad EXE format for
```
Not really what you want to hear but it's all I can think it can be for now.:-k 

$

---

### Post by attercop on 2007-01-11
> **skinny said:**
> Ok, I was merely checking that you were definitely trying the correct file.

A quick google shows that ["Any Self-Extracting EXE files will run with no special config nor copying of DLL files."]("http://appdb.winehq.org/appview.php?iAppId=1104"). All I can suggest at present is perhaps your update is corrupt and to download the update from si again? This would fit with the last line of your error (and the 2nd and 3rd lines now that I read it again):
```
wine: could not load L"Z:\\home\\andy\\fm2007_patch_7.0.1.exe": Bad EXE format for
```
Not really what you want to hear but it's all I can think it can be for now.:-k 

$
Sir you are a genius, and a fellow Gooner to boot!

The patch i'd downloaded from the official site was bad somehow, and i remembered that i'd already downloaded it once on Windows, so i tried that one. Straight in and patched it up.

The game now starts up, and though i'm yet to test it properly for crashing and bugs, i have every reason to believe that i'm free from Windows once again!

Here's what worked for me.

1. Installed latest Java, offline method.
2. Installed FM2007 using working Java wizard.
3. Copied entire directory from Windows just in case.
4. Downloaded and installed official patch.
5. Downloaded and patched with FootballManager2007v7.0.1ProperWorkingNoCDFixedexeEng.rar, as linked to on this thread.
6. System beep and black on startup but pressing Enter takes us into the game.

Sorted! Many thanks again, and i shall be the one in the Arsenal shirt at the game vs City on Jan 30th :)

---

### Post by dolny on 2007-01-11
How do I get it fullscreen :/ ?

```
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?

```

Do you have any command line arguments to force fullscreen?

---

### Post by skinny on 2007-01-12
[Command line options found here.]("http://sigames.com/sibase.php?type=view&id=199"). This includes fullscreen options, smallscreen options, and you can also change the fullscreen height and width options if you're playing on a widescreen and don't want that horrible stretch affect.

**@dolny**: 
```
wine fm.exe --fullscreen=true

```

Curiously, I can force it into fullscreen through the terminal, but adding that option on the end of my (Gnome) launcher results in nothing happening.:???: 

**@attercop**: No more windows! :D And even Aliadiere looks like a world-beater! Is this a dream?! Did someone say 6-3?! :mrgreen: 

$

---

### Post by attercop on 2007-01-12
> **skinny said:**
> **@attercop**: No more windows! :D And even Aliadiere looks like a world-beater! Is this a dream?! Did someone say 6-3?! :mrgreen: 

$
I know! What's going on!?

Just another quick query. Has anyone had any luck enabling sound? Presumably this only comes on during matches anyway, but whenever i enable it in my preferences the game crashes at the point when sounds are to be played. The game shrinks away and dies, and an error box says: "DirectSound Error: No Driver"

Am i just going past the current limitations of Wine in expecting sound or have i made a schoolboy error somewhere?

---

### Post by dolny on 2007-01-12
> **skinny said:**
> [Command line options found here.]("http://sigames.com/sibase.php?type=view&id=199"). This includes fullscreen options, smallscreen options, and you can also change the fullscreen height and width options if you're playing on a widescreen and don't want that horrible stretch affect.

**@dolny**: 
```
wine fm.exe --fullscreen=true

```

Curiously, I can force it into fullscreen through the terminal, but adding that option on the end of my (Gnome) launcher results in nothing happening.:???: 

**@attercop**: No more windows! :D And even Aliadiere looks like a world-beater! Is this a dream?! Did someone say 6-3?! :mrgreen: 

$

Thanks a lot mate. :)

---

### Post by skinny on 2007-01-12
> Has anyone had any luck enabling sound?

Yeah sound working here. Are you using ALSA? At a terminal
```
winecfg
```
and click the Audio tab, make sure ALSA is ticked and ignore the

ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

if it appears in terminal because it happens fo rme but I get sound ok...

$

---

### Post by berthanas on 2007-01-13
> **martibs said:**
> This is what I get when I try to install. After showing the loading box, it gives this error:

```
$wine Setup\ FM2007\ PC.exe -console
WARNING: cannot instantiate string resolver method com.installshield.util.LocalizedStringResolver: com.installshield.database.ISSqlException: File input/output error: C:\windows\temp\ismp001\4323393\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0 [ CREATE TABLE Event(Event VARCHAR(255) NOT NULL PRIMARY KEY,EventText VARCHAR(255) NOT NULL,ActionSequence_ INTEGER)] caused by: java.sql.SQLException: File input/output error: C:\windows\temp\ismp001\4323393\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0
File input/output error: C:\windows\temp\ismp001\8607310\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0 [ CREATE TABLE Event(Event VARCHAR(255) NOT NULL PRIMARY KEY,EventText VARCHAR(255) NOT NULL,ActionSequence_ INTEGER)] caused by: java.sql.SQLException: File input/output error: C:\windows\temp\ismp001\8607310\isdb.properties java.lang.ArrayIndexOutOfBoundsException: 0WARNING: could not delete temporary file C:\windows\temp\ismp001
WARNING: could not delete temporary file C:\windows\temp\ismp001\858191
WARNING: could not delete temporary file C:\windows\temp\ismp001\6475608
WARNING: could not delete temporary file C:\windows\temp\ismp001\4323393
WARNING: could not delete temporary file C:\windows\temp\ismp001\5566987
WARNING: could not delete temporary file C:\windows\temp\ismp001\8607310
```

I guess it's got something to do with my java install? Anyone know what I need to do to fix this?

i'm getting the very same error. anyone know how to fix it?

---

### Post by skinny on 2007-01-13
Have you succesfully completed the offline java install for windows for your wine?

> @ martibs:
I have this problem too but after install the java windows offline installation solve the problem 

$

---

### Post by berthanas on 2007-01-13
> **skinny said:**
> Have you succesfully completed the offline java install for windows for your wine?



$

oops i missed that. but when i try to install the offline java, simply nothing happens :) here's the screenshot. This is the first time i'm using wine so i have no idea what to do. (i've downloaded the offline java installation)

[[IMG]http://img160.imageshack.us/img160/2120/bbzb7.th.jpg[/IMG]](http://img160.imageshack.us/my.php?image=bbzb7.jpg)

---

### Post by skinny on 2007-01-13
Hi berthanas I've never encountered this before so lets try and figure it out. Can you open a terminal and go to your system32 directory within your wine folder?

To navigate to mine I have to cd to .wine/drive_c/windows/system32 but on your computer it may be different.
From there can you type ```
ls
```Do you have a java.exe file present? If so, can you then type ```
wine java.exe -version
```

Hopefully you'll see something like:
```
skinny@ubuntulaptop:~/.wine/drive_c/windows/system32$ wine java.exe -version
java version "1.5.0_09"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_09-b03)
Java HotSpot(TM) Client VM (build 1.5.0_09-b03, mixed mode, sharing)

```
If you don't see the above, then we need to do some more reading and thinking! :-k 
If you do see the above (or something similar) then your java would appear to have been installed ok, and so maybe retry installing FM 2007 again.

good luck!

$

---

### Post by berthanas on 2007-01-13
unfortunately there is no java.exe in the system32 directory. i tried the 1_5_0_10 version of the java offline installation also but still nothing happens ](*,) .

i've been searching the forum, the net but i haven't found anything yet.

EDIT: i've tried the both versions of the java installer in windows 2000 and all the other modes in wine but still nothing...

---

### Post by skinny on 2007-01-14
This is weird. Done a bit of searching here and there but nothing that really matches your problem.

Java is obviously not installed, so...
1. What's the size in Mb of the java offline exe that you downloaded? It should be about 15.82Mb. If your [jre-1_5_0_x-windows-i586-p-s.exe]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=10879") is significantly less I would definitely recommend downloading it again and retrying to install it as you were before.
2. If 1. doesn't work, as you were: ](*,) 

Scratching my head here, dunno why it wouldn't work for you normally apart from the download being corrupt etc.

$

---

### Post by berthanas on 2007-01-14
i checked the file size and it is 15.8 mb. Tried downloading with and without a download accelerator. still nothing happens and it doesn't make any sense. so still ](*,)  :) . i've spent hours to search but i couldn't find a similar problem. i'm gonna install ubuntu 6.10 and try again. i hope i'll work.

and skinny thank you very much for helping...

---

### Post by skinny on 2007-01-14
What version of wine do you have? Provided that it is 0.9.24 or later, I don't envisage that it is the problem, but perhaps if you have an old version then that could be your problem.

FM has worked on wine on Dapper and Edgy.  But if an update to Edgy fixes this strange error, then it's worth it, although I'm not quite sure why it would fix it.

Good luck!

$

---

### Post by mermi on 2007-01-14
berthanas - do you have a amd 64bit platform?

---

### Post by skinny on 2007-01-14
Do you think that should affect it mermi?

I only ask because I am currently using amd 64bit Edgy (and until about 2 weeks ago amd 64bit Dapper). I've never had problems but would be keen to hear if you've had any problems with Football Manager or any other games and amd 64bit setups.

$

---

### Post by attercop on 2007-01-15
> **skinny said:**
> Yeah sound working here. Are you using ALSA? At a terminal
```
winecfg
```
and click the Audio tab, make sure ALSA is ticked and ignore the

ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: wrong ELF class: ELFCLASS64
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

if it appears in terminal because it happens fo rme but I get sound ok...

$

Brilliant. Sorted once again. It's actually running stable as in Windows and with sound now! Nice one.

Three in three for King Henry. The King is back. Long live the King.

---

### Post by redeyes32 on 2007-01-17
hi.i can run this game but my mouse is invisible.anyone know how to fix it???

---

### Post by redeyes32 on 2007-01-17
sorry for previous post i can fix it by use windows98 to play it. 

but this sunday we gonna smile right skinny because we going to win the red devil right?

bless for the king, Henry

---

### Post by berthanas on 2007-01-17
> **mermi said:**
> berthanas - do you have a amd 64bit platform?

sorry for late response but i have finals these days and i don't have time...

no i'm using a Dell Latitude 110L laptop. 


i installed 6.10 edgy and at last i've managed to get errors at least :) it's better than nothing. :) now i'm not home and writing from another computer so not sure about the error but when i try to install the java it says lib3dl or "something like that" error. it has been asked in this thread. i've checked the net and most probably it is because the Intel 910GML graphics chipset. Still searching for a solution. i'll post the actual error message in first chance.

---

### Post by sagarhshah on 2007-01-18
Hiya,

Has anyone used football manager with crossover office instead of wine?
If so did you encounter any problems with your installation or gameplay or anything with it so ever?

---

### Post by skinny on 2007-01-18
**@sagarhshah**: CrossOver Office appears to be built on wine, only with a few extra tweaks, so I imagine that a recent version of Crossover should be able to run Football Manager 2007.  I would question whether Crossover is able to work harmoniously with SafeDisc v4 which is the only reason why No-cd patches are mentioned in this thread.

**@berthanas**: maybe you should wait til after your finals??!! g'luck with them btw...

**@redeyes32 & attercop**: :D. but lets all (inc. me!) leave the Arsenal chat for another thread, and try to keep this one for FM 2007.

$

---

### Post by DBFT on 2007-01-23
Just moved over to Ubuntu from Windows

Enjoying it so far but my attempts at getting FM to work have been futile

I cannot get past installing java - I have tried the latest JRE(1.6) and also the one that you guys managed to get working,  I get the following:

> dbft@dbft-desktop:~/Downloads$ wine jre-1_5_0_09-windows-i586-p-s.exe
fixme:advapi:LookupAccountNameW (null) L"dbft" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"dbft" 0x172f10 0x34f808 0x172f28 0x34f804 0x34f810 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
err:msi:msi_dialog_oncommand button click from nowhere 0x1b9340 67108864 0x10040
err:msi:msi_dialog_oncommand button click from nowhere 0x1b9340 67108864 0x10040
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
err:msi:deformat_environment Unknown environment variable L"ALLUSERSPROFILE"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveExistingProducts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishComponents"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishFeatures"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterTypeLibraries"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveODBC"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterClassInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterExtensionInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterProgIdInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterMIMEInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveShortcuts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveDuplicateFiles"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveFolders"
err:msi:ITERATE_DuplicateFiles Failed to copy file L"c:\\Program Files\\Common Files\\Java\\Update\\Base Images\\jre1.5.0.b64\\patch-jre1.5.0_09.b03\\RegUtils.dll" -> L"c:\\Program Files\\Java\\jre1.5.0_09\\bin\\", last error 3
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msvcrt:MSVCRT__sopen : pmode 0x0124 ignored
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Java\\jre1.6.0\\bin\\client\\jvm.dll") not found
fixme:reg:GetNativeSystemInfo (0x7d97cf40) using GetSystemInfo()
dbft@dbft-desktop:~/Downloads$ wine jre-1_5_0_09-windows-i586-p-s.exe
fixme:advapi:LookupAccountNameW (null) L"dbft" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"dbft" 0x172f10 0x34f808 0x172f28 0x34f804 0x34f810 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
err:msi:ITERATE_Actions Execution halted, action L"MaintenanceWelcome" returned 1602
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
fixme:reg:GetNativeSystemInfo (0x33db54) using GetSystemInfo()


Anybody know how I would solve this as FM is pretty much the only game I ever played on Windows:guitar: 

Thanks

---

### Post by DBFT on 2007-01-23
Doesnt matter - got past it by installing on a windows machine and copying the files over. Thanks anyway =D>

---

### Post by raul_ on 2007-01-26
Is it supposed to be using 100% CPU most of the times? i know it isn't a light game but since it doesn't have nothing graphic in it, just data processing i find it strange that a game like that consumes so much CPU

---

### Post by Pedro84 on 2007-02-13
I got serious problems. I can't install my FM:

Here's screenshot:
[http://www.fotosik.pl/pokaz_obrazek/23a7b1ffd7115787.html](http://www.fotosik.pl/pokaz_obrazek/23a7b1ffd7115787.html)

Hmm. I have to use no-CD crack? Which one is compatibile with 7.01 patch?

I'd be very pleased with Your help!

BTW. I can't run Virtual Machine now cause I have too low hdd's space.

---

### Post by Pedro84 on 2007-02-13
Anyone knows?

---

### Post by Pedro84 on 2007-02-14
Heeeelp!:mad:

---

### Post by raul_ on 2007-02-14
Did you try to install it with Wine?

The link to the crack is posted on this thread, some posts back (#59 or so)

---

### Post by Pedro84 on 2007-02-14
Is the crack necessary?

I tried to instal Deamon Tools. The newest version can't even install. version 3.47 installed but can't run [error: No language support!]

Any suggestions?


I use this crack but I can't choose database, can't load game from Windows. Game version in "game statu" is 7.0.0.92972 [or something similar]

---

### Post by raul_ on 2007-02-14
I use the crack with no problems whatsoever. It's necessary if you want to play without the cd.

I never looked much into Daemon tools in Ubuntu, so i can't help you there

---

### Post by Pedro84 on 2007-02-14
> **raul_ said:**
> I use the crack with no problems whatsoever. It's necessary if you want to play without the cd.

Question. Can You choose database when starting new game? Could You be so nice and upload or email crack You use, please?

---

### Post by raul_ on 2007-02-14
I can choose the old database and the patch's database. So I guess I can...

As I said, i use the one that was posted in this thread, post #59 i think. Worked for me.

---

### Post by Pedro84 on 2007-02-14
> **skinny said:**
> **@Crazysah:** Not able to get into Torrentleech, not a member. Send me an invite and I'll check ;)
Alternatively, have you tried the last file listed at the link below?

**@Kinty:** Have you downloaded the replacement exe? Step by step instructions:
1. Rename your current (original) fm.exe file, located in the Football Manager 2007 directory (just as a backup)
2. [Download]("http://www.gameburnworld.com/gp/gamefixes/footballmanager2007.shtml") a new fm.exe (I think you want the first file filesize 4.87Mb)
3. Place the new fm.exe in the Football Manager 2007 folder.

:D Run FM as normal...

The above link has some other interesting files but I've yet to try any of them.  I'll try to check them out later this week and report back, unless someone else is desperate to get their FM patched to 7.0.1 and checks them first....

As for the Norwegian translation files....erm I dunno. It must say either in the manual or on the si forums - I tried looking but I just get sidetracked horribly....(he says over an hour later). Best of luck!

$



You mean in this post?
Do You use first file filesize 4.87Mb?

Just replace original fm.exe?

Sorry but I never cracked software;)

Cheers

---

### Post by simonmac on 2007-02-18
Daft question but after i (hopefully) have installed FM how do I run the program?

---

### Post by Pedro84 on 2007-02-20
> **simonmac said:**
> Daft question but after i (hopefully) have installed FM how do I run the program?


You can type in Terminal
```

cd /path/to/Your/FM/in/wine/folder/
wine fm.exe

```

or simply use shortcut in the menu /if wine made one/


BTW. I use the crack and I got conract bug:( Ehhh.

---

### Post by scotty2hott2k on 2007-02-20
which contract bug is that? ive got the latest patch installed with a nocd patch (from megagames) and it works flawlessly.

---

### Post by Pedro84 on 2007-02-20
> **scotty2hott2k said:**
> which contract bug is that? ive got the latest patch installed with a nocd patch (from megagames) and it works flawlessly.


That when player reject new contract offer and the contract expires. Could You upload and PM me with Your no-cd patch link?

I will be very happy. If You dodn't believe I can attach some screenschots. I play on my old save. This save was perfect. Started on Windows, with ORIGINAL fm.exe, of course patched.

---

### Post by CurtyD13 on 2007-02-22
I just installed FM2007 with help from this thread and everything worked flawlessly from the start, however today I installed beryl and FM2007 no longer works no matter what window manager I use. When I run fm.exe I get an text box with "Unable to open fullscreen mode". and the following error messages in the console
```
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
```
Anybody had any problems like this or have any idea what might be going on?

---

### Post by scotty2hott2k on 2007-02-23
can;t help sorry, however try running it in a managed window mode (goto wineconf and create a virtual desktop in that), if not try running football manager with the windowed mode flag.

---

### Post by CurtyD13 on 2007-02-24
Well I got it to work today. I'm not exactly sure what I did to fix it but I went into beryl settings and checked "Enable workarounds for certain Wine and legacy windows" which might have fixed it.

---

### Post by AndyCooll on 2007-03-22
I just want to say thanks to everyone in this thread for helping me to get FM07 working  with Wine.

I've been using Linux for a couple of years now. Only one app has required me to keep using Windoze, this game. Despite repeated attempts I never could get it to work. Anyway, yesterday I finally cracked it!

As usual with these things, the resolution is easy (when you know how!) and you wonder why you ever struggled. However I had struggled, and yesterday was a great release!!

So ...thanks everyone.

:cool:

---

### Post by Bap on 2007-04-02
This might be abit off track but it is referring to fm07

I just got FM2007 running on wine without any hickups, but upon testing network mode, i found no one could connect as the ports have'nt been forwarded is there a way to forward the ports through terminal?

---

### Post by nardz on 2007-04-06
I am trying to install FM07 as per the instructions in post #30 and i get the following error when trying to run the installation of FM07.

libGL warning: 3D driver claims to not support visual 0x4b
err:seh:setup_exception stack overflow 124 bytes in thread 000b eip b7e9854f esp 00230f84 stack 0x231000-0x340000

The java installation seemed to work ok with some warnings though..

any help would be appreciated :)

i'm fairly new to linux and am sick of dual booting to windows every time i wanna play.

---

### Post by AndyCooll on 2007-04-06
> **nardz said:**
> I am trying to install FM07 as per the instructions in post #30 and i get the following error when trying to run the installation of FM07.

libGL warning: 3D driver claims to not support visual 0x4b
err:seh:setup_exception stack overflow 124 bytes in thread 000b eip b7e9854f esp 00230f84 stack 0x231000-0x340000

The java installation seemed to work ok with some warnings though..

any help would be appreciated :)

i'm fairly new to linux and am sick of dual booting to windows every time i wanna play.

Since you already have the game running in Windoze, the easiest way to get FM to work is to copy the "Sports Interactive" folder in your Program Files in Windows over to your Wine folder in Linux (which will be somewhere along the lines of: /home/yourname/.wine/drive_c/Program Files).

Then replace the fm.exe with a patched NO-CD copy for the version of the game [Football Manager 2007 NO-CD patches]("www.gameburnworld.com/gp/gamefixes/footballmanager2007.shtml").

:cool:

---

### Post by Bap on 2007-04-07
Has anyone managed to get network mode working, trying to host a game but wont allow users to connect :(

---

### Post by scotty2hott2k on 2007-04-08
i couldn't host but when a friend hosted i could connect to his game and play perfectly fine.

---

### Post by Bap on 2007-04-13
Same, ive managed to connect to other people hosting, but when people try to connect to me, it just doesnt want to work :(

---

### Post by Cleves on 2007-04-15
> **CurtyD13 said:**
> Well I got it to work today. I'm not exactly sure what I did to fix it but I went into beryl settings and checked "Enable workarounds for certain Wine and legacy windows" which might have fixed it.

I got the same problem you had but I'm not using Beryl but Compiz.

Any idea how can I fix it?

---

### Post by oxygala on 2007-05-09
Hey folks,

I have FM2007 working almost flawlessly under feisty, however the 2d match engine is rather slow. Besides, the speed of the match does not change no matter what I try on the left hand side speed sliders of the match engine. Do you have the same problem, is it related to the java or wine version (which are rather updated actually) or is there something else that I'm missing?

edit: ok, no problem anymore, related to old wine version.

---

### Post by scotty2hott2k on 2007-05-09
what version of wine are you running? i haven't played it in quite a while now, but the 2d pitch slow speed issue was fixed, unless newer evrsions of wine have a regression in them.

---

### Post by Enverex on 2007-05-09
The AppDB has it rated as gold - [http://appdb.winehq.org/appview.php?iVersionId=7387](http://appdb.winehq.org/appview.php?iVersionId=7387)
Which basically meant it should run really well. As well as Scotty's question, do you have OpenGL set up properly in Linux?

---

### Post by VOD on 2007-05-10
> **pompeyjohn said:**
> oh I am so close!

I have followed all the steps above

wine fm.exe generates 

```
libGL warning: 3D driver claims to not support visual 0x5b
```

WTF???

and then I get a popup box showing 

```
A debugger has been detected / Unload the debugger and try again
```

SWTF?!?!

hopefully one of you FM linux ninja's can help!

cheers

john

ps. get Jo and Falcao - they are goal machines :D

I have encounter the same problem. i am using ubuntu 7.04 feisty with wine 9.33 to run FM 2007 but failed. i have follow the step to install jre first and then install fm2007 with -console parameter.
who can help me out this problem?
thank you very much for your help.

---

### Post by scotty2hott2k on 2007-05-10
you need a nocd patch as wine doesn't support the cd copy protection.

---

### Post by VOD on 2007-05-10
i already use the nocd patch...

---

### Post by VOD on 2007-05-10
i have try this and find that i could not use 7.02 nocd patch but can use 7.0 nocd patch.
so i can enjoy 7.0 now. Thank you very much.
but how can i use 7.02 nocd patch?

---

### Post by Enverex on 2007-05-10
> **VOD said:**
> i already use the nocd patch...

You need to use a better one that actually works because it's still checking. Also, the "doesn't support visual" can be ignored.

---

### Post by arijit on 2007-05-19
I have successfully installed and playing FM 2007 under Debian GNU/Linux.
Thanks to you guys, and wine.

See the attachment.

I followed the instructions from [http://appdb.winehq.org/appview.php?iVersionId=7387](http://appdb.winehq.org/appview.php?iVersionId=7387)
thanks to all, again
:):):):):):):)

:guitar:

---

### Post by vuroth on 2007-06-10
Unfortunately, I suspect that my problems are a bit different.  WSM 2007, the downloaded version using elicense rather than a CD protection thingy.  Install ok (wine, feisty), runs ok first time.  Next time I try to run, I get a popup saying:

> Sorry, could not get a license at this time.
Please try running this program later.
23
0

In the terminal:

> err:advapi1:service_control_dispatcher failed to create pipe for L"LicCtrlService", error=0

Edit:  running the 7.0.2 patch....

Hope I'm not on my own on this one....

V

---

### Post by scotty2hott2k on 2007-06-11
have you tried repalcing the .exe with  a nocd version? (maybe try a football manager nocd patch instead of world soccer manager one).

---

### Post by wild_oscar on 2007-07-04
Is it a problem with my configuration, or does the FM Editor run super slow under wine?

---

### Post by adoato on 2007-07-05
> **scotty2hott2k said:**
> you need a nocd patch as wine doesn't support the cd copy protection.

Where can I find this nocd patch?

---

### Post by wild_oscar on 2007-07-05
Where is the Hall of Fame file when running under wine?

---

### Post by AndyCooll on 2007-07-06
> **adoato said:**
> Where can I find this nocd patch?

Here: [FM2007 NO-CD patches]("http://www.gameburnworld.com/gp/gamefixes/footballmanager2007.shtml")

:cool:

---

### Post by AndyCooll on 2007-07-06
> **wild_oscar said:**
> Where is the Hall of Fame file when running under wine?

They should be in your /home folder. The actual FM program files themselves will be in Wine's (normally) hidden folder /home/yourname/.wine/ etc etc ...can't remember the rest. CTRL+H will reveal your hidden folders.

:cool:

---

### Post by wild_oscar on 2007-07-06
> **AndyCooll said:**
> They should be in your /home folder. The actual FM program files themselves will be in Wine's (normally) hidden folder /home/yourname/.wine/ etc etc ...can't remember the rest. CTRL+H will reveal your hidden folders.

:cool:

Found it

Under Windows, the file is in the folder 

Documents and Settings/All Users/Documents/Sports Interactive/Football Manager 2007

, not in the game folder.

Under wine, it should be in

~/.wine/drive_c/windows/profiles/All Users/Documents/Sports Interactive/Football Manager 2007

---

### Post by nuno19 on 2007-07-21
has anyone been able to host a game in network mode or to connect to someone?

---

### Post by oxygala on 2007-10-03
hi,

i recently switched from feisty to gutsy beta. i can still play fm 2007 without much problem but there's one small thing. in feisty i used to play the game fullscreen, but in gutsy gnome toolbars still appear in front of the game screen. i remember having this problem in feisty sometime, but i can't remember what it was about and how i solved it. any idea?

---

### Post by wild_oscar on 2007-10-03
> **oxygala said:**
> hi,

i recently switched from feisty to gutsy beta. i can still play fm 2007 without much problem but there's one small thing. in feisty i used to play the game fullscreen, but in gutsy gnome toolbars still appear in front of the game screen. i remember having this problem in feisty sometime, but i can't remember what it was about and how i solved it. any idea?

Is the in-game option for fullscreen active?

---

### Post by scotty2hott2k on 2007-10-03
are you running compiz? if so that is the problem.

---

### Post by oxygala on 2007-10-03
@wild_oscar, yes, fullscreen is on.

@scotty, yes i'm running compiz. probably that's the problem but it's strange as it seemed they solved this in early beryl stages. i've been using desktop effects and fm2007 together for quite a reasonable amount of time. 

thanks lads.

---

### Post by wild_oscar on 2007-10-04
> **oxygala said:**
> @wild_oscar, yes, fullscreen is on.

@scotty, yes i'm running compiz. probably that's the problem but it's strange as it seemed they solved this in early beryl stages. i've been using desktop effects and fm2007 together for quite a reasonable amount of time. 

thanks lads.

If you confirm compiz is the problem, make sure to tell us about it.


BTW, has anyone tried the FM 2008 demo on Linux?

---

### Post by scotty2hott2k on 2007-10-04
haven't tried it yet, but would imagine it will work.

---

### Post by oxygala on 2007-10-05
> **wild_oscar said:**
> If you confirm compiz is the problem, make sure to tell us about it.


BTW, has anyone tried the FM 2008 demo on Linux?


I can definitely confirm this is compiz related, no such problem occurs when I start FM fullscreen in case desktop effects are disabled.

---

### Post by AndyCooll on 2007-10-09
> **wild_oscar said:**
> If you confirm compiz is the problem, make sure to tell us about it.


BTW, has anyone tried the FM 2008 demo on Linux?

I've tinkered. So far only got it to run under a VMware XP image.

:cool:

---

### Post by wild_oscar on 2007-10-09
> **AndyCooll said:**
> I've tinkered. So far only got it to run under a VMware XP image.

:cool:

I'm still enjoying FM 2007 (and rulling the footballing world, I might add), so haven't tried 2008 yet.

If you find a way to play it under wine on another forum, please drop by with a guide through!

Cheers

---

### Post by oxygala on 2007-10-11
> **wild_oscar said:**
> I'm still enjoying FM 2007 (and rulling the footballing world, I might add), so haven't tried 2008 yet.

If you find a way to play it under wine on another forum, please drop by with a guide through!

Cheers

There you go:

[http://ubuntuforums.org/showthread.php?p=3513650#post3513650](http://ubuntuforums.org/showthread.php?p=3513650#post3513650)

---

