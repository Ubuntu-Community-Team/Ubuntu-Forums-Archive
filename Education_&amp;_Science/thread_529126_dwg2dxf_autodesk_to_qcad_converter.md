---
title: "dwg2dxf autodesk to qcad converter"
date: 2007-08-18
forum: Education &amp; Science
---

### Post by buzzmandt on 2007-08-18
I have several projects that where started and done with autodesk (dwg) and need to open them with qcad whcih wont do dwg as far as i can tell will only do dxf

anyone know where and how I can install the converter and how to use it?

---

### Post by bkortleven on 2007-10-15
Well...
we're currently looking at a similar conversion tool, and found a basic solution, with some minor disappointments...



The packages and stuff used is mainly open-source, except for the OpenDWG packages which are binary, and needed to compile all conversion tools I have found so far.


first of all look at this:
[http://lx-viewer.sourceforge.net/download.php](http://lx-viewer.sourceforge.net/download.php)

This is a 'viewer' program used to open dwg files (they say they support the acad 2.5 to 2000 or even 2002 format)

The 'convertor' part is also downloadable in the same sourceforge project, namely "dwg2dxf".


Now the tricky part:
You need some (ad27 and ad37) binary library files you need to obtain from the OpenDesign/OpenDWG foundation.
The website is here: [http://opendesign.com/](http://opendesign.com/)
You'll need to subscribe to them, and sign some NDA-forms...

I have to warn you: it took us over 2 months to get to the actual downloads...
so be patient... they have a lot on their mind, are very strict in security and availability on their software and libraries...

If you need further assistance or help, let me know...
I'll try to help as much as I can...

Bram
Ampersant bvba
Belgium

---

### Post by manimaul on 2008-03-16
Even better, don't wait, use wine with the windows dwg to dfx converter.

[http://opendesign.com/guestfiles](http://opendesign.com/guestfiles)

Works flawlessly.

Will

---

### Post by kogos on 2009-06-23
since subscription with OpenDWG guyz is not free anymore (as i see on their site), getting EveryDWG free converter is the way to go!!! and it works great!!!

---

### Post by parovelb on 2011-01-25
Hello!
I have installed *Teigha for DWG* through Wine without any issues. However executing the program gives me errors with dependencies. How can I solve the dll problems?
 ```

fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_SpatialIndex_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_SpatialIndex_3.04_8.dll") not found
err:module:import_dll Library TD_SpatialIndex_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library TD_Gi_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_DbRoot_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_DbRoot_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_DbRoot_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_DbRoot_3.04_8.dll") not found
err:module:import_dll Library TD_DbRoot_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TeighaFileConverter.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TeighaFileConverter.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_SpatialIndex_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_SpatialIndex_3.04_8.dll") not found
err:module:import_dll Library TD_SpatialIndex_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library TD_Gi_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_DbRoot_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_DbRoot_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_DbRoot_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_DbRoot_3.04_8.dll") not found
err:module:import_dll Library TD_DbRoot_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Db_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_SpatialIndex_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_SpatialIndex_3.04_8.dll") not found
err:module:import_dll Library TD_SpatialIndex_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Gi_3.04_8.dll") not found
err:module:import_dll Library TD_Gi_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Db_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Db_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Db_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Db_3.04_8.dll") not found
err:module:import_dll Library TD_Db_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TeighaFileConverter.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Root_3.04_8.dll") not found
err:module:import_dll Library TD_Root_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TD_Ge_3.04_8.dll") not found
err:module:import_dll Library TD_Ge_3.04_8.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TeighaFileConverter.exe") not found
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\QtCore4.dll") not found
err:module:import_dll Library QtCore4.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\QtGui4.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\QtGui4.dll") not found
err:module:import_dll Library QtGui4.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TeighaFileConverter.exe") not found
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.4053)
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\QtCore4.dll") not found
err:module:import_dll Library QtCore4.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TeighaFileConverter.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TeighaFileConverter.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programi\\ODA\\TeighaFileConverter_3.4.0\\TeighaFileConverter.exe" failed, status c0000135
```

---

### Post by parovelb on 2011-01-25
I have solved the problem updating *Wine *and using [*winetricks*]("http://wiki.winehq.org/winetricks") to install vcrun2005 package. The conversion works fine ;)

---

### Post by bwakkie on 2012-02-29
From now on you can just install a linux version:

[http://www.opendesign.com/files/guestdownloads/TeighaFileConverter/teighafileconverter_3.5.1_i386.deb](http://www.opendesign.com/files/guestdownloads/TeighaFileConverter/teighafileconverter_3.5.1_i386.deb)

Just tested it and works in Ubuntu 11.10

Start TeighaFileConverter in your terminal.

---

### Post by oldos2er on 2012-02-29
Closed, necromancy.

---

