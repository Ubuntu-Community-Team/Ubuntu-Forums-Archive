---
title: "GNUstep apps are broken"
date: 2010-10-18
forum: Desktop Environments
---

### Post by topopardo on 2010-10-18
Hi,

I find this extremely strange because it would mean there's a bug in a library but for some reason it's happening and I can't seem to fix it.

All software which uses the GNUstep libraries is broken in 10.10 and 10.04, it segfaults upon launch.

For example:

```
$ Terminal 
2010-10-18 15:41:15.869 Terminal[6690] Problem posting notification: <NSException: 0xc2ba60> NAME:NSRangeException REASON:index is out of range in function _attributesAtIndexEffectiveRange() INFO:(nil)
Segmentation fault
```

Going a bit further reveals more about the issue, it seems to be a problem in a library

```
$ gdb /usr/bin/Terminal 
GNU gdb (GDB) 7.2-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/Terminal...(no debugging symbols found)...done.
(gdb) r
Starting program: /usr/bin/Terminal 
[Thread debugging using libthread_db enabled]
2010-10-18 15:59:14.316 Terminal[6825] Problem posting notification: <NSException: 0x971c50> NAME:NSRangeException REASON:index is out of range in function _attributesAtIndexEffectiveRange() INFO:(nil)

Program received signal SIGSEGV, Segmentation fault.
-[GSMutableString replaceCharactersInRange:withString:] (self=0x96db60, _cmd=0x7ffff7b92380, aRange=<value optimized out>, 
    aString=0x8) at GSString.m:4297
4297	GSString.m: No such file or directory.
	in GSString.m
(gdb) bt
#0  -[GSMutableString replaceCharactersInRange:withString:] (self=0x96db60, _cmd=0x7ffff7b92380, 
    aRange=<value optimized out>, aString=0x8) at GSString.m:4297
#1  0x00007ffff779fb49 in -[GSTextStorage replaceCharactersInRange:withString:] (self=0x96da00, _cmd=0x7ffff7b52f80, 
    range=..., aString=0x7ffff7b52600) at GSTextStorage.m:719
#2  0x00007ffff772721e in cache_lookup_string (string=0x9545f0, attributes=0x91f030, hasSize=0, size=..., useScreenFonts=1)
    at NSStringDrawing.m:281
#3  0x00007ffff77288aa in -[NSString(NSStringDrawing) sizeWithAttributes:] (self=0x9545f0, _cmd=0x7ffff7bc2ca0, 
    attrs=0x91f030) at NSStringDrawing.m:651
#4  0x00007ffff77f839e in -[GSTitleView titleSize] (self=0x91ed60, _cmd=0x7ffff7b0ffd0) at GSTitleView.m:195
#5  0x00007ffff76bb006 in -[NSMenuView sizeToFit] (self=0x91ea20, _cmd=0x7ffff7b10050) at NSMenuView.m:692
#6  0x00007ffff76bbbf9 in -[NSMenuView rectOfItemAtIndex:] (self=0x91ea20, _cmd=0x7ffff7b10060, index=2) at NSMenuView.m:913
#7  0x00007ffff76bbea1 in -[NSMenuView setNeedsDisplayForItemAtIndex:] (self=0x91ea20, _cmd=0x7ffff7b0fd10, index=2)
    at NSMenuView.m:963
#8  0x00007ffff76ba0da in -[NSMenuView itemChanged:] (self=0x91ea20, _cmd=0x7ffff7b0fc10, notification=0x83c920)
    at NSMenuView.m:448
#9  0x00007ffff6fe7fc3 in -[NSNotificationCenter _postAndRelease:] (self=0x6ae750, _cmd=<value optimized out>, 
    notification=0x83c920) at NSNotificationCenter.m:1161
#10 0x00007ffff76b5306 in -[NSMenu setMenuChangedMessagesEnabled:] (self=0x9121a0, _cmd=0x7ffff7b0c100, flag=1 '\001')
    at NSMenu.m:1269
#11 0x00007ffff76b4735 in -[NSMenu update] (self=0x9121a0, _cmd=0x7ffff7b0bf90) at NSMenu.m:1057
#12 0x00007ffff76b44e3 in -[NSMenu update] (self=0x9007c0, _cmd=0x7ffff7b0bf90) at NSMenu.m:1010
#13 0x00007ffff76b379c in -[NSMenu itemChanged:] (self=0x9007c0, _cmd=0x7ffff7b12380, anObject=0x954550) at NSMenu.m:718
#14 0x00007ffff76c0382 in -[NSMenuItem setTarget:] (self=0x954550, _cmd=0x7ffff7b12300, anObject=0x9007c0)
    at NSMenuItem.m:386
#15 0x00007ffff76bf442 in -[NSMenuItem setSubmenu:] (self=0x954550, _cmd=0x7ffff7b0c050, submenu=0x9121a0)
    at NSMenuItem.m:183
#16 0x00007ffff76b3f5e in -[NSMenu setSubmenu:forItem:] (self=0x9007c0, _cmd=0x627560, aMenu=0x9121a0, anItem=0x954550)
    at NSMenu.m:871
#17 0x0000000000404687 in _start ()
(gdb) 

```


Is anybody else experiencing this? It doesn't happen in Debian but I've encountered it on both 10.04 and 10.10

Thanks

---

### Post by Jeremy23 on 2010-10-30
It's not just you. I'm having the exact same issue (found your post by Googling for that error message).

I have [reported the bug on Launchpad]("https://launchpad.net/bugs/668731").

---

### Post by GermanGT on 2010-11-08
Is better if you try GNUstep from source. In this way all work fine.

---

