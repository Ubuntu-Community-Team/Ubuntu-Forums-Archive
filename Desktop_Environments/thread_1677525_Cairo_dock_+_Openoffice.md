---
title: "Cairo dock + Openoffice"
date: 2011-01-28
forum: Desktop Environments
---

### Post by vacco on 2011-01-28
I have Cairo dock with OpenGL configured to show all open applications in the current desktop. Applications which I have launchers for in my dock are set to minimize to their launcher icon, and most applications do exactly that.

When I use Openoffice applications however, the launcher do nothing more than function as a launcher. When clicked, the document shows up as a seperate running program in the part of the dock used for applications not permanently attached to the dock.


Not the clearest explanation in the world perhaps, but I hope someone is getting something out of it.

---

### Post by Copper Bezel on 2011-01-28
No, I've seen this too, and it's true of any dock - I've seen it with Cairo as well as AWN. There's no way getting around it, though - OpenOffice is a complicated suite of apps that all like to run in their own windows with their own names. Even if you launch Writer by itself instead of starting from Core, the editor itself is still yet another app.

Amusingly, I've even seen, with three documents open, one of the three documents separated from the group of the other two as its own item in the taskbar, all separate from the launcher.

---

### Post by vacco on 2011-02-03
The problem is also present on Spotify running under Wine. This does not appear to be a problem with other applications under Wine (I have tested only the built-in notepad though).

---

### Post by Copper Bezel on 2011-02-03
I figured it out, but there's no solution. I was wrong about multiple apps - the entire suite is running under one process, I think, sort of like Firefox does, but with the added complication of switches and parameters to define the different types of document windows. Run *ooffice* without any parameters, and you get the core launcher screen - unless there's a window of *any* part of the OOo suite, in which case it does nothing at all, because ooffice is already running. To launch straight into a new document in one of the four "applications", you have to run the command with specific parameters, which are set in the default launchers for Cairo-Dock, AWN, and so on. I think that is, itself, the cause of the problem - the command doesn't match the running window.

So here's the "solution" part: if you create a custom launcher with just ooffice as the command, it *will* behave like any other application that didn't know it was OpenOffice. You launch it, it stays where it is, it keeps your custom icon. Great, **except**....

This means that you'd have to launch Core every time, then select Document, Presentation, Calc, or whatever before getting to the document itself. Because "launch new" just submits ooffice again and because the core only runs once, you could also only start a new document by hitting Ctrl+N, and **only within the "app" you're already using** - Calc to Calc, Writer to Writer. In addition, as a minor thing, if you're using AWN and have the Zeitgeist Helper installed, you won't have a recent documents list for OOo.

If you only use Writer or only use Calc, it might be a livable arrangement, but if that's your style, it seems like all the more a terribly inconvenient extra step to select the document type every time. So, yeah, no solution on this one. Accept the ugly extra icon and live with it. = )

Edit: Alternately, if you wanted all four icons out there and just wanted all those launched windows to go *somewhere* on the dock, add the launcher for core, and it will at least corral them. Eh.

---

### Post by moonbeam on 2011-02-05
A couple quick notes.

Separate launcher for various OOo windows _should_ be working if one uses the awn-testing ppa with the caveat that atm you will probably need an english locale.  It appears that it will be necessary to expose some regular expressions for translation to get this working for other locales - messy.

If anyone is wondering why OOo is such a horrible mess for the docks it not so much that it's all running in one process.... we could deal with that if only OO would deign to set the WM_CLASS xprops based upon which office app the window represents, as it is WM_CLASS only identifies the fact that this is a generic open office window.  As it is, the only halfway reliable to distinguish the windows is the title (see comments about localization above).

Edit: It may be working ok in awn with other locales atm... Need to get some testing done on that.

---

### Post by Little Bones on 2011-02-05
If you're not bound to Cairo-dock it works absolutely fine in Docky...

---

### Post by vacco on 2011-02-05
I have tested and can confirm Little Bones' observation. Openoffice is working fine with Docky, but Spotify have the same problem as with Cairo.

Btw: Docky seems nice. Had it only been possible to choose the desired window of a a program running with multiple open windows, and had the active launcher indicator not been as good as invisible, I would have considered replacing Docky with it to save system resources.

---

