---
title: "Ubuntu 8.10 + EVE Online"
date: 2009-02-04
forum: General Help
---

### Post by calvert, phil on 2009-02-04
I installed the Linux versoin of EVE Online and it installed alright. But I ran it and it doesn't work... Heres what I got out of the terminal.

phil@phil-desktop:~$ eve
Single-user install...
This is the update checker... 
Running /home/phil/.cedega/.updater/cedega_updater.py
/home/phil/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Running... /home/phil/.cedega/.ui/runGUI
/home/phil/.cedega/.ui/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
phil@phil-desktop:~$ Could not load graphics driver 'x11drv'
Could not load graphics driver 'x11drv'
wine: Unhandled exception, starting debugger...
Could not load graphics driver 'x11drv'

---

### Post by amgnix on 2009-02-15
Hi,

Getting the same error. Did you find a solution.

Thanks
A

---

### Post by NSAJEFF on 2009-02-15
> **amgnix said:**
> Hi,

Getting the same error. Did you find a solution.

Thanks
A

Which version are you running? According to this: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9022](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9022)

the install should go off without a problem but nothing else works..

---

### Post by amgnix on 2009-02-15
Hi,

Found a post on the eve forums saying the the video hardware has to be nVidia. I'm running a thinkpad t60 with an ATI. Guess its back to work!!

A

---

### Post by Selcal on 2009-02-15
> **calvert, phil said:**
> I installed the Linux versoin of EVE Online and it installed alright. But I ran it and it doesn't work... Heres what I got out of the terminal.

phil@phil-desktop:~$ eve
Single-user install...
This is the update checker... 
Running /home/phil/.cedega/.updater/cedega_updater.py
/home/phil/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Running... /home/phil/.cedega/.ui/runGUI
/home/phil/.cedega/.ui/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
phil@phil-desktop:~$ Could not load graphics driver 'x11drv'
Could not load graphics driver 'x11drv'
wine: Unhandled exception, starting debugger...
Could not load graphics driver 'x11drv'

I found a solution, I posted it in a thread but i can tell you here as well.

If you have an ATI graphics card you need to use wine there really isn't another way to do it.

Install WINE then the windows version of the game into WINE

then
grab windows fonts because it won't even allow you to Read and accept the EULA unless you do
> sudo apt-get install msttcorefonts

then copy the fonts to the right location
> sudo cp /usr/share/fonts/truetype/msttcorefonts/* ~/.wine/drive_c/windows/Fonts

then it worked fine for me but i have to use wine if i want to play the game.  talk to me ingame if you want 'Facetiousproxy'

---

### Post by amgnix on 2009-02-15
thanks i will give this a go.

A

---

