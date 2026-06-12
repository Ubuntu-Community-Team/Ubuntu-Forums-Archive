---
title: "Unity/ Wine issues"
date: 2011-12-25
forum: Desktop Environments
---

### Post by volare on 2011-12-25
After 2 whole days of Ubuntu experience, could be Unity, could be Wine, so my questions:

- When I position the Wine Configuration icon into my launcher, it creates a blank space but no icon.  When I click on the blank space my Wine Configuration gui box appears.  How do I get an icon in the Launcher?

- When I put a windows application cd in my drive, I see it in Launcher, and can open it and see the folders and files.  However, I cannot browse to it from my Wine Configuration "Add Application" window.  Choosing "My Computer" gives C: and Z: drives, no evidence of the cd drive.  How do I find my cd drive to add the application?

- When I right click on one of the above files and folders, and attempt to copy it to a new folder on my desktop, all the copied folders and files are blank, why?

- When I double click on the "setup.exe" in said windows application, it gives me a "blocked: wine start /unix" error message.  How should I install this application?

These are very old Mad Magazine archives requiring Windows 95/98 or windows NT.  

Running 11.10 and wine1.2 1.2.3-0ubuntu1

Thank you

---

### Post by grahammechanical on 2011-12-26
As you have only had two days experience with both Ubuntu and wine you will not mind my sharing with you a little of my longer experience, will you? I hope not.

Wine is not a program that you run/launch in the normal way. We use wine to install the Windows program and then we run the Windows program by clicking on its icon and wine then runs and it also loads the Windows program for us. So, you do not need a wine icon in the Launcher.

If you have installed wine then open the Dash (Ubuntu icon on top left) and in the search panel type wine. Click on the icon Uninstall Wine Software. A dialog box will open. It will be called Add/Remove Programs. You will see a button called Install. Click on it and you will see a Windows type Open dialog. You can use that to browse to the setup.exe or install.exe on the CD drive that might be labelled drive D: or H: or something like that.

Alternatively you can use the Ubuntu File Manager to copy the files off the CD into a folder that you have created. You can browse to that. It will be in the folder called by your user name.

Once the program has been installed through wine it may put an icon on the desktop. It may not. Search for that program in the Dash. An icon will be there. You use that icon to load the windows program and it will load (if all goes well) just like it was loading on Windows. You will not notice wine working.

You can fix the icon to the Launcher or you can drag it from the Dash on to the Launcher and then it will be always available to launch.

I have never being able to use the method that you are trying to install an application through wine. So, I know how frustrating it is.

In the past I used to run from a terminal a utility called winefile. That produced a Windows Explorer type dialog that I used to browse to the CD drive.

I hope that this helps.

Regards.

---

### Post by BC59 on 2011-12-26
> **volare said:**
> After 2 whole days of Ubuntu experience, could be Unity, could be Wine, so my questions:

- When I position the Wine Configuration icon into my launcher, it creates a blank space but no icon.  When I click on the blank space my Wine Configuration gui box appears.  How do I get an icon in the Launcher?

- When I put a windows application cd in my drive, I see it in Launcher, and can open it and see the folders and files.  However, I cannot browse to it from my Wine Configuration "Add Application" window.  Choosing "My Computer" gives C: and Z: drives, no evidence of the cd drive.  How do I find my cd drive to add the application?

- When I right click on one of the above files and folders, and attempt to copy it to a new folder on my desktop, all the copied folders and files are blank, why?

- When I double click on the "setup.exe" in said windows application, it gives me a "blocked: wine start /unix" error message.  How should I install this application?

These are very old Mad Magazine archives requiring Windows 95/98 or windows NT.  

Running 11.10 and wine1.2 1.2.3-0ubuntu1

Thank you

Adding to @grahammechanical post, you could right click on .exe files you like to install and choose "Open with Other Application" -->Wine

---

