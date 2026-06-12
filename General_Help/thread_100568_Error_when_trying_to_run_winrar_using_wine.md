---
title: "Error when trying to run winrar using wine"
date: 2005-12-07
forum: General Help
---

### Post by Kelpie on 2005-12-07
i recently just installed wine and installed winrar aswell but when i clicked winrar.exe it did nothing, so i try to run it from the terminal and got this:
```
amber@Dementia:~$ wine "C:\program files\winrar\winrar.exe"
fixme:shell:SHAutoComplete SHAutoComplete stub
err:rebar:REBAR_AdjustBands Phase 1 failed, x=692, maxx=-4, start=0, end=0
err:rebar:REBAR_AdjustBands Phase 1 failed, x=692, maxx=-4, start=0, end=0
err:rebar:REBAR_AdjustBands Phase 1 failed, x=40, maxx=-4, start=1, end=1
err:rebar:REBAR_AdjustBands Phase 1 failed, x=692, maxx=-4, start=0, end=0
err:rebar:REBAR_AdjustBands Phase 1 failed, x=40, maxx=-4, start=1, end=1
err:rebar:REBAR_AdjustBands Phase 1 failed, x=100, maxx=-4, start=2, end=2
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  3178
  Current serial number in output stream:  3180
```
but when i try unrar.exe it gives me this:
```
amber@Dementia:~$ wine "C:\program files\winrar\unrar.exe"

UNRAR 3.51 freeware      Copyright (c) 1993-2005 Alexander Roshal

Usage:     unrar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  e             Extract files to current directory
  l[t,b]        List archive [technical, bare]
  p             Print file to stdout
  t             Test archive files
  v[t,b]        Verbosely list archive [technical,bare]
  x             Extract files with full path

<Switches>
  -             Stop switches scanning
  ac            Clear Archive attribute after compression or extraction
  ad            Append archive name to destination path
  ap<path>      Set path inside archive
  av-           Disable authenticity verification check
  c-            Disable comments show
  cfg-          Disable read configuration
  cl            Convert names to lower case
  cu            Convert names to upper case
  dh            Open shared files
  ep            Exclude paths from names
  ep3           Expand paths to full including the drive letter
  f             Freshen files
  id[c,d,p,q]   Disable messages
  ierr          Send all messages to stderr
  inul          Disable all messages
  ioff          Turn PC off after completing an operation
  kb            Keep broken extracted files
  n<file>       Include only specified file
  n@            Read file names to include from stdin
  n@<list>      Include files in specified list file
  o+            Overwrite existing files
  o-            Do not overwrite existing files
  oc            Set NTFS Compressed attribute
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
  ri<P>[:<S>]   Set priority (0-default,1-min..15-max) and sleep time in ms
  ta<date>      Process files modified after <date> in YYYYMMDDHHMMSS format
  tb<date>      Process files modified before <date> in YYYYMMDDHHMMSS format
  tn<time>      Process files newer than <time>
  to<time>      Process files older than <time>
  ts<m,c,a>[N]  Save or restore file time (modification, creation, access)
  u             Update files
  v             List all volumes
  ver[n]        File version control
  vp            Pause before each volume
  x<file>       Exclude specified file
  x@            Read file names to exclude from stdin
  x@<list>      Exclude files in specified list file
  y             Assume Yes on all queries
```

i want to unrar "C:\Downloads\conquer2.0.rar"
i would be greatful for your help, thanks!

---

### Post by aysiu on 2005-12-07
Probably not the solution you're looking for, but you could always use the native *rar* programs...

---

### Post by Kelpie on 2005-12-07
[QUOTE=aysiu]Probably not the solution you're looking for, but you could always use the native *rar* programs...[/QUOTE]
actually id prefer that, trial programs get pretty annoying afterawhile, they allow you to use it but the annoying popups, the long waiting till you can use it, very icky, thanks much!

Edit: is there one thats free? thatd be great ^^

---

### Post by giloth on 2005-12-07
Doesn't most linux distros come with a built in programs for this? Maybe most don't support RAR formats yet, I dunno.

---

### Post by Kelpie on 2005-12-07
[QUOTE=giloth]Doesn't most linux distros come with a built in programs for this? Maybe most don't support RAR formats yet, I dunno.[/QUOTE]

the archiver that came with Ubuntu doesnt recognize it as a supported file format :/

---

### Post by aysiu on 2005-12-07
[QUOTE=Kelpie]
Edit: is there one thats free? thatd be great ^^[/QUOTE] Free as in cost-free (no money to pay)? They're all free in that way. Just make sure you enable extra repositories (see the first link in my sig).

---

### Post by Kelpie on 2005-12-07
thanks alot!

---

