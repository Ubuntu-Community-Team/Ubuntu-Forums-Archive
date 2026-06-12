---
title: "Rosetta Stone v.3.2.11 with wine?"
date: 2009-06-07
forum: General Help
---

### Post by TheoryWeary on 2009-06-07
I just made the jump to ubuntu last week so please be gentle.. I realize that Wine is not finished and generally requires quite a lot of work before it works, but people claim to have gotten Rosetta stone working with it. 

I'm trying to install rosetta stone in wine and it doesn't seem to install. I get an error inside the windows installer that says:  "The wizard was interupted before Rosetta stone V3 could be completely installed.   Your system has not been modified, to complete the installation at another time please run setup again"

Has anyone had experience with this?

Here is my terminal output:
> 
brendon@ubuntu:~/Desktop/rosettaStoneCopied$ wine setup.exe
fixme:advapi:LookupAccountNameW (null) L"brendon" (nil) 0x33f87c (nil) 0x33f880 0x33f874 - stub
fixme:advapi:LookupAccountNameW (null) L"brendon" 0x12d6a0 0x33f87c 0x12ed70 0x33f880 0x33f874 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
err: ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err: ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 4 ignored L"CreateFolder" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:domdoc_createNode unhandled node type 2
fixme:msxml:DllCanUnloadNow 
err:msi:custom_get_thread_return Invalid Return Code -2302
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603


I had to include spaces in these two lines in the first "err: ole" since the forum was displaying them as smilies and said i was over the image limit. 

err: ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err: ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created 

How do i post code in one of those code boxes?

Many thanks for everyone in the community! I've learned tons by searching here each time i come to a roadblock, and up till now there was always a solution easily found.

---

### Post by Nexusx6 on 2009-06-08
That's odd since the WineHQ database has a platinum rating for this version of Rosetta Stone, meaning that it install and run without any hiccups.
[Database Link]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=15349")

What version of wine are you using?

```
wine --version
```

Also, to make code blocks when posting, you can push the pound symbol (#).

---

### Post by TheoryWeary on 2009-06-08
```
brendon@ubuntu:~/Desktop/rosettaStoneCopied$ wine --version
wine-1.0.1
```

I believe this is the latest version.

---

### Post by Nexusx6 on 2009-06-08
Ah, that's probably the source of the problem. Version 1.0.1 is the latest *stable* release, but it isn't the latest version. What's going on is that Wine releases a version they consider very stable once in a while, but they have on going releases about once a month of a 'beta' version that is always more advanced than it's stable counter part but considered a little unstable. It is **strongly** advised that you use this periodic updates versus the stable release.

The Ubuntu repositories by default only downloads from the stable releases of wine. What you want to do is add the Wine repository to your sources list so that you have the latest releases now and every time there is an update. Before I forward the link and how to do this (its very easy) I recommend uninstalling the Wine version you have now. You wont have to do this everytime, just this once since you're getting a much more advanced version from a different repo. The terminal commands would be

```
sudo apt-get purge wine
rm -r ~/.wine  //This will delete your wine folder in home
```

To get the latest version from the Wine Repo's, follow the instructions here: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

You can always check up on Wine at [www.winehq.org](www.winehq.org) and see the database about what success users have gotten to getting a program running by going to the AppDB tab at the top while you're over there. This update should be all you need to get Rosette Stone working, but if you have anymore questions feel free to keep asking

---

### Post by WatchingThePain on 2009-06-08
I tried to run a Linux course on wine.
The strange thing was that it was geared up to run on Windows.
Put in the W64 codecs.
It worked but the sound was like coming from underwater.

---

### Post by TheoryWeary on 2009-06-08
Thanks for the help! It is now installed and working. You were right about the wine version causing that problem. 

One word of warning for anyone else reading this: immediately after the install it tried to launch and came up with a fatal error. After a few minutes of puzzled searching I tried to run it again from the applications menu for no real reason and it worked. I've opened it about five times since and it works every time, i guess the installer launcher just has a problem with wine?

---

