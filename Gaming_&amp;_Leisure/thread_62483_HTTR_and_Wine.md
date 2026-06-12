---
title: "HTTR and Wine ???"
date: 2005-09-04
forum: Gaming &amp; Leisure
---

### Post by grofaz on 2005-09-04
Hi,

I'm getting the following when I try to run Highway to the Reich with Wine:

kudu@ubuntu:~$ wine "C:\Matrix Games\Highway to the Reich\HTTR.exe"
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Matrix Games\\Highway to the Reich\\PGUI.dll") not found
err:module:import_dll Library PGUI.dll (which is needed by L"C:\\Matrix Games\\Highway to the Reich\\HTTR.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Matrix Games\\Highway to the Reich\\HTTR.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Matrix Games\\Highway to the Reich\\HTTR.exe" failed, status c0000135

Is there any way to correct the lack of these dll's ??

Regards,
grofaz

---

### Post by evilghost on 2005-09-04
Google for them and put them in the same directory as HTTR.exe

MFC42.dll is pretty common, not sure about PGUI.dll, but it may be installed in the "Common Files" which you copy into the same dir as HTTR.exe

---

### Post by grofaz on 2005-09-05
OK...done did. Now I'm getting this:

kudu@ubuntu:~$ wine "C:\Matrix Games\Highway to the Reich\HTTR.exe"
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Value in failed request:  0x0
  Serial number of failed request:  4542
  Current serial number in output stream:  4606

Now how do I jump this particular hurddle ?? The Scenario Maker runs nicely though.

Regards,
grofaz

---

### Post by evilghost on 2005-09-05
If this game uses DirectX and/or requires DirectX you will not be able to play/use it using WINE, due to the lack of DirectX.  Instead, you will have to use the free solution WineX, or, the subscription based service called Cedega.  WineX lacks support for copy-protection schemes such as SafeDisc, SafeDisc2, SecurROM, etc.

---

### Post by grofaz on 2005-09-05
I haven't had any luck with P2P/Cedega. Maybe I'll try cedega cvs. Actually have come closest using wine. Go figure. Is wineX different from cedega cvs ??

Regards

---

