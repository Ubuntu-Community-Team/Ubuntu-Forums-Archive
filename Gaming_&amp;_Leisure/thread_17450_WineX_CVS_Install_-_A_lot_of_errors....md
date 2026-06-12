---
title: "WineX CVS Install - A lot of errors..."
date: 2005-02-28
forum: Gaming &amp; Leisure
---

### Post by martin.t on 2005-02-28
Hello.
I'm trying to install WineX trough CVS and get these errors..
I would be very happy if someone could help me solve this problem.

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

Compiling ...




--------- Error log - file /root/.WineCVS/sources/cvscedega/ErrorLog : ---------./ppl.l:1368: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1368: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:1370: error: `input_name' undeclared (first use in this function)
./ppl.l:1371: error: `line_number' undeclared (first use in this function)
./ppl.l:1378: error: `pp_macexp' undeclared (first use in this function)
./ppl.l: På toppnivå:
./ppl.l:1386: varning: "macro_add_expansion" deklarerades implicit "extern" och senare "static"
./ppl.l:1276: varning: tidigare deklaration av "macro_add_expansion"
./ppl.l:1386: varning: type mismatch with previous implicit declaration
./ppl.l:1276: varning: previous implicit declaration of `macro_add_expansion'
./ppl.l:1386: varning: "macro_add_expansion" deklarerades tidigare implicit att returnera "int"
./ppl.l: I funktion `macro_add_expansion':
./ppl.l:1387: error: `macexpstackentry_t' undeclared (first use in this function)
./ppl.l:1387: error: `mep' undeclared (first use in this function)
./ppl.l:1396: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1396: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:1398: error: `input_name' undeclared (first use in this function)
./ppl.l:1399: error: `line_number' undeclared (first use in this function)
./ppl.l: På toppnivå:
./ppl.l:1411: varning: "put_buffer" deklarerades implicit "extern" och senare "static"
./ppl.l:1151: varning: tidigare deklaration av "put_buffer"
./ppl.l:1411: varning: type mismatch with previous implicit declaration
./ppl.l:1151: varning: previous implicit declaration of `put_buffer'
./ppl.l:1411: varning: "put_buffer" deklarerades tidigare implicit att returnera "int"
./ppl.l: I funktion `put_buffer':
./ppl.l:1415: error: `pass_data' undeclared (first use in this function)
./ppl.l: I funktion `do_include':
./ppl.l:1439: error: `includelogicentry_t' undeclared (first use in this function)
./ppl.l:1439: error: `iep' undeclared (first use in this function)
./ppl.l:1441: error: `includelogiclist' undeclared (first use in this function)
./ppl.l:1462: varning: implicit declaration of function `open_include'
./ppl.l:1462: varning: tilldelning skapar pekare från heltal utan typkonvertering
./ppl.l:1467: error: `seen_junk' undeclared (first use in this function)
./ppl.l:1468: error: `include_state' undeclared (first use in this function)
./ppl.l:1469: error: `include_ppp' undeclared (first use in this function)
./ppl.l:1470: error: `pass_data' undeclared (first use in this function)
./ppl.l:1473: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1473: error: `DEBUGLEVEL_PPMSG' undeclared (first use in this function)
./ppl.l:1474: error: `input_name' undeclared (first use in this function)
./ppl.l:1474: error: `line_number' undeclared (first use in this function)
./ppl.l:1474: error: `include_ifdepth' undeclared (first use in this function)
./ppl.l: I funktion `push_ignore_state':
./ppl.l:1488: error: `pp_ignore' undeclared (first use in this function)
./ppl.l: På toppnivå:
lex.ppl.c:15101: varning: `yyunput' defined but not used
make[2]: *** [lex.ppl.o] Fel 1
make[2]: Leaving directory `/root/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Fel 2
make[1]: Leaving directory `/root/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Fel 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)
------------------------------------------------------------------------------------------

```

---

### Post by DJ_Max on 2005-02-28
With CVS versions there are no gurantee that they will work. Main reason, because a CVS version you download it just a snapshot of where the developers left off at, and any developer can vouch that they will leave a script in a non-working condition to work on later. So those errors are probably where Transgaming left off at.

Thats it the Cedega CVS is the normal way a CVS acts as.

---

### Post by Snipersnest on 2005-02-28
This is just one more reason to be a TransGaming subscriber and support the Linux game industry!  Once you subscirbe at least you get support and patches/fixes. 

No offence but sounds like your screwed... Go suck it up and subscribe.. lol...Use Point2Play, it makes gaming such more simple!

---

