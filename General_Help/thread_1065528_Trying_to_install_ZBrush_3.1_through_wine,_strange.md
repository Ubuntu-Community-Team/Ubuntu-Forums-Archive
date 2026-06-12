---
title: "Trying to install ZBrush 3.1 through wine, strange error message"
date: 2009-02-10
forum: General Help
---

### Post by m9105826 on 2009-02-10
I'm trying to get ZBrush running through Wine. It's the only reason I keep Windows dual booted, and I'd like to get rid of that dependency. Anyway, when I attempt to run the installer through Wine, it runs through to "Copying new files" then stops, saying that it has encountered an error before all of the files could be copied. In the terminal, I get these errors:

fixme:advapi:LookupAccountNameW (null) L"matt" (nil) 0x33f80c (nil) 0x33f810 0x33f804 - stub
fixme:advapi:LookupAccountNameW (null) L"matt" 0x131098 0x33f80c 0x131f80 0x33f810 0x33f804 - stub
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 3 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 31 ignored L"CreateFolder" table values
err:msi:msi_cabextract FDICopy failed
err:msi:ACTION_InstallFiles Failed to extract cabinet: L"#Data1.cab"
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627


I can't figure out what's going on for the life of me, and I haven't seen anyone else who has had this problem with ZBrush 3.1 under Wine. My Wine version is 1.1.14. Any help would be awesome.

---

