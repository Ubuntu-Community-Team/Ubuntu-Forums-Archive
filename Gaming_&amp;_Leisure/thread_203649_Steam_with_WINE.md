---
title: "Steam with WINE"
date: 2006-06-25
forum: Gaming &amp; Leisure
---

### Post by sean_ on 2006-06-25
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:dbghelp:EnumerateLoadedModules If this happens, bump the number in mod


That's what it says when I try to run WINE in the terminal. 
it says that in the terminal, the Error popup box says > steam.exe main exception: win32 structuredexception at 7d3bb127:
              attempt toread from virtual address 0 without appropriate access
              rights.


Please help.

---

### Post by Jasper Houtman on 2006-06-25
Type sudo in front of the command you typed to run the program.
for example: sudo wine filename

---

### Post by sean_ on 2006-06-25
Nope.
> err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
wine: Call from 0x7fc2eb50 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting
Shutting down. . .
30client callback thread error



---

### Post by Jasper Houtman on 2006-06-25
Solution found on WINE homepage:

Installing and Running Steam 3

Option 1: Without Winetools or Internet Explorer

1. Install Wine 0.9.15 (confirmed)

2. Install Mozilla Active X Control from

[http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz)

(The transgaming ActiveX Control is used because it includes one enhanced dll necessary to Steam operation)

a. Untar to any directory
b. In that directory, run #regsvr32 mozctlx.dll

3. Install tahoma.ttf from either a windows installation, or download from the net. Installation will vary with flavor of linux.

4. Install Steam with steaminstall.exe from the Steampowered website. When it asks for your username and password, close the application.

(Alternatively you can right-click the username input box and it will give you keyboard focus. In this case you can skip steps 5-7)

5. Run winecfg as user, select the Graphics tab, then check "Emulate a virtual desktop". Select at least a 1024x768 desktop size and click Apply. Close the app.

6. Start Steam.exe from .wine/drive_c/Program Files/Steam/. After entering your username and password, make SURE that "Remember my username and password" is checked.

You cannot enter your username or password when Wine is not running with an emulated desktop, so it must remember them now, before we switch that setting back.

Click OK, close the HTML window that pops up by clicking the X at the top. The Close button at the bottom does not work. Close the app.

7. Return to winecfg and uncheck "Emulate a virtual desktop". Apply and exit the app.

Your steam install is now complete.

Option 2: Using Winetools (not recommended)

1. Install Wine 0.9.15

2. Install winetools

3. Run winetools, allow it to create a new wine folder, and allow it to install DCOM98 and Internet Explorer. Then select install tested software and then choose steam from the list.

Known Bugs:

-Username and Password dialogs cannot be typed in unless right clicked first.
-Application will always stay on top of other windows.
-Minimizing the Steam window does not work and will lock user input out of X
-Steam window will not appear in Window List in Gnome or KDE.
-Update freezes at 26% (just keep killing and retrying application, also try #wineboot)
-Won\'t start with no error message (completely re-install wine and start from scratch)

Last tested on 6.18.2006. In Wine 0.9.15

	
**Fixing the 26% bug:**
	
Hanging on 26%

Workarounds for 26% hang bug:

Kill all wine processes...

#killall wine
#killall wine-preloader
#killall wineserver

and then make a fake win boot...

#wineboot

---

### Post by sean_ on 2006-06-25
K, I updated it fully, but I don't get step 2:
b. In that directory, run #regsvr32 mozctlx.dll

I did sudo wine Steam.exe and it still gives out the same error I pastein the last post

---

### Post by sean_ on 2006-06-25
Fixed, now I need to know where to put tahoma.tff

---

### Post by Jasper Houtman on 2006-06-25
2. Install Mozilla Active X Control from

[http://downloads.transgaming.com/moz...mozcontrol.tgz]("http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz")

*Download the above file and extract it to your desktop*

Then start up the terminal
type: cd /Desktop/directory (replacing directory with the name of the directory on your desktop).
then type: regsvr32 mozctlx.dll 
or if that gives you errors try: sudo regsvr32 mozctlx.dll

After installing this steam should work.

---

### Post by Jasper Houtman on 2006-06-25
[QUOTE=sean_]Fixed, now I need to know where to put tahoma.tff[/QUOTE]

open up your home directory in the file browser.
press Ctrl+H
now open .wine then drive-c then windows and then fonts
Now copy the file into the fonts directory

---

### Post by cs378 on 2006-07-17
im on the same page. I tried and installed all the steps witht h newest version of wine. ](*,)

---

