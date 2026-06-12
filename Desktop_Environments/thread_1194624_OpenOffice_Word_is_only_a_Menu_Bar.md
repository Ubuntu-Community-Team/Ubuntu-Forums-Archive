---
title: "OpenOffice Word is only a Menu Bar?"
date: 2009-06-22
forum: Desktop Environments
---

### Post by sandman3838 on 2009-06-22
Hello

I was adding a Icon to Cardio-Dock and I must have put in the wrong command line.

Now no matter where I open “Open Office Word” all I get is what looks like the top of the menu bar.

** Just take a look at the screen shot.

I can’t Force Quit the thing.
I can’t right click with the mouse and close it.
I can’t even move the thing.
If I reboot it comes back.

However if I “Reload Window Manager” it will go away until I try to open Word again?

I have removed WORD through “Add Remove Programs” and installed it again.  But I still have this issue.

Oh, none of the other Open Office programs are experiencing any issues.
Suggestions?

---

### Post by sandman3838 on 2009-06-23
Ok

This is getting really strange?

I have in order:

- Removed OpenOffice
- Deleted the remaining Openoffice folders in /home/username/.openoffice.org/3/user
- Dumped Trash
- Rebooted
- Re-installed OpenOffice
- Started OpenOffice Presentation & Spreadsheet without a hitch.
- However, every time I start the "Word Processor" I get just the same non-functioning bar that I have placed in the screen shot.

Note - If I go to /usr/share/applications and start OpenOffice Word Processor from there it opens up just great!

A setting on my side has gone haywire?  There has to be a reset switch somewhere?

Anyone?

---

### Post by sandman3838 on 2009-06-23
Does anyone have any ideas on how to reset OpenOffice Word?

There has to be a way to rest totally remove open office and reinstall it?

Perhaps there is some left over Cache or Backup someplace that needs to be removed?

---

### Post by sandman3838 on 2009-06-23
Got it!

I just started from the beginning and went into "Startup Applications" and unchecked anything that was unnecessary.

Then I started switching them back on one at a time.
After switching each one on I would open OO_Word.

Some where along the way it must have re-set?

It's working.  :P

---

