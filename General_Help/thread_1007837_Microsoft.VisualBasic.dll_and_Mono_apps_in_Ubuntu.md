---
title: "Microsoft.VisualBasic.dll and Mono apps in Ubuntu"
date: 2008-12-10
forum: General Help
---

### Post by Kimos on 2008-12-10
So, I've got a small windows app that seems to have been written in VB. If I run it with Mono, here's what I get:

```
$ mono dslazy.exe

** (dslazy.exe:25252): WARNING **: The following assembly referenced from /tmp/dslazy.exe could not be loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=1)
     Version:    7.0.5000.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/tmp/dslazy/).


** (dslazy.exe:25252): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=7.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.

...

```

Some googling and searching shows that I don't have the Microsoft.VisualBasic.dll installed and thus don't have the VB7 runtime. I know nothing about .NET or VB or even Mono for that matter. Any idea how I can get this app to run? I come from a Java background so this looks to me like a classpath problem, but that's just a guess.

I've found the dll and tried dropping it into /usr/lib/mono/1.0/ /usr/lib/mono/2.0/ /usr/lib/mono/gac/ but no change...

---

### Post by Fryrocket on 2008-12-10
Try running it in wine up date the .net and see what happens Let me know this has me curious.

---

### Post by Kimos on 2008-12-10
Should have said I tried it in wine first

```
$ wine dslazy.exe 
install the Windows version of Mono to run .NET executables
```

I'm not sure what you mean by "update the .net" though..

---

### Post by directhex on 2008-12-11
> **Kimos said:**
> Some googling and searching shows that I don't have the Microsoft.VisualBasic.dll installed and thus don't have the VB7 runtime. I know nothing about .NET or VB or even Mono for that matter. Any idea how I can get this app to run? I come from a Java background so this looks to me like a classpath problem, but that's just a guess.

It IS a classpath problem.

There are two issues with fixing it

1) Microsoft.VisualBasic.dll is contained in the libmono-microsoft-visualbasic8.0-cil package. This package is only available for Jaunty (though should be easy to backport manually)

2) You want version 7 (.NET 1.0), but there's only version 8 (.NET 2.0) available. This isn't insurmountable - you can instruct Mono to remap an application into 2.0 - whereupon it should use the 2.0 libraries. In this case, use:
mono --runtime=v2.0.50727 program.exe
Once you have libmono-microsoft-visualbasic8.0-cil installed, of course.

> I've found the dll and tried dropping it into /usr/lib/mono/1.0/ /usr/lib/mono/2.0/ /usr/lib/mono/gac/ but no change...

From Windows? That won't work. And don't manually insert files into the GAC - use "gacutil -i" to install them (generally speaking - but don't bother with Windows DLLs)

---

### Post by vaineh on 2008-12-22
i've got a similar issue with a windows app

```
WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies
```

im on ubuntu 7.10 but im just seeing if this app will work at all. ultimately i'd like to get it on debian etch. 

is libmono-microsoft-visualbasic8.0-cil source available anywhere?

---

### Post by vaineh on 2008-12-23
the only way i've got my app running so far is by installing the windows version of mono into wine, and then running the app through mono.. through wine :)

---

### Post by directhex on 2008-12-23
> **vaineh said:**
> i've got a similar issue with a windows app

```
WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies
```

im on ubuntu 7.10 but im just seeing if this app will work at all. ultimately i'd like to get it on debian etch. 

is libmono-microsoft-visualbasic8.0-cil source available anywhere?

[http://packages.ubuntu.com/source/jaunty/mono-basic](http://packages.ubuntu.com/source/jaunty/mono-basic)

---

### Post by ExecutorE on 2009-05-20
When running a mono app, I get this:

```
System.UnauthorizedAccessException: Access to the path "~\EveHQ\Reports" is denied.
  at System.IO.Directory.CreateDirectoriesInternal (System.String path) [0x00000] 
  at System.IO.Directory.CreateDirectory (System.String path) [0x00000] 
  at Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory (System.String directory) [0x00000] 
  at Microsoft.VisualBasic.MyServices.FileSystemProxy.CreateDirectory (System.String directory) [0x00000] 
  at EveHQ.frmSplash.frmSplash_Load (System.Object sender, System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnLoad (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnLoadInternal (System.EventArgs e) [0x00000] 
^C

```

I'm trying to run this under gentoo, but this thread has been helpful. Any suggestions?

Thanks,

EE

---

### Post by directhex on 2009-05-20
> **ExecutorE said:**
> When running a mono app, I get this:

```
System.UnauthorizedAccessException: Access to the path "~\EveHQ\Reports" is denied.
  at System.IO.Directory.CreateDirectoriesInternal (System.String path) [0x00000] 
  at System.IO.Directory.CreateDirectory (System.String path) [0x00000] 
  at Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory (System.String directory) [0x00000] 
  at Microsoft.VisualBasic.MyServices.FileSystemProxy.CreateDirectory (System.String directory) [0x00000] 
  at EveHQ.frmSplash.frmSplash_Load (System.Object sender, System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnLoad (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnLoadInternal (System.EventArgs e) [0x00000] 
^C

```

I'm trying to run this under gentoo, but this thread has been helpful. Any suggestions?

Thanks,

EE

export MONO_IOMAP=all

And contact the app's author to tell them their code is faulty - use System.IO.Path.Combine( "EveHQ", "Reports" ) not "EveHQ\Reports" and so on

---

### Post by ExecutorE on 2009-05-21
was the export command supposed to solve that problem, and allow the code to run? Or does tha app author still need to fix the faulty bits?

Thanks for the help.

EE

---

### Post by directhex on 2009-05-21
> **ExecutorE said:**
> was the export command supposed to solve that problem, and allow the code to run? Or does tha app author still need to fix the faulty bits?

Thanks for the help.

EE

Both. The export is a hack to make Mono ignore some of the most common programming errors (hardcoded backslashes in paths, and case-insensitive paths)

---

