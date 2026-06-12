---
title: "Utility to see ink level for HP printers"
date: 2005-12-26
forum: General Help
---

### Post by Sef on 2005-12-26
Is there a utility to see the ink level for HP printers?  (an HP equivalent to Epson's mtink.)

---

### Post by blair on 2005-12-26
There is a package called hplip. Go into Synaptic and read the description for the package. You will see the following pertinent statement: “…This package contains the GUI components of the HPLIP system including the hp-toolbox". 

Install hplip from Synaptic. Once the hplip package is installed, open a terminal as root and enter hp-toolbox.  This will cause the HP Device Manager application to launch. If you want to find the path so you can create a shortcut on your desktop, open a shell and enter "whereis hp-toolbox" at a prompt. 

Launching the HP Device Manager before installing any printers generates the following message: “No installed HP devices found. To install a device, use the CUPS interface ([http://localhost:631](http://localhost:631)) or the printer installation wizard that comes with your OS. After setting up the printer, select Device/Refresh All for the printer to appear in the HP Device Manager UI.    

Note: Only devices installed with the hp: CUPS backend will appear in the HP Device Manager. 

You can search HP's web site or sourceforge.net for more info on hp-toolbox. I was never able to actually get it working w/ my HP printer, and I don't know all its feature sets, however this is the tool you are looking for.

---

### Post by steve.horsley on 2005-12-26
Interesting. I hadn't heard of that one - I'll give it a try. The one I use is a package called mtink, which is also in the Synaptic Universe repository.

---

### Post by steve.horsley on 2005-12-26
I'm not impressed with hp-toolbox. It says no HP devices are installed. This is despite the fact that my HP printer works perfectly with all other applications, and is there in System->Administration->Printing.

BTW, mtink needs to run under sudo, and finds my printer on /dev/usb/lp0

---

### Post by Perfect Storm on 2005-12-26
Perhaps try GMSO [http://www.gnomefiles.org/app.php?soft_id=292](http://www.gnomefiles.org/app.php?soft_id=292)

---

### Post by blair on 2005-12-26
As I said, I never was able to get it to work either. It never found my printer either. However it is developed by HP and it is described by them as being a complete GUI-based tool for managing HP printers and seeing printer status. Sorry I can't be of more help.

---

### Post by Sef on 2005-12-26
Steve: mtink is made for Epson printers, do you have an HP printer and it works with it?

---

### Post by tokenwizard on 2008-03-28
I know this is a really old thread, but I came across it trying to find an answer to this same question for Hard Heron Beta. 

The HPLIP was installed by default, but the correct version of python-qt was not, so it would not run hp-toolbox. To resolve, I ran 

**sudo apt-get remove hplip**

then in Synaptic search for** hplip** and install it as well as** hplip-gui**. It will tell you that **python-qt3** must also be installed. 

Once you have those items installed, you *cannot* just simply run HPLIP Toolbox from the System->Preferences menu.  **It MUST be run as sudo** or the toolbox will not see your printer.

So, from a terminal, run **sudo hp-toolbox** and viola!

Of course, knowing this, you can edit your Menu to place gksudo in the Launcher for the HPLIP Toolbox so you can then use your Menus to launch it in the future.

---

