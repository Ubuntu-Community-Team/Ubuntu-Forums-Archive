---
title: "WineCVS.sh error in CVS Checkout"
date: 2006-09-20
forum: Gaming &amp; Leisure
---

### Post by odweaver on 2006-09-20
I'm trying to setup cedega from wine.sh, this is the error I get:
```
WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Checking out CVS ... May take a while




--------- Error log - file /home/odweaver/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/odweaver/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

```

---

### Post by RoyArne on 2006-09-20
You need to install cvs:
```
sudo aptitude install cvs
```

---

### Post by odweaver on 2006-09-20
That worked, thank you for telling me how to fix my problem.

---

