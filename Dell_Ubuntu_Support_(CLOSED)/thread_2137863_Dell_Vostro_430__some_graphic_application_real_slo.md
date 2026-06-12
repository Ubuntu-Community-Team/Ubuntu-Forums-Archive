---
title: "Dell Vostro 430 : some graphic application real slow"
date: 2013-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vincentberenz on 2013-04-22
Hi,

I just installed 12.04LTS, 32bits on a dell vostro 430 (corei7 cpu).
Things are running fine, except that some graphical application are surprisingly slow.

The two examples:
- I have a c++ program using open dynamics engine and drawstuff (which uses opengl). It runs 10x slower than on my acer aspire S7 (windows8).
- Plotting on GNU octave is surprisingly slow. Plotting a scatter plot of only 200 points takes several seconds. 

Note:
- After installing ubuntu I agreed to the proposal of using nvidia drivers. The recommended one (version current) is in use.
- When running sysinfo, selecting the nvidia tab, I have errors appearing on my console:

```
System.IO.DirectoryNotFoundException: Could not find a part of the path "/proc/driver/nvidia/cards/0".
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] in <filename unknown>:0 
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.IO.File.OpenRead (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.StreamReader..ctor (System.String path, System.Text.Encoding encoding, Boolean detectEncodingFromByteOrderMarks, Int32 bufferSize) [0x00000] in <filename unknown>:0 
  at System.IO.StreamReader..ctor (System.String path) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader:.ctor (string)
  at System.IO.File.OpenText (System.String path) [0x00000] in <filename unknown>:0 
  at Sysinfo.NvidiaInfo.MainInfo () [0x00000] in <filename unknown>:0 
System.ComponentModel.Win32Exception: ApplicationName='nvidia-settings', CommandLine='-q VideoRam', CurrentDirectory=''
  at System.Diagnostics.Process.Start_noshell (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] in <filename unknown>:0 
  at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] in <filename unknown>:0 
  at System.Diagnostics.Process.Start () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Diagnostics.Process:Start ()
  at Sysinfo.NvidiaInfo.AditionaInfo () [0x00000] in <filename unknown>:0 

```

- if I run glxgears, I do have gears running nicely in a window

When looking for the issue, I noticed that the 64bits version of ubuntu was recommanded for vostro 430 ([http://www.ubuntu.com/certification/hardware/201004-5591/](http://www.ubuntu.com/certification/hardware/201004-5591/)).
Could this be the source of my problem ? (I run the 32bits version).
If not, anybody could point me to the right direction ?

many thx

---

### Post by mikewhatever on 2013-04-24
While a 64bit version may run heavy loads substancially faster, don't expect miracles. OpenGL implementation is generally slower on Linux when compared to Windows. Also, do you have both Intel and Nvidia GPUs, aka Nvidia Optimus?

---

