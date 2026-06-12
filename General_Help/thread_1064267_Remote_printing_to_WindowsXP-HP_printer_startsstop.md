---
title: "Remote printing to WindowsXP-HP printer starts/stops but no output"
date: 2009-02-08
forum: General Help
---

### Post by newbjeff on 2009-02-08
I am trying to print from Ubuntu 8.04 to a HP 4215xi on a WindowsXP machine.  Printing works from Windows but sending a job from Ubuntu only results in the printer starting as though it was going to load paper and then shutting down with an error.  The print job is then hung in the queue.  Prior to disk drive failure on the Windows machine, printing worked from Ubuntu, but I had a hard time finding the answer to this problem the last time and am having no luck finding it now.  As I recall, I had to edit something on the Windows machine, and the instructions were for a different HP printer, but those instructions solved the problem.  Can anyone refer me to this information again?

---

### Post by newbjeff on 2009-02-19
Here's a link to a posting that solved the problem for me (my printer is different, so modify for yours accordingly) [http://ssdirect.com/index.php?option=com_content&task=view&id=33&Itemid=1](http://ssdirect.com/index.php?option=com_content&task=view&id=33&Itemid=1), but I'm going to restate part of that post here in case that link disappears.

To begin with, an easy way to get rid of print jobs hung in the WindowsXP print queue is to make a batch file in Notepad that contains the following:

net stop spooler

del %systemroot%\system32\spool\printers\*.shd

del %systemroot%\system32\spool\printers\*.spl

net start spooler

and save that to the root of C: as DeletePrintJobs.cmd - Make a desktop shortcut to that file and you can doubleclick the shortcut to clear the print queue.  Thanks Microsoft - I used that plenty until I found the above post which is restated in part below:

"The problem seems to be caused by the way the HP driver monitors the printer port. An additional complication can be the fact that Macromedia Shockwave associates "spl"-files as shockwave player files. This I found out step by step when trying to find a more effective way to regain control of the printer under Windows and with the help of the article on [http://citrixfaq.msterminalservices.org/faqs2.cfm?id=74&category=2%2C3&sortby=date](http://citrixfaq.msterminalservices.org/faqs2.cfm?id=74&category=2%2C3&sortby=date)

Attention:

    * - you must have local administrator rights on the PC to perform the changes
    * - better back up your Windows system before proceeding
    * Step 1: deleting the stuck print job under Windows:
    * - the spooler service must be stopped first: Start - Control Panel - Administrative Tools - Services - Print Spooler -"Stop"
    * - leave the window open, it will be needed later
    * - navigate to systemfolder (eg C:\WINDOWS) \system32\spool\PRINTERS
    * -- two files will be shown there: xxxx.shd and xxxx.spl
    * -- see if the spl file is described as "Shockwave Splash file": if yes, the registry key must be removed, see Step 2
    * -- delete the two files, close the window
    * Step 2: this step is only required if the spl-file is set to open with Shockwave (see above)
    * - run regedit and navigate to "HK classes root - .spl"
    * - highlight this folder and delete it
    * STEP 3:
    * - if it's not already open run regedit now:
    * - navigate to: "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\hp psc 1300 series"
    * -- Note: the number in "Version-" may be different on your system!
    * - right click the key and select "Export" to back it up to a location of your choice
    * - look for the "Monitor"-key on the right hand side, double-click it, note down the value (most likely "hpzsnt10") and delete it
    * - double-click the "Dependent Files"-key and delete the line that reads "hpzsnt10.dll"
    * - exit the registry editor
    * - in Windows Explorer navigate to the equivalenty of "C:\WINDOWS\system32\spool\drivers\w32x86\hppsc_1300_series7216" and rename "hpzsnt10.dll" to "hpzsnt10.dl~"
    * - do the same for "C:\WINDOWS\system32\spool\drivers\w32x86\3"
    * - start the spooler service again

The printer now should react promptly to jobs sent from Linux."

---

