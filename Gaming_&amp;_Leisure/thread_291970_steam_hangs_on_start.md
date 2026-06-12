---
title: "steam hangs on start"
date: 2006-11-03
forum: Gaming &amp; Leisure
---

### Post by el_ricardo on 2006-11-03
hello, been trying to get steam working in ubuntu with wine for about the millionth time (i want to get rid of my dependency on windows for gaming!) i thought i'd finally got it set up right, but now when i try to load steam, i get the updating window, fir about a second, then it vanishes, my cpu goes up 2 100%, and nothing happens. I've had it hanging on 27%, i got round that, and i've had the mozilla active-x problem, and i fixed that, though it only just started doing this after i installed the mozilla active-x control, plz help! the only output i get is this:

```

ricardo@ricardo-desktop:~/.wine/drive_c/Programme/Valve$ WINEDEBUG="fixme-all" wine Steam
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file ole32.dbg ("")
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file oleaut32.dbg ("")
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file rpcrt4.dbg ("")
wine: Call from 0x7fc2e770 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting
Shutting down. . .
300client callback thread error


```

and an error message in wine: ERROR: Steam.exe (main exception):win32 StructuredException at 7CFDB127: Attempt to read from virtual adress 0 without appropriate access rights

please help, i'm getting seriously fed up!

---

### Post by dbd on 2006-11-03
There seems to be info on similar problems in the troubleshooting section of this howto:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

---

### Post by KuriKai on 2006-11-04
What version of wine do you have?

---

### Post by haxer on 2006-11-04
try steam4linux :D

---

