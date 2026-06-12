---
title: "Autosketch in Wine"
date: 2005-11-18
forum: Desktop Environments
---

### Post by Irony on 2005-11-18
I installed Autosketch in wine yesterday. At the end of the install it asked if I wanted to run AutoSketch so I okayed it and it opened and I could view my Autosketch files - so I know Autosketch works and will open in linux in wine.

However on closing the Autosketch program I find that I cannot not start it. As there is no shortcut to it I type in terminal;

[PHP]irony@ubuntu:~$ wine "c:\program files\AutoSketch\Sketch.exe"
err:module:import_dll Library acge15.dll (which is needed by L"C:\\program files\\AutoSketch\\sxMath2.dll") not found
err:module:import_dll Library sxMath2.dll (which is needed by L"C:\\program files\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACDB15.dll (which is needed by L"C:\\program files\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library acge15.dll (which is needed by L"C:\\program files\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACRX15.dll (which is needed by L"C:\\program files\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACUTIL15.dll (which is needed by L"C:\\program files\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACDBXREF.dll (which is needed by L"C:\\program files\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library fct42.dll (which is needed by L"C:\\program files\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library kern42.dll (which is needed by L"C:\\program files\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library Sx2.dll (which is needed by L"C:\\program files\\AutoSketch\\Sketch.exe") not found
err:module:import_dll Library acge15.dll (which is needed by L"C:\\program files\\AutoSketch\\sxMath2.dll") not found
err:module:import_dll Library sxMath2.dll (which is needed by L"C:\\program files\\AutoSketch\\Sketch.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program files\\AutoSketch\\Sketch.exe" failed, status c0000135[/PHP]

It seems that wine cannot find the .dll files. They are however there and in the correct place, I know this because I can compare them to what I have in the actual Windows install.

This is the first time I've tried wine so it maybe that I missed some obvious configurations.

---

