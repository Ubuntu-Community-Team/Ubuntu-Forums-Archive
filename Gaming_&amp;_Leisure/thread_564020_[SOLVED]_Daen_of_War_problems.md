---
title: "[SOLVED] Daen of War problems"
date: 2007-09-30
forum: Gaming &amp; Leisure
---

### Post by madsmeg on 2007-09-30
Hey all :)

I may not have many posts, but trust me i have read through everything to find a solution to this, so don't pass me off too lightly :)

I am trying to install Dawn of War (who would have guessed by the topic title eh?)

I have tried installing from the CD and every time i get to put disk 2 in it the first WILL NOT come out. i have tried unmounting, and i have tried "wine eject d:" (says there is no cd drive there apparently) i even tried "wine eject -a" with no luck either. 

so i went with putting all the cd's into 1 folder and doing a wine install from there, now im having an error turn up, please help, altho its fun to figure out how to install things... im now lost and cant find any way of doing it

Thanks in advance

---

### Post by Cappy on 2007-09-30
Hi, try running this from your HOME directory
```
wine /media/cdrom/setup.exe
```
You'll need to edit that for the correct path. The important thing is that you don't navigate the console into the cdrom's folder(s).
When you get ready to switch cds you'll probably need to open a new terminal and type ```
wine eject
```


My second suggestion is to open the cdrom in Nautilus (the file browser) and then right click on the setup.exe or install.exe (or whatever) and click "open with" and click "Use a custom command" and type in "wine". Now click "open".
When you need to switch CDs you can try the "wine eject" or you can try right clicking on the CD-ROM on the Desktop and clicking "eject".

---

### Post by madsmeg on 2007-09-30
tried both of these suggestions, wine isnt seeing my d: as a cd device for some reason

thanks for the quick reply to a cackly spelt thread :p

so basically it wont let me eject the CD no matter what i try :(

I dont really understand why it will not install out of the folder though. This is the what my terminal is telling me

```

jon@jon-desktop:~$ wine Desktop/DoW/DawnOfWar.exe
fixme:advapi:LookupAccountNameW (null) L"jon" (nil) 0x34f7fc (nil) 0x34f800 0x34f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"jon" 0x12f058 0x34f7fc 0x12e5f0 0x34f800 0x34f7f4 - stub
err:msi:call_script Could not find CLSID for Windows Script
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 6 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 15 ignored L"CreateFolder" table values
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\BugReport\\BugReport.exe" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\BugReport\\BugReport.ini" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Drivers\\shader.txt" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Drivers\\ati.txt" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Drivers\\nvidia.txt" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Drivers\\spdx9_config.txt" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Engine.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\GraphicsOptions\\GOTData.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kData-Whm-Low.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kData-Whm-Medium.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kData.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kData-Whm-High.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\relic_intro.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\credits.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\relic_intro.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\dow_intro.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\credits.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\dow_intro.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS11_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS05_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M11.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS06_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS03_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M01.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS09_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS09_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS02_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M02.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S10.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS11_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M03.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S11.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M04.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S01.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS10_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS06_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M05.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S02.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M06.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S03.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS08_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS05_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS03_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS02_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M07.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S04.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M08.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S05.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M09.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S06.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS07_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S07.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S08.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS04_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS04_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS01_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S09.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS07_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS08_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS01_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS10_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M10.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kDataGOTY.sga" (error 2)
err:msi:ACTION_InstallFiles compressed file wasn't extracted (L"c:\\Program Files\\THQ\\Dawn Of War\\BugReport\\BugReport.exe")
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603



```

---

### Post by Cappy on 2007-09-30
Have you run ```
winecfg
```
and gone to the "Drives" tab and added your CDrom drive to the list as D:?

---

### Post by Sandlst on 2007-10-01
Have you tried looking up the AppDB entry for Dawn of War under winehq?  If you haven't, some special instructions are down the page for installation: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2576]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2576")

---

### Post by madsmeg on 2007-10-01
@ Cappy, yes i have :p

 @ Sandlst thanks i'll take a look now and try it when i get home.

---

