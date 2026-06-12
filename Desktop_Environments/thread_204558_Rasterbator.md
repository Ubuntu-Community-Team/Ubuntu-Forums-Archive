---
title: "Rasterbator"
date: 2006-06-27
forum: Desktop Environments
---

### Post by andlinux21 on 2006-06-27
I use the program Rasterbator to make wall size posters has anyone used this in linux or know of a program that will take pictures and turn them into huge posters?:confused:

---

### Post by crysys on 2007-01-27
Old thread, I know but I have an answer and a problem.

First off, I found this how-to for compiling Rasterbator on linux using mono:
[http://screamz.madoka.be/wiki/index.php/Rasterbator_with_mono]("http://screamz.madoka.be/wiki/index.php/Rasterbator_with_mono")

But, I'm having difficulty compiling.  I installed all the listed packages in both the 'Install Mono' and 'Get some packages' steps.  The source patched just fine.  When I try to compile with mcs I get:
```
Rasterbator.cs(222,27): error CS0227: Unsafe code requires the `unsafe' command line option to be specified
Compilation failed: 1 error(s), 0 warnings

```

When I toss the '-unsafe' flag in I get:
```
MainForm.cs(35,26): error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
Compilation failed: 1 error(s), 0 warnings

```

:confused:

Kernel 2.6.17-10-generic
Kubuntu Edgy

---

### Post by screamz on 2007-02-11
my bad, forgot to insert the patching of the patch step :D
also the compiling part is not necessary because it s built.

I 've updated the wiki

[http://screamz.madoka.be/Rasterbator.buildfix1.diff](http://screamz.madoka.be/Rasterbator.buildfix1.diff)

here is the right patch

yt

SC

---

### Post by rscarriere on 2007-03-03
I've followed all the instructions but can't seem to get it to run.   Here is the output I get - any thoughts?

$mono ../Rasterbator.exe
Mono System.Windows.Forms Assembly [$auto_build_revision$]
Gtk colorscheme read

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at System.Windows.Forms.MimeIconEngine.GetIconIndexForMimeType (System.String mime_type) [0x00000] 
  at System.Windows.Forms.UnixFileSystem..ctor () [0x00000] 
  at System.Windows.Forms.MWFVFS..ctor () [0x00000] 
  at System.Windows.Forms.FileDialog..ctor () [0x00000] 
  at System.Windows.Forms.OpenFileDialog..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.OpenFileDialog:.ctor ()
  at Rasterbator.MainForm.InitializeComponent () [0x00000] 
  at Rasterbator.MainForm..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) Rasterbator.MainForm:.ctor ()
  at Rasterbator.MainForm.Main (System.String[] args) [0x00000]

---

### Post by mcduck on 2007-03-03
You could just use the original web version ;)

[http://homokaasu.org/rasterbator/wizard.gas?Phase=1]("http://homokaasu.org/rasterbator/wizard.gas?Phase=1")

---

### Post by GavinZac on 2007-09-30
this is the output from my MAKE
```
gavin@gavin-laptop-ubuntu:~/Rasterbator Standalone/source$ make
#mcs -out:../Rasterbator.exe -unsafe -resource:Rasterbator.MainForm.resources -r:System.Windows.Forms -r:System.Drawing -r:../itextsharp.dll *.cs
/bin/sh: mcs: not found
make: *** [all] Error 127
```
I pressed ahead as suggested by the how-to, but got this
```
gavin@gavin-laptop-ubuntu:~/Rasterbator Standalone/source$ mono ../Rasterbator.exe

** (../Rasterbator.exe:11174): WARNING **: The following assembly referenced from /home/gavin/Rasterbator Standalone/Rasterbator.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=0)
     Version:    1.0.5000.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/gavin/Rasterbator Standalone/).


** (../Rasterbator.exe:11174): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
The entry point method could not be loaded
```

---

### Post by couch on 2008-04-24
Try installing mcs.

---

### Post by couch on 2008-04-24
Try installing mcs Gavin.






On my machine(Gutsy): I finally installed all the necessary packages, and I can compile fine.  It runs, however it only displys the logo and a short text intro to the program.  It never displays the menu to actually do anything.

Any suggestions?

---

