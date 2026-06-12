---
title: "CVSWineX help wanted."
date: 2005-01-18
forum: Gaming &amp; Leisure
---

### Post by node on 2005-01-18
trying to get it running

```
node@starscream:~/winex $ sudo ./tools/winecheck
This script verifies the configuration of the whole Wine environment.
Note that this is an ALPHA version, and thus it doesn't catch all problems !
The results of the checks are printed on the right side:
OK         - test passed without problems.
SUSPICIOUS - potentially problematic. You might want to look into that.
BAD        - This is a problem, and it leads to configuration score penalty.
CRITICAL   - A critical problem which can easily lead to malfunction.
FAILED     - This problem leads to Wine failure almost certainly.

The result will be printed as a percentage score indicating config completeness.


--------------------------- checking Wine base files ---------------------------
001. Checking for file "wine"...                            OK.
002. Checking for correct .so lib config (please wait)...   OK.

----------------------------- checking config file -----------------------------
003. Checking config file access...                         OK.

>>> Checking drive C settings:
004.  Checking Path option...                               FAILED (${HOME}/.wine/c_drive does not exist !).
- ADVICE: create this directory or point Path to a real directory.
005.  Checking Type option...                               OK.
006.  Checking Filesystem option...                         OK.
--> PROBLEM.

>>> Checking drive D settings:
007.  Checking Path option...                               OK.
008.  Checking Type option...                               OK.
009.  Checking Filesystem option...                         OK.
--> OK.

>>> Checking drive E settings:
010.  Checking Path option...                               OK.
011.  Checking Type option...                               OK.
012.  Checking Filesystem option...                         OK.
--> OK.

>>> Checking drive G settings:
013.  Checking Path option...                               OK.
014.  Checking Type option...                               OK.
015.  Checking Filesystem option...                         OK.
--> OK.

--------------------- checking system devices used by Wine ---------------------
016. Checking sound device /dev/dsp...                      OK.
017. Checking audio mixer device /dev/mixer...              OK.
018. Checking MIDI sequencer device /dev/sequencer...       BAD (/dev/sequencer does not exist).
- ADVICE: use MAKEDEV script to create it.

----------------------- checking registry configuration ------------------------
019. Checking availability of winedefault.reg entries...    OK.
020. Checking availability of windows registry entries...   CRITICAL (entry "Default Taskbar" not found).
- ADVICE: Windows registry does not seem to be added to Wine, as this typical Windows registry entry does not exist in Wine's registry. This can affect many newer programs. A complete original Windows registry entry set will *not* be available with a no-windows install, of course, so you'll have to live with that..

20 tests. 0 suspicious, 1 bad, 1 critical, 1 failed.
Wine configuration correctness score: 12.11%

```
Although it says "004.  Checking Path option...                               FAILED (${HOME}/.wine/c_drive does not exist !)." this does exist.
And with MAKEDEV I get "node@starscream:~/winex $ sudo MAKEDEV /dev/sequencer
/sbin/MAKEDEV: don't know how to make device "/dev/sequencer"
"
Is there anyone that actually got it working ?

---

### Post by node on 2005-01-19
there is more here " [http://www.bobjonesonline.com/tmp/Errorlog.txt](http://www.bobjonesonline.com/tmp/Errorlog.txt) "  :-|

---

