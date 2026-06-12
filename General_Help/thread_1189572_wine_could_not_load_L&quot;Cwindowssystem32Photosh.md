---
title: "wine: could not load L&quot;C:\\windows\\system32\\Photoshop.exe&quot;: Module not found--HELP!"
date: 2009-06-16
forum: General Help
---

### Post by House101 on 2009-06-16
Help! I'm attempting to run Elements 5 in Wine and this is what happens when I run it from Terminal. When I just plain click on a shortcut nothing happens. My Wine directory doesn't even have a system32 folder, and that's not the folder I'm initially running it from. I'm sick of trying to configure my system to run the the programs I need and hitting a wall (especially when those so-called help files don't even help).:mad:

---

### Post by ezramorris on 2009-06-17
> **House101 said:**
> Help! I'm attempting to run Elements 5 in Wine and this is what happens when I run it from Terminal. When I just plain click on a shortcut nothing happens. My Wine directory doesn't even have a system32 folder, and that's not the folder I'm initially running it from. I'm sick of trying to configure my system to run the the programs I need and hitting a wall (especially when those so-called help files don't even help).:mad:

Your .wine directory definitely should have a system32 folder!

Open a terminal, and type the following:
```
mv .wine .wine.old
winecfg
```

The first command will move your existing wine directory out of the way, and the second will create a new one.

In the dialog that appears, set any options you like, and click OK.

Then try installing Photoshop Elements again, and try launching it from the terminal.

WINE can be pretty temperamental at times, and thing can change for better or worse between versions.

---

### Post by House101 on 2009-06-19
I found the problem, the welcome window doesn't seem to exist, I have to run it from the Editor or the Organizer file. The thing is I now have a new problem. I can run it, but it crashes at "loading preferences", and tells me the EULA Agreement is declined or invalid. My dad got a similar error (one that's all over the net w/ Windows computers), but I don't get the second half of that says that the Serial # and name/company are invalid. I figure its similar enough to be able to fix by reinstalling, but now the wine un-installer shows 3 'Adobe Photoshop Elements 5.0' options and none of them will let me uninstall the program. :mad::mad::mad::mad::mad::mad:

---

### Post by ezramorris on 2009-06-19
> **House101 said:**
> I found the problem, the welcome window doesn't seem to exist, I have to run it from the Editor or the Organizer file. The thing is I now have a new problem. I can run it, but it crashes at "loading preferences", and tells me the EULA Agreement is declined or invalid. My dad got a similar error (one that's all over the net w/ Windows computers), but I don't get the second half of that says that the Serial # and name/company are invalid. I figure its similar enough to be able to fix by reinstalling, but now the wine un-installer shows 3 'Adobe Photoshop Elements 5.0' options and none of them will let me uninstall the program. :mad::mad::mad::mad::mad::mad:

Moving or deleting the .wine folder makes WINE create a new set of settings and fake C drive, so after doing that there shouldn't be anything in the uninstaller, and if there is, then no files for it will actually exist.

Out of interest, what version of WINE are you using?
```
wine --version
```

---

### Post by House101 on 2009-06-19
1.01
I couldn't get rid of the damn thing so I un-installed all of wine. The launcher for wine was still there after I did a complete removal of wine, as well as the short cut to PSE 5 and the wine folder(wow my computer is a mess). When I clicked on them nothing happened, not even an error, so I just deleted them(probably not very smart, but I was getting pretty annoyed with the thing by then). I reinstalled wine, but the launcher won't re-appear, so I'm currently Wine-free. I'm going to reinstall it and see if it goes well, fingers-crossed!;)

---

### Post by ezramorris on 2009-06-22
> **House101 said:**
> 1.01
I couldn't get rid of the damn thing so I un-installed all of wine. The launcher for wine was still there after I did a complete removal of wine, as well as the short cut to PSE 5 and the wine folder(wow my computer is a mess). When I clicked on them nothing happened, not even an error, so I just deleted them(probably not very smart, but I was getting pretty annoyed with the thing by then). I reinstalled wine, but the launcher won't re-appear, so I'm currently Wine-free. I'm going to reinstall it and see if it goes well, fingers-crossed!;)

You should still be able to access wine from a terminal though.

Edit the menu by right clicking>Edit Menus, and making sure the items inside the wine section are checked.

---

### Post by ezramorris on 2009-06-22
Did you try this?

[LIST]
[*]Go to .wine/drive_c/Program Files/Adobe/Photoshop Elements 5.0
[*]Rename PhotoshopElementsFileAgent.exe to something else eg. 0-PhotoshopElementsFileAgent.exe
[*]Open system monitor and end PhotoshopElementsFileAgent.exe if it is running.
[/LIST]
(From [The WINE Application Database]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8904&iTestingId=24099").)

---

### Post by t0p on 2009-06-22
> **House101 said:**
> 1.01
I couldn't get rid of the damn thing so I un-installed all of wine. The launcher for wine was still there after I did a complete removal of wine, as well as the short cut to PSE 5 and the wine folder

Dude, people have already told you this: you can get rid of the wine folder and all the directories and files and config files very easily, simply by deleting the .wine directory that is in your home directory.  Open a terminal and type in the command

```
cd
```

That takes you to your home directory.  Next type in the command

```
rm -r .wine
```

That will delete the .wine directory and everything in it.  Once that's done, you can run the command

```
winecfg
```

which will configure the wine program and a new .wine directory.  Or you can use the Applications menu to run the Configure Wine option.

As for the version of Photoshop you want to run in Wine: have you checked in the [Wine Applications Database]("http://appdb.winehq.org/") that that particular version does actually work with Wine?  Lots of programs work fine in Wine... but there are also plenty that won't work.

---

### Post by dazman19 on 2009-06-22
or you can copy the file you want to execute into your /home/username/.wine/drive_c/ folder and execute it from there.

---

### Post by House101 on 2009-09-28
Appaerently WINE doesn't pick up after itself, it leaves bits everywhere. I went around picking them all up and then reinstalled WINE and PSE. Very useful thing to do. Got it working all the way up to the Welcome screen and it crashes. Something to do with MyCatalog.pse. If you have the same problem or know what it is, please reply to my other thread:
[**MyCatalog.psa not found in Organizer and Editor doesn't even load (Adobe PSE 5)**]("http://ubuntuforums.org/showthread.php?p=7976445#post7976445")

Otherwise, I'm marking this as solved... =;

---

