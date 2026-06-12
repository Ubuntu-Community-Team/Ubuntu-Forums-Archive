---
title: "Wine running Black &amp; White (game)"
date: 2006-06-11
forum: Gaming &amp; Leisure
---

### Post by Maelgwyn on 2006-06-11
Hi All!

I've just tried to wine setup.exe from the Black & White cd and got the following error messages during the install:

(this bit isn't important as far as I know, it's just here in case it is! See the next one for the bit that stumps me)

```
nik@relativity:/media/cdrom$ sudo wine Setup.exe
Password:
fixme:ole:ITypeInfo_fnRelease destroy child objects
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ole:ITypeInfo_fnRelease destroy child objects
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ole:ITypeInfo_fnRelease destroy child objects
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000001
fixme:ole:NdrClearOutParameters (0xb448e1c0,0x10004212,0xb448e2d8): stub
fixme:win:SetWindowTextA setting text "InstallShield Wizard" of other process window (nil) should not use SendMessage
err:win:CreateWindowExA bad class name "Null Window"
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x20026
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\Lionhead Studios Ltd\\Black & White\\black.ico") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"Z:\\media\\cdrom0\\RunDll32 c:\\PROG~FBU\\COMM~CP1\\INST~JM1\\engine\\6\\INTE~MEX\\Ctor.dll,LaunchSetup \"c:\\Program Files\\InstallShield Installation Information\\{E51B4CD9-A0A6-4324-B26A-31B3F2DE26CE}\\Setup.exe\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\setup.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\Lionhead Studios Ltd\\Black & White\\black.ico") failed, error 193
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\Lionhead Studios Ltd\\Black & White\\black.ico") failed, error 193
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\ereg\\go_ez.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\ereg\\Black and White_eReg.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\Lionhead Studios Ltd\\Black & White\\help.ico") failed, error 193
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\Lionhead Studios Ltd\\Black & White\\black.ico") failed, error 193
err:menubuilder:extract_icon32 LoadLibraryExW (L"Z:\\media\\cdrom0\\RunDll32 c:\\PROG~FBU\\COMM~CP1\\INST~JM1\\engine\\6\\INTE~MEX\\Ctor.dll,LaunchSetup \"c:\\Program Files\\InstallShield Installation Information\\{E51B4CD9-A0A6-4324-B26A-31B3F2DE26CE}\\Setup.exe\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\Lionhead Studios Ltd\\Black & White\\black.ico") failed, error 193
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\Lionhead Studios Ltd\\Black & White\\black.ico") failed, error 193
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\readme.txt") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\ereg\\go_ez.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Lionhead Studios Ltd\\Black & White\\ereg\\Black and White_eReg.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\Lionhead Studios Ltd\\Black & White\\help.ico") failed, error 193
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\windows\\Uninst.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:advapi:QueryServiceObjectSecurity 0x7fd447f0 4 0x7fb8f060 512 0x7fb8ee4c
fixme:advapi:SetServiceObjectSecurity 0x7fd447f0 4 0x7fb8ee60
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

``` 
Then it kicked me back to the standard command line.

I cd'd to the ~/.wine/drive_c/Program Files/Lionhead Studios Ltd/Black & White and tried to sudo wine runblack.exe and got THIS error message:

```
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

``` 
Does anybody have a clue how I get around this? I'd love to play B&W!

---

### Post by elbryan on 2006-06-11
Uhm try to download "secdrv.sys" and put it into that directory (obviously following the wine path) (i.e. ~/.wine/drive_c/windows/system32/drivers).

That file it's quite difficult to find on the net so I've uploaded it for you from my Windows XP Professional partition.

Here is the link:
[http://www.filefactory.com/?da7e1b]("http://www.filefactory.com/?da7e1b")

Let me know ^^

---

### Post by Maelgwyn on 2006-06-11
hrm.. It doesn't seem to want to let me download it:

> 
Sorry, this file is no longer available. It may have been deleted by the uploader, or has expired.


Your new file is still being processed. It will be available to download in 5 minutes. If you see this message after more than 10 minutes, there may have been a problem with your upload (most likely your file is corrupt), and you will need to upload again.


shall I PM you with my email? :)

---

### Post by Perfect Storm on 2006-06-11
You properly also need to set it up with 'winecfg'.

---

### Post by Maelgwyn on 2006-06-11
In what respect? I'm not sure how to do this as I haven't used wine before!

---

### Post by Perfect Storm on 2006-06-11
I'm not an expert (or advance user) when it comes to wine, but when type winecfg a window shows up where you can add/remove diffrent .dll's to its libary.

---

### Post by Harleen on 2006-06-11
I'm not an expert for wine. But I know the missing file SECDRV.SYS belongs to the SafeDisc copy protection. And wine is known not to work too well with copy protection systems.
But even if you remove the copy protection, you probably won't have much success with this game either: [http://appdb.winehq.org/appview.php?versionId=257](http://appdb.winehq.org/appview.php?versionId=257)

---

### Post by Maelgwyn on 2006-06-12
Dang.

Is there another way to get this game running? Maybe Cedega?

---

### Post by Perfect Storm on 2006-06-12
Black and white is supported by cedega. [http://transgaming.org/gamesdb/ratings/view.mhtml?game_id=2317](http://transgaming.org/gamesdb/ratings/view.mhtml?game_id=2317) Just use the engine which have the highest rating.

---

